---
title: "F3-BE-01 — Catalogo de beneficios por marca"
tags: [zontes, lote, f3, backend]
status: bloqueado-por-decision
fase: F3
frente: BE
bloqueos: [DEC-07, DEC-02]
updated: 2026-10-03
---

# F3-BE-01 — Catalogo de beneficios por marca

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F3-BE-01 · F3 — Beneficios y canje · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | El BE entrega catálogo y detalle de beneficios sólo de marcas vinculadas del cliente, con costo, disponibilidad, búsqueda y filtros. |
| Fuente y página | SRC-01 p. 1; SRC-03 pp. 6–7, 12 · REQ-11 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE); consumidor UI-05. |
| Reglas y decisiones | RN-08, RN-09 · **DEC-07 abierta** (origen y gestión del catálogo, variantes, stock) · DEC-11 (imágenes y licencias) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`: módulo de beneficios; imágenes en Storage sólo si se autoriza. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-05: catálogo paginado por marca, filtros y detalle (a fijar). · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]]; DEC-07; DEC-02. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-BRAND, T-AUTHZ · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado por decisión: DEC-07** · 2026-10-03 |

## Aceptación

- [ ] Un cliente nunca recibe beneficios de una marca no vinculada.
- [ ] La disponibilidad viene del BE; categorías y variantes corresponden al catálogo real, no al mockup.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
