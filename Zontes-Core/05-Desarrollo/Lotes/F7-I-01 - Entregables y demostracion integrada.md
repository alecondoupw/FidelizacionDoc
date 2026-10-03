---
title: "F7-I-01 — Entregables y demostracion integrada"
tags: [zontes, lote, f7, integracion]
status: bloqueado-por-decision
fase: F7
frente: Integración
bloqueos: [DEC-12, DEC-13]
updated: 2026-10-03
---

# F7-I-01 — Entregables y demostracion integrada

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F7-I-01 · F7 — Entrega y operación · Integración · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Entregar arquitectura, prototipo usuarios+puntos, código en repositorio compartido y manuales de despliegue y uso; ejecutar pruebas, backup/restauración y despliegue según DEC-13. |
| Fuente y página | SRC-01 p. 2 · REQ-21, REQ-22, REQ-23 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | Todas |
| Reglas y decisiones | DEC-12, DEC-13 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Integrador único. FE_REPO `FidelizacionFronted`, BE_REPO `FidelizacionBackend` y Core. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | Todos los aprobados. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F7-FE-01 - Recorrido demo y optimizacion medida\|F7-FE-01]], [[05-Desarrollo/Lotes/F7-BE-01 - Seguridad observabilidad respaldo y despliegue\|F7-BE-01]]/02. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-DEMO · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado por decisión: DEC-12, DEC-13** · 2026-10-03 |

## Aceptación

- [ ] Cada entregable de SRC-01 p. 2 enlazado a su evidencia.
- [ ] Cumple [[05-Desarrollo/Criterio de terminado]].
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
