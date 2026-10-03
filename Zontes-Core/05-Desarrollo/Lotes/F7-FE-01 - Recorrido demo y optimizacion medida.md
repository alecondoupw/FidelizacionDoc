---
title: "F7-FE-01 — Recorrido demo y optimizacion medida"
tags: [zontes, lote, f7, frontend]
status: bloqueado-por-decision
fase: F7
frente: FE
bloqueos: [DEC-12, DEC-13]
updated: 2026-10-03
---

# F7-FE-01 — Recorrido demo y optimizacion medida

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F7-FE-01 · F7 — Entrega y operación · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Recorrido demo cliente y admin sin errores, con mejoras de rendimiento medidas, no supuestas. |
| Fuente y página | SRC-01 p. 2 · REQ-22 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | Todas |
| Reglas y decisiones | DEC-12 (hitos), DEC-13 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | Todos los aprobados. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | F1–F6 verificadas. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-DEMO, T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado: depende de F1–F6 y DEC-12/13** · 2026-10-03 |

## Aceptación

- [ ] Guion de demo reproducible con datos sintéticos.
- [ ] Métricas antes/después registradas en el Core.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
