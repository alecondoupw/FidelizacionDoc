---
title: "F2-I-01 — Integracion evento a saldo e historial"
tags: [zontes, lote, f2, integracion]
status: verificado-con-recorrido-parcial
fase: F2
frente: Integración
bloqueos: []
updated: 2026-10-03
---

# F2-I-01 — Integracion evento a saldo e historial

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F2-I-01 · F2 — Motor de puntos · Integración · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Un evento realista llega desde su origen autorizado hasta saldo e historial del cliente y del admin, incluyendo el borde de vencimiento. |
| Fuente y página | SRC-01 p. 1; SRC-02 pp. 4–5, 14 · REQ-07–REQ-10 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-03, UI-13, UI-14, UI-04, UI-19 |
| Reglas y decisiones | RN-04–RN-07 · DEC-05, DEC-06, DEC-14 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Integrador único. FE_REPO `FidelizacionFronted` y BE_REPO `FidelizacionBackend`. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-03 e I-04 aprobados y versionados. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F2-BE-01 - Reglas de puntos por marca y evento\|F2-BE-01]]/02/03, [[05-Desarrollo/Lotes/F2-FE-01 - Inicio saldo e historial cliente\|F2-FE-01]]/02. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-RULE, T-HISTORY, T-POINTS, T-EXP · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Recorrido parcial aceptado por Usuario (2026-10-03): reglas, otorgamiento, evento sin regla y saldo verificados con Firebase real (F2-T08/T09); vencimiento por marca, ajustes (incluido el rechazo por saldo insuficiente), edición/activación/eliminación de reglas y la vista del cliente no se ejercitaron por la interfaz con Firebase real** · 2026-10-03 |

## Aceptación

- [ ] Evento repetido no duplica; regla inactiva no otorga; cambio de regla sólo futuro.
- [ ] Vencimiento en el borde definido por DEC-06 visible en ambos roles.
- [ ] Saldo de vistas = suma reconciliada de movimientos por marca.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
