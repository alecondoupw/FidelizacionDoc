---
title: "F7-BE-02 — Documentacion API y operacion"
tags: [zontes, lote, f7, backend]
status: pendiente
fase: F7
frente: BE
bloqueos: [DEC-13]
updated: 2026-10-03
---

# F7-BE-02 — Documentacion API y operacion

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F7-BE-02 · F7 — Entrega y operación · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Documentación de la API, colección de pruebas manuales y manual de despliegue y operación. |
| Fuente y página | SRC-01 p. 2; SRC-02 p. 13 (Postman) · REQ-21, REQ-22 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica. |
| Reglas y decisiones | DEC-13 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`; manuales en [[07-Manuales/Manual de usuario]]. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | Refleja todos los contratos aprobados. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | Endpoints implementados; [[05-Desarrollo/Lotes/F7-BE-01 - Seguridad observabilidad respaldo y despliegue\|F7-BE-01]]. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | Revisión contra pruebas de contrato · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Pendiente: crece con cada fase; cierre bloqueado por DEC-13** · 2026-10-03 |

## Aceptación

- [ ] Cada endpoint documentado con actor, permisos, errores y ejemplo sintético.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
