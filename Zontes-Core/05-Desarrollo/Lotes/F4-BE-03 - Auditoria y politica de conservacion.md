---
title: "F4-BE-03 — Auditoria y politica de conservacion"
tags: [zontes, lote, f4, backend]
status: bloqueado-por-decision
fase: F4
frente: BE
bloqueos: [DEC-08]
updated: 2026-10-03
---

# F4-BE-03 — Auditoria y politica de conservacion

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F4-BE-03 · F4 — Administración de identidades · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Los cambios de administradores, clientes, reglas y configuración dejan eventos de auditoría consultables con actor, marca, momento y antes/después permitido, conservados según la política acordada. |
| Fuente y página | SRC-02 pp. 2–3, 5 · REQ-13, REQ-14, REQ-09 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica. |
| Reglas y decisiones | RN-02, RN-05 · **DEC-08 abierta** (retención y privacidad) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`: módulo de auditoría transversal. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | Consulta admin de auditoría a fijar. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F4-BE-01 - Gestion de administradores y ultimo activo\|F4-BE-01]]/02; DEC-08. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-HISTORY, T-AUTHZ · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado por decisión: DEC-08** · 2026-10-03 |

## Aceptación

- [ ] Cada mutación sensible produce exactamente un evento de auditoría.
- [ ] La auditoría no guarda contraseñas, tokens ni datos excluidos por DEC-08.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
