---
title: "Plan de pruebas e indicadores"
tags: [zontes, testing]
status: planificado
updated: 2026-10-02
---

# Plan de pruebas e indicadores

**Estado inicial: 0 pruebas de producto ejecutadas.** Los IDs son escenarios de aceptación derivados de SRC-01/02/03 y organizados para implementación; no son resultados. La trazabilidad por página está en [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] y los flujos en [[02-Arquitectura/Contratos de integracion por flujo]]. Registrar para cada corrida: fecha, FE/BE revisión, entorno, datos sintéticos, esperado, observado, evidencia, defectos y responsable. Evitar datos personales reales en capturas.

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

Una captura o una compilación no es prueba de reglas. Los resultados se registrarán aquí o se enlazarán desde una nota de evidencia dentro de este Core. Ver [[05-Desarrollo/Criterio de terminado]] y [[06-Estado/Bitacora]].
