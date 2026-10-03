---
title: "F6-I-01 — Integracion de contenido y revision visual"
tags: [zontes, lote, f6, integracion]
status: bloqueado-por-decision
fase: F6
frente: Integración
bloqueos: [DEC-10, DEC-11]
updated: 2026-10-03
---

# F6-I-01 — Integracion de contenido y revision visual

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F6-I-01 · F6 — Contenido y calidad visual · Integración · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Comparar con referencias y tareas reales, no sólo con capturas estéticas, y probar aislamiento de contenido por marca. |
| Fuente y página | SRC-02 pp. 7–9 · REQ-17–REQ-19 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-12 y todas las UI-ID |
| Reglas y decisiones | RN-09 · DEC-10, DEC-11 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Integrador único. FE_REPO `FidelizacionFronted` y BE_REPO `FidelizacionBackend`. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-08 aprobado. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F6-BE-01 - Contenido por marca\|F6-BE-01]], [[05-Desarrollo/Lotes/F6-FE-01 - Contenido por marca admin\|F6-FE-01]]/02/03. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-UI, T-BRAND · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado por decisión: DEC-10, DEC-11** · 2026-10-03 |

## Aceptación

- [ ] Recorridos reales por rol completados en tres tamaños sin bloqueos de accesibilidad.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
