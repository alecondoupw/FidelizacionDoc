---
title: "F6-FE-02 — Cotejo visual de cada UI-ID"
tags: [zontes, lote, f6, frontend]
status: pendiente
fase: F6
frente: FE
bloqueos: [DEC-11]
updated: 2026-10-03
---

# F6-FE-02 — Cotejo visual de cada UI-ID

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F6-FE-02 · F6 — Contenido y calidad visual · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Cada UI-ID construida se compara con su referencia y con la guía visual durante su fase; aquí se consolida la revisión. |
| Fuente y página | SRC-02 pp. 8–9; SRC-03 pp. 2, 9–10 · REQ-18, REQ-19 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | Todas: C01–C10, A01–A13 según [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]] |
| Reglas y decisiones | ADR-07 · DEC-11 (identidad final) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE + revisión de Paulo. FE_REPO `FidelizacionFronted`. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | No aplica. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | UI-ID implementadas en F1–F5. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Pendiente: transversal, se ejecuta al cerrar cada UI-ID** · 2026-10-03 |

## Aceptación

- [ ] Captura de implementación por UI-ID en escritorio, tablet y móvil enlazada desde el Core.
- [ ] Diferencias con la referencia anotadas y aprobadas o corregidas.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
