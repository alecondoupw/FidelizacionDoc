---
title: "Plan de pruebas e indicadores"
tags: [zontes, testing]
status: planificado
updated: 2026-10-03
---

# Plan de pruebas e indicadores

**Estado: 0 pruebas de producto ejecutadas; pruebas técnicas de F0 ejecutadas y pasadas (ver «Corridas F0»).** Los IDs son escenarios de aceptación derivados de SRC-01/02/03 y organizados para implementación; no son resultados. La trazabilidad por página está en [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] y los flujos en [[02-Arquitectura/Contratos de integracion por flujo]]. Registrar para cada corrida: fecha, FE/BE revisión, entorno, datos sintéticos, esperado, observado, evidencia, defectos y responsable. Evitar datos personales reales en capturas.

| ID | Escenario mínimo | Fase |
| --- | --- | --- |
| T-ROLE | Cliente no entra a admin; sólo admin crea admin; no se elimina/desactiva último admin activo | F1/F4 |
| T-LINK | Correo normalizado enlaza exactamente al legacy; no coincide → sin vínculo; duplicado/cambio de correo se maneja según DEC-04 | F1/F4 |
| T-AUTHZ | Token ausente, vencido, revocado o rol insuficiente: backend rechaza aunque se manipule frontend | F1–F7 |
| T-RULE | Marca+evento único, puntos no negativos; editar regla afecta sólo grants futuros | F2 |
| T-HISTORY | Cada grant/canje/caducidad/corrección conserva historial y actor/origen | F2/F3 |
| T-POINTS | Reintento del mismo evento no duplica puntos; concurrencia preserva saldo no negativo y aislamiento por marca | F2 |
| T-EXP | Periodo por marca y fecha inicial de grant; cambio de configuración sólo futuro; límites de calendario y consumo parcial según DEC-06 | F2/F3 |
| T-REDEEM | Canje insuficiente/sin stock/concurrente no entrega dos veces ni descuenta incorrectamente; comprobante y reversa según DEC-07 | F3 |
| T-BRAND | Reglas, catálogo, contenido, saldos y reportes respetan Zontes/Kiden/NIU sin fuga cruzada | F2–F6 |
| T-EXPORT | Filtros, totales, permiso y volumen de export coinciden con reportes; no exponer datos extra | F5 |
| T-UI | Cada UI-ID: escritorio/tablet/móvil, teclado/foco, contraste, carga/vacío/error/sin permiso/éxito y comparación con referencia aprobada | F1–F6 |
| T-DEMO | Flujo completo cliente + admin sobre FE↔BE, datos sintéticos y manuales; recuperación ante fallo y backup según entorno aprobado | F7 |

## Pirámide y calidad de evidencia

- BE: unitarias de reglas, normalización y fechas; transacciones/idempotencia; autorización por endpoint; integración con emulador/entorno de prueba autorizado; carga focalizada para reportes/canjes.
- FE: componentes/estados y accesibilidad; contrato tipado frente a respuestas y errores reales; recorrido extremo a extremo sólo cuando ambos repos estén listos.
- Contrato compartido: esquema versionado para payload, rol, fechas UTC/zona decidida, paginación, errores e idempotency key. Un cambio rompe o actualiza prueba de contrato antes de integrar.
- Indicadores: escenarios críticos pasados/planeados, defectos críticos abiertos, UI-ID completos/planeados, rutas BE autorizadas/protegidas, reconciliación ledger↔reportes, tiempo de respuesta medido en entorno definido. No inventar metas numéricas sin volumen/SLA aprobados.

## Corridas F0 — 2026-10-03

Entorno: Windows 11, Node 24.14.1, npm 11.11.0. FE `FidelizacionFronted` y BE `FidelizacionBackend` sobre sus commits base (`4f8ad6e`, `e9e0dd2`) con el trabajo de F0, después publicado sin cambios como `f29da45` (FE) y `747e191` (BE). Datos: ninguno; sin token, sin Firebase, sin datos personales. Responsable: agente Claude Code por encargo de Paulo. Corrida final: `npm ci`/`check`/`smoke` BE 04:40Z y FE 04:41Z; FE→BE (T07/T08) 04:46Z (UTC), sobre el mismo árbol final.

| ID | Prueba | Comando | Resultado | Límite |
| --- | --- | --- | --- | --- |
| F0-T01 | Instalación limpia BE | `npm ci` | PASS, exit 0, 424 paquetes | Sólo este host |
| F0-T02 | Instalación limpia FE | `npm ci` | PASS, exit 0, 752 paquetes | Sólo este host |
| F0-T03 | Formato + lint + typecheck + test + build BE | `npm run check` | PASS, exit 0; 23/23 pruebas | Pruebas técnicas, no de negocio |
| F0-T04 | Formato + lint + typecheck + test + build FE | `npm run check` | PASS, exit 0; 9 pasadas, 3 de integración omitidas sin BE; build de 3 rutas estáticas | Sin pruebas de componentes (desde F1) |
| F0-T05 | Arranque BE | `npm run smoke` | PASS: `GET /api/v1/health` 200 `ok`; `GET /api/v1/no-existe` 404 `NOT_FOUND` | Build de producción local |
| F0-T06 | Arranque FE | `npm run smoke` | PASS: `GET /` 200, `GET /diagnostico` 200 | No valida diseño |
| F0-T07 | FE→BE desde Node con el cliente `fetch` del FE | `INTEGRATION_API_BASE_URL=http://localhost:4000 npm run test:integration` | PASS 3/3: salud válida por contrato; CORS permite `http://localhost:3000`; CORS niega origen ajeno | BE `npm start` en :4000 |
| F0-T08 | FE→BE en navegador real | `/diagnostico` del build FE (:3000) con BE (:4000) | PASS: «Conectado (ok)», `GET http://localhost:4000/api/v1/health → 200`; el único error de consola es el `ERR_CONNECTION_REFUSED` provocado por F0-T09 | Panel de navegador de la app; captura no disponible (timeout del panel); comprobación por texto/red |
| F0-T09 | Negativo FE→BE con BE detenido | Botón «Volver a comprobar» | PASS: `role="alert"` «Sin conexión (NETWORK_ERROR)» tras ~10 s | — |
| F0-T10 | Frontera de arquitectura FE | `eslint` sobre archivo sonda con `axios`, `firebase/firestore`, `firebase-admin/auth` | PASS: 3 errores esperados (sonda borrada) | Regla estática |
| F0-T11 | Secretos en archivos versionables | patrón de claves/llaves/correos sobre `git ls-files` + no rastreados | PASS: sin coincidencias; detector probado con muestra positiva; sólo `.env.example` versionable | Heurístico |

Pruebas BE incluidas en F0-T03: contrato de salud y UTC; `X-Request-Id` (seguro respetado, inseguro reemplazado); sin `x-powered-by`; Firebase Admin no se inicializa; CORS permitido/denegado/preflight con `Authorization`; 404, 400 `INVALID_JSON`, 413, 500 sin filtrar detalle; `requireAuth` 401 sin token, 401 con esquema no Bearer, 501 sin alcanzar el handler con token no verificado; Admin SDK → 503 `AUTH_NOT_CONFIGURED` sin credenciales; configuración inválida rechazada (puerto, entorno, origen con ruta, `*`). Pruebas FE incluidas en F0-T04: URL con prefijo `/api/v1`, Bearer sólo si hay token, sobre de error → `ApiError`, 200 fuera de contrato → `INVALID_RESPONSE`, `NETWORK_ERROR`, `TIMEOUT`, configuración Firebase completa o nula.

**Fallos observados durante F0 y corregidos antes de la corrida final:** `CORS_ALLOWED_ORIGINS="*"` → excepción no controlada (FAIL → corregido); aserción libuv del smoke FE en Windows (FAIL exit 127 → corregido); tipos de mocks y `LayoutProps` en typecheck FE (FAIL → corregido). Ningún T-ID de producto (T-ROLE…T-DEMO) se ejecutó: F0 no implementa reglas de negocio.

Una captura o una compilación no es prueba de reglas. Los resultados se registrarán aquí o se enlazarán desde una nota de evidencia dentro de este Core. Ver [[05-Desarrollo/Criterio de terminado]] y [[06-Estado/Bitacora]].
