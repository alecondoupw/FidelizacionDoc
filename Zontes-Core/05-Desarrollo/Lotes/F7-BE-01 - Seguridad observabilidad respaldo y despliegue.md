---
title: "F7-BE-01 — Seguridad observabilidad respaldo y despliegue"
tags: [zontes, lote, f7, backend]
status: bloqueado-por-decision
fase: F7
frente: BE
bloqueos: [DEC-13, DEC-02]
updated: 2026-10-03
---

# F7-BE-01 — Seguridad observabilidad respaldo y despliegue

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F7-BE-01 · F7 — Entrega y operación · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Observabilidad, revisión de seguridad, backup y restauración probados y despliegue en un entorno autorizado. |
| Fuente y página | SRC-01 p. 2; SRC-02 p. 2 · REQ-21, REQ-22 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica. |
| Reglas y decisiones | **DEC-13 abierta** (entorno, backups, integraciones) · DEC-02 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE + Paulo para autorizaciones. BE_REPO `FidelizacionBackend`. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | Todos los aprobados. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | F1–F6; DEC-13. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-DEMO · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado por decisión: DEC-13** · 2026-10-03 |

## Aceptación

- [ ] Restauración probada desde backup.
- [ ] Despliegue sólo tras autorización expresa.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
