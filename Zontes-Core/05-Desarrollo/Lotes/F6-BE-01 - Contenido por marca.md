---
title: "F6-BE-01 — Contenido por marca"
tags: [zontes, lote, f6, backend]
status: bloqueado-por-decision
fase: F6
frente: BE
bloqueos: [DEC-10, DEC-11]
updated: 2026-10-03
---

# F6-BE-01 — Contenido por marca

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F6-BE-01 · F6 — Contenido y calidad visual · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | El admin crea, edita, activa/desactiva y elimina contenido de una marca; el cliente sólo recibe contenido activo de sus marcas. |
| Fuente y página | SRC-01 p. 1; SRC-02 p. 7 · REQ-17 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE); consumidor UI-12. |
| Reglas y decisiones | RN-09 · **DEC-10 abierta** (tipos, programación) · **DEC-11** (activos y licencias) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`; Storage sólo con archivos autorizados. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-08 a fijar. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]]; DEC-10/11. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-BRAND, T-AUTHZ · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado por decisión: DEC-10, DEC-11** · 2026-10-03 |

## Aceptación

- [ ] Contenido inactivo o de otra marca nunca llega al cliente.
- [ ] Archivos privados sólo con acceso autorizado.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
