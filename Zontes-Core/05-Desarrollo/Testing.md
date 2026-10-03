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

## Corridas F1 — 2026-10-03 (dobles de prueba, sin Firebase real)

Entorno: el mismo de F0; código publicado en `main` como FE `71184a5` y BE `8fce35e`. Datos sintéticos (`ejemplo.test`). Firebase Auth y Firestore **sustituidos por dobles** en F1-T01…T07; F1-T08 y F1-T10 se ejecutaron después contra el proyecto de desarrollo que Paulo creó y configuró en los `.env` (las credenciales no se leyeron ni se registran aquí).

| ID | Prueba | Comando | Resultado | Límite |
| --- | --- | --- | --- | --- |
| F1-T01 | BE completo | `npm run check` (FidelizacionBackend) | PASS, exit 0; 63 pasadas, 5 omitidas (Firestore real) | Dobles de Auth y Firestore |
| F1-T02 | Arranque BE | `npm run smoke` | PASS 2/2 | — |
| F1-T03 | FE completo | `npm run check` (FidelizacionFronted) | PASS, exit 0; 43 pasadas, 3 omitidas (integración) | Componentes en jsdom con sesión simulada |
| F1-T04 | Arranque FE | `npm run smoke` | PASS 7/7; las rutas protegidas sólo envían «Cargando tu cuenta» desde el servidor | — |
| F1-T05 | FE→BE en vivo, BE sin Firebase | `curl` + `npm run test:integration` | `/me` sin token → 401; con token → 503 `AUTH_NOT_CONFIGURED`; preflight con `Authorization` desde `localhost:3000` → 204; integración 3/3 | Sin token real |
| F1-T06 | Mutaciones de seguridad | quitar la verificación de correo y `requireRole` | Las pruebas correspondientes fallan (2) y vuelven a pasar al restaurar | — |
| F1-T07 | Navegador real (Chrome del panel de la app) | `/ingresar`, `/registro`, `/admin/ingresar` en escritorio y 375 px; `/marcas` sin sesión | Sin scroll horizontal; aviso de Firebase no configurado; `/marcas` redirige a `/ingresar` | Sin sesión real: las vistas protegidas sólo se ven en pruebas de componentes |
| F1-T08 | Firestore real (proyecto de desarrollo de Paulo) | `FIRESTORE_INTEGRATION=1 npm run test:firebase` | **PASS 2026-10-03 06:39Z**, exit 0: 10/10 (5 memoria + 5 Firestore, ninguna omitida). Limpieza verificada: el proyecto queda sin colecciones | Registro, unicidad de uid y de correo en transacción, administrador activo/inactivo; no prueba concurrencia real entre dos procesos |
| F1-T10 | Admin SDK real ante tokens inválidos | BE `npm start` con el proyecto + `curl` a `/me` y `/clientes/registro` | **PASS:** token malformado y JWT con firma falsa → 401 `UNAUTHENTICATED`; sin errores en el servidor | No prueba un token válido: requiere iniciar sesión (F1-T09) |
| F1-T09 | Recorrido integrado F1-I-01 en navegador | Paulo crea el admin (`admin:bootstrap`) y el usuario `cliente.multimarca@ejemplo.test` (`dev:usuario-prueba`); el agente levanta BE (:4000) y FE (:3000) contra el proyecto de desarrollo; **Paulo** inicia sesión | **PASS, informado por Paulo (2026-10-03):** cliente → verificación → vínculo con Zontes, Kiden y NIU → Mis marcas y cambio de marca activa → Mi perfil → cierre de sesión; admin → Mi perfil; cuenta de cliente rechazada en el acceso de administración | El agente no vio las pantallas autenticadas; evidencia de servidor en F1-T11 |
| F1-T11 | Estado de Firestore tras F1-T09 | script de lectura con Admin SDK (sólo conteos, roles y marcas; sin imprimir correos) | **PASS:** 2 perfiles (admin activo sin marcas; cliente activo `vinculado` con zontes, kiden, niu); 2 índices de correo, cada uno apunta a su perfil, 0 huérfanos; correos normalizados; 2 eventos de auditoría (`administrador.bootstrap`, `cliente.registrado` por el propio usuario), ninguno con «@»; log del BE sin errores | — |

Escenarios cubiertos con dobles: **T-AUTHZ** (sin token, malformado, expirado, revocado, esquema no Bearer, inactivo, sin registro, fallo de infraestructura → 500), **T-ROLE** (cliente en ruta de admin → 403; bootstrap sólo una vez, idempotente, nunca promueve a un cliente), **T-LINK** (normalización con mayúsculas/espacios, sin coincidencia, correo no verificado, correo del cuerpo ignorado, mismo uid → 409, mismo correo con otro uid → 409, auditoría sin correo). En el FE: ingreso por rol, mensajes que no revelan si una cuenta existe, aviso de sesión expirada, registro por pasos con verificación, resultado vinculado y no vinculado, Mis marcas sólo con marcas del backend y marca activa inválida descartada.

Fallos encontrados y corregidos en F1: contrato de prueba de Firestore construido fuera de `beforeAll`; prueba de configuración por defecto desactualizada; finales CRLF tras `git checkout` que rompían `prettier --check` (se añadió `.gitattributes` con `eol=lf` en FE y BE); etiquetas de pasos ocultas a lectores de pantalla en móvil; marcador del smoke que pasaba por el `<title>`.

## Corridas F2 — 2026-10-03

Mismo entorno; código publicado en `main` como BE `7e5589a` y FE `e4278a2`. Firestore real = proyecto de desarrollo de Paulo con colecciones temporales `prueba_*` borradas al terminar.

| ID | Prueba | Comando | Resultado | Límite |
| --- | --- | --- | --- | --- |
| F2-T01 | BE completo con dobles | `npm run check` (FidelizacionBackend) | PASS, exit 0; 116 pasadas, 30 omitidas (Firestore) | — |
| F2-T02 | Contratos contra Firestore real | `FIRESTORE_INTEGRATION=1 npm run test:firebase` | **Primera corrida FAIL 5/61:** ordenar por id descendente exige índice; corregido con ids invertidos. **Corrida final PASS 61/61** (almacén, perfiles y motor de puntos completo) y proyecto sin restos | Sin concurrencia real entre procesos |
| F2-T03 | Mutaciones | quitar idempotencia, aislamiento por marca o control de saldo | Fallan 3, 1 y 3 pruebas; restaurado todo pasa | — |
| F2-T04 | Arranque BE | `npm run smoke` | PASS 2/2 | — |
| F2-T05 | FE completo | `npm run check` (FidelizacionFronted) | PASS, exit 0; 66 pasadas | Componentes con sesión simulada |
| F2-T06 | Arranque FE | `npm run smoke` | PASS 11/11; `/inicio`, `/historial`, `/admin/reglas`, `/admin/registrar` sólo envían «Cargando tu cuenta» | — |
| F2-T07 | Rutas F2 en vivo sin credenciales | `curl` al BE nuevo | `/me/saldo` 401, `/admin/reglas` 401, `/integracion/eventos` 503 sin claves | — |
| F2-T08 | Recorrido integrado F2-I-01 en navegador | Paulo inicia sesión como admin con BE (:4000) y FE (:3000) contra el proyecto de desarrollo | **PARCIAL (2026-10-03, decisión de Paulo):** creó la regla «Compra · Kiden · 4»; registró una compra Kiden que otorgó +4 y un evento sin regla que quedó sin puntos | Sin probar por la interfaz: vencimiento por marca, ajustes (incluido el rechazo por saldo insuficiente), edición/activación/eliminación de reglas y la vista del cliente no se ejercitaron por la interfaz con Firebase real; cubiertos por F2-T01/T02/T05 |
| F2-T09 | Estado de Firestore tras F2-T08 | script de lectura con Admin SDK (sin correos ni uid) | **PASS:** saldo materializado Kiden = 4 = suma de lotes (un lote sin vencimiento); 2 registros de idempotencia (otorgado y sin puntos); 0 vencimientos pendientes; auditoría `regla.creada` sin «@»; log del BE sin errores | — |

Escenarios cubiertos: **T-RULE** (combinación única, sin condición, sin negativos/decimales, cambio sólo futuro), **T-POINTS** (mismo origen + id no otorga dos veces, conflicto con otros datos, regla inactiva o ausente sin puntos), **T-BRAND** (cliente no vinculado rechazado, saldos y filtros por marca), **T-EXP** (fin de mes, bisiesto, día local de Bolivia, último milisegundo, vencimiento al leer el saldo, proceso reejecutable, cambio de vigencia sin efecto retroactivo), **T-HISTORY** (vencimiento y ajustes como movimientos con motivo, auditoría sin correos, conciliación saldo = suma de lotes). FE: resumen singular/plural, reglas (crear, validar, conflicto, activar, eliminar con confirmación), vencimiento (máximo 10 años, historial), registro de eventos con la misma clave al reintentar, ajuste con motivo y saldo insuficiente, inicio con error parcial, historial paginado y filtrado.

## Corridas F3 — 2026-10-03

Mismo entorno; código publicado en `main` como BE `e8bbc7c` y FE `b2cf41b`. Firestore real = proyecto de desarrollo de Paulo con colecciones temporales `prueba_*` borradas al terminar.

| ID | Prueba | Comando | Resultado | Límite |
| --- | --- | --- | --- | --- |
| F3-T01 | BE completo con dobles | `npm run check` (FidelizacionBackend) | PASS, exit 0; 136 pasadas, 43 omitidas (Firestore) | — |
| F3-T02 | Contratos contra Firestore real | `FIRESTORE_INTEGRATION=1 npm run test:firebase` | PASS 87/87 (almacén, perfiles, motor de puntos y canjes, incluido el canje concurrente de la última unidad: uno gana y el otro recibe `OUT_OF_STOCK`); proyecto sin restos | Concurrencia dentro de un proceso, no entre instancias |
| F3-T03 | Mutaciones BE | quitar el control de propietario del canje, el de stock o el de marca vinculada | Cada una hace fallar 1–2 pruebas de la suite de contrato; restaurado todo pasa | — |
| F3-T04 | Arranque BE | `npm run smoke` | PASS 2/2 | — |
| F3-T05 | FE completo | `npm run check` (FidelizacionFronted) | PASS, exit 0; 83 pasadas, 3 omitidas; build con `/catalogo`, `/catalogo/[id]`, `/canjes`, `/canjes/[codigo]`, `/admin/beneficios`, `/admin/canjes` | Componentes con sesión simulada |
| F3-T06 | Mutación FE | regenerar `idSolicitud` tras un error de canje | Falla 1 prueba («reintenta con el mismo idSolicitud»); restaurado pasa | — |
| F3-T07 | Arranque FE | `npm run smoke` | PASS 17/17; las seis rutas F3 sólo envían «Cargando tu cuenta» | — |
| F3-T08 | Recorrido integrado F3-I-01 en navegador | Paulo con BE (:4000) y FE (:3000) contra el proyecto de desarrollo | **PARCIAL (2026-10-03, decisión de Paulo):** catálogo de ejemplo cargado y un canje real por la interfaz: «Descuento en repuestos» Kiden por 4 puntos | Entrega, anulación y edición de beneficios quedan cubiertas sólo por F3-T01/T02/T05. Sin registro en Firestore de entrega, anulación, ajuste de puntos ni alta/edición de beneficios por la interfaz; las vistas de sólo lectura (catálogo, detalle, QR, PDF) no dejan rastro y el BE no registra peticiones |
| F3-T09 | Estado de Firestore tras F3-T08 | script de lectura con Admin SDK (sin correos ni uid) | **PASS:** 1 canje `emitido` con vigencia 15 días (fin del 18-10 en Bolivia = `2026-10-19T03:59:59.999Z`), movimiento `canje −4` e índice `codigos` enlazados, 1 registro de idempotencia `canje`; stock de 9 variantes = inicial − canjes no anulados; saldo Kiden 0 = suma de lotes = suma de movimientos; 0 vencimientos pendientes; auditoría sin «@» | — |

Escenarios cubiertos: **T-BRAND** (catálogo y detalle sólo de marcas vinculadas, 403/404 en otra marca, filtros FE sólo con marcas propias), **T-POINTS** (saldo insuficiente, reintento con la misma solicitud devuelve el mismo canje, conflicto con otros datos), stock por variante (agotado, últimas, sin límite, próximamente, devolución al anular), **T-EXP** (lotes consumidos por vencimiento más próximo; al anular se reponen y lo ya caducado vuelve a vencer), **T-HISTORY** (movimientos `canje` con motivo, auditoría de beneficios, entrega y anulación sin correos), propiedad del comprobante (PDF y QR sólo del propietario; otro cliente recibe 404).

## Corridas F4 — 2026-10-03

Mismo entorno; código publicado en `main` como BE `403819b` y FE `6fb0035`. Firestore real = proyecto de desarrollo de Paulo con colecciones temporales `prueba_*` (un prefijo por prueba de identidades) borradas al terminar. **Firebase Auth siempre es un doble en las pruebas**: no se crearon cuentas reales.

| ID | Prueba | Comando | Resultado | Límite |
| --- | --- | --- | --- | --- |
| F4-T01 | BE completo con dobles | `npm run check` (FidelizacionBackend) | PASS, exit 0; 164 pasadas, 57 omitidas (Firestore) | — |
| F4-T02 | Contratos contra Firestore real | `FIRESTORE_INTEGRATION=1 npm run test:firebase` | PASS 120/120: perfiles sobre el almacén, `array-contains` + igualdades + orden por id sin índice, identidades completas incluida la **desactivación cruzada simultánea** (una pasa, otra `LAST_ADMIN`); 0 colecciones `prueba_*` restantes | Auth real no ejercitado (invitación, cambio de correo y borrado en Auth) |
| F4-T03 | Mutaciones BE | quitar: protección del último activo, control propio, exigencia de verificación tras cambio de correo, control de rol cliente, recálculo del vínculo | Fallan 2, 2, 1, 1 y 2 pruebas; restaurado todo pasa | — |
| F4-T04 | FE completo | `npm run check` (FidelizacionFronted) | PASS, exit 0; 92 pasadas, 3 omitidas | Componentes con sesión simulada |
| F4-T05 | Mutación FE | cambiar el correo sin el diálogo de confirmación | Falla 1 prueba; restaurado pasa | — |
| F4-T06 | Arranque FE | `npm run smoke` | PASS 21/21; `/admin/clientes`, `/admin/clientes/[uid]`, `/admin/administradores` sólo envían «Cargando tu cuenta» | — |
| F4-T07 | Recorrido integrado F4-I-01 en navegador | Paulo con BE (:4000) y FE (:3000) contra el proyecto de desarrollo | **PARCIAL (2026-10-03, decisión de Paulo):** recorrido sin escrituras de F4 en Firestore ni Auth | Invitación por correo, cambio de correo con verificación, baja, cambio de nombre y de contraseña con Firebase Auth real quedan cubiertos sólo por F4-T01…T05 (Auth con doble). Sin alta ni invitación de administradores, cambios de nombre, estado o correo, ni bajas; las vistas de sólo lectura no dejan rastro y el BE no registra peticiones |
| F4-T08 | Estado de Firestore y Auth tras F4-T07 | script de lectura con Admin SDK (sin correos; uid abreviados) | **PASS de coherencia:** 2 cuentas de Auth = 2 perfiles (1 admin activo, 1 cliente vinculado a 3 marcas), correo de Auth = correo del perfil, índices de correo correctos y sin colgantes, 0 cuentas de Auth sin perfil, 0 vencimientos pendientes, saldo = lotes = movimientos, auditoría sin «@». Último evento de auditoría 14:34 UTC y últimos ingresos 14:41/14:57 UTC, anteriores al recorrido | Nada de F4 que verificar en datos reales |

Escenarios cubiertos: **T-ROLE/T-AUTHZ** (cliente → 403 en las 9 rutas, sin token → 401, cuerpos estrictos: no se puede enviar rol, marcas ni correo de admin; un correo de cliente o de una cuenta de Auth sin perfil no se convierte en admin; sin cuenta de Auth huérfana si falla el perfil; último activo y cuenta propia protegidos; admin desactivado sin acceso), **T-LINK** (cambio de correo recalcula marcas sólo con el correo nuevo, sin coincidencia queda no vinculado, correo ocupado en Firestore o en Auth → 409 y Auth vuelve al correo anterior, verificación exigida y sesiones revocadas), **T-HISTORY** (un evento por operación, sin «@», historial con formatos F1 y F2–F4, saldo de marca desvinculada conservado y visible, baja que conserva movimientos y canjes y libera el correo). FE: alta con invitación por correo de Firebase y error 409, «Tú» sin desactivar ni eliminar, rechazo `LAST_ADMIN` visible, eliminación confirmada, lista de clientes con filtros y búsqueda exacta, cambio de correo con confirmación y vínculo recalculado, baja confirmada, edición del propio nombre y correo de contraseña, desvío a `/verificar-correo`.

Fallo encontrado y corregido en F4: los nombres accesibles de «Gestionar» (F4) y «Ver beneficios» (F3) se leían pegados («Gestionara…», «Ver beneficiosde…») porque el espacio inicial dentro del texto sólo para lectores de pantalla se descarta; ahora usan `aria-label`. El doble de pruebas del FE construía respuestas 204 con cuerpo, que `Response` rechaza; corregido.

## Corridas F5 — 2026-10-03

Mismo entorno; código publicado en `main` como BE `a4f5014` y FE `7d8e3ce`. Firestore real = proyecto de desarrollo de Paulo con colecciones temporales `prueba_*` borradas al terminar; Auth siempre con doble.

| ID | Prueba | Comando | Resultado | Límite |
| --- | --- | --- | --- | --- |
| F5-T01 | BE completo con dobles | `npm run check` (FidelizacionBackend) | PASS, exit 0; 182 pasadas, 65 omitidas (Firestore) | — |
| F5-T02 | Contratos contra Firestore real | `FIRESTORE_INTEGRATION=1 npm run test:firebase` | PASS 138/138: libro global y conciliación, rangos de un campo, `count()` con `array-contains`, listado del libro con igualdades + orden por id + cursor, actividad, tendencias, canjes, dashboard y exportaciones con datos generados por los flujos reales | Volumen de demostración; topes probados en memoria |
| F5-T03 | Limpieza del proyecto | listado de colecciones tras F5-T02 | **Primera corrida: 2 colecciones `prueba_*_libro` restantes** (las suites F2/F3 no limpiaban el libro nuevo); corregido y borradas. **Corrida final: 0 restos** | — |
| F5-T04 | Mutaciones BE | quitar: asiento del libro, anulaciones en «utilizados», exclusión de bajas en clientes, protección de fórmulas CSV, tope de 10.000 filas, máximo de 12 meses | Fallan 7, 2, 1, 2, 1 y 2 pruebas; restaurado todo pasa | — |
| F5-T05 | Arranque BE | `npm run smoke` | PASS 2/2 | — |
| F5-T06 | Conciliación del proyecto real (sólo lectura) | `npm run reportes:conciliar` | 2 movimientos y 1 canje de F2/F3 sin asiento ni índice ampliado (anteriores al libro). **Con autorización de Paulo:** `-- --reparar` aplicó 3 escrituras; la conciliación siguiente sale limpia (2 = 2, 0 índices desactualizados) y el dashboard real muestra 1 cliente, 4 pts otorgados, 4 utilizados y 1 canje pendiente, igual a los datos de F2–F3 | — |
| F5-T07 | FE completo | `npm run check` (FidelizacionFronted) | PASS, exit 0; 102 pasadas, 3 omitidas | Componentes con sesión simulada; gráficos verificados por su tabla accesible |
| F5-T08 | Mutación FE | quitar el filtro de tipo del desglose del KPI «Puntos otorgados» | Falla 1 prueba; restaurado pasa | — |
| F5-T09 | Arranque FE | `npm run smoke` | PASS 27/27; las seis rutas F5 sólo envían «Cargando tu cuenta» | — |
| F5-T10 | Recorrido integrado F5-I-01 en navegador | Paulo con BE (:4000) y FE (:3000) | **PASS (2026-10-03).** Exportaciones reales auditadas con filtros y sin correos: canjes en Excel (18:42 y 18:50 UTC) y en **CSV** (18:50 UTC), que Paulo abrió en Excel con columnas y tildes correctas; un primer «CSV» que Paulo informó no llegó al backend y se repitió. Paulo confirmó el aviso al pedir un rango de más de 12 meses. Recorrió las pantallas de reportes | Exportación de movimientos y clientes sólo por pruebas automáticas (mismo generador CSV/Excel); volumen de demostración (1 cliente, 4 pts, 1 canje); sin nuevos movimientos ni canjes |
| F5-T11 | Estado de Firestore tras F5-T10 | `npm run reportes:conciliar` + lectura con Admin SDK (sin correos; uid abreviados) | **PASS:** libro 2 = movimientos 2, 0 índices desactualizados, saldo Kiden 0 = lotes = movimientos, stock de los 6 beneficios sin cambios, 0 vencimientos pendientes, 11 eventos de auditoría sin «@»; tras completar el recorrido, 13 eventos sin «@» | — |

Escenarios cubiertos: **T-HISTORY/conciliación** (13 movimientos = 13 asientos, 3 canjes con índice completo; detección y reparación de datos previos sin borrar), **T-EXPORT** (filtros efectivos, columnas, CSV con BOM, `;` y fórmulas neutralizadas, .xlsx válido, tope de 10.000 filas, auditoría sin correos), **T-AUTHZ** (cliente → 403 en las 7 rutas), **T-BRAND** (filtros por marca, registros contados en cada marca vinculada, comparación entre marcas), periodos (borde de medianoche en Bolivia, semanas desde el lunes, meses, periodo anterior, máximo 12 meses). FE: KPI con variación que abren su desglose, actividad por evento enlazada a movimientos, tendencias con periodo anterior y enlace al origen, filtros de movimientos y canjes que viajan a Exportar, vista previa con rechazo por volumen y descarga. FE: catálogo con filtros, detalle con bloqueo explicado (saldo, agotado, próximamente), confirmación y resultado con código, Mis canjes, detalle con QR y descarga, anulado sin QR, ajeno con error; admin: ids de opción, crear con errores del backend, editar con PUT conservando ids, entregar, anular con motivo obligatorio.

Una captura o una compilación no es prueba de reglas. Los resultados se registrarán aquí o se enlazarán desde una nota de evidencia dentro de este Core. Ver [[05-Desarrollo/Criterio de terminado]] y [[06-Estado/Bitacora]].
