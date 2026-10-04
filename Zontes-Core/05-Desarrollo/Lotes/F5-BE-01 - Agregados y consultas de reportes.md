---
title: "F5-BE-01 — Agregados y consultas de reportes"
tags: [zontes, lote, f5, backend]
status: verificado
fase: F5
frente: BE
bloqueos: []
updated: 2026-10-03
---

# F5-BE-01 — Agregados y consultas de reportes

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: libro global `libro/{id}` escrito con cada movimiento e índice `codigos` ampliado; `/admin/reportes/{resumen,actividad,tendencias,canjes}` y `/admin/movimientos` sin índices compuestos; conciliación `npm run reportes:conciliar` (ADR-15 propuesta). Evidencia en [[05-Desarrollo/Testing]] «Corridas F5». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F5-BE-01 · F5 — Observabilidad de negocio · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | El BE entrega actividad, canjes, tendencias y KPI filtrados por marca y periodo, derivados de movimientos y canjes, con índices Firestore definidos por consulta. |
| Fuente y página | SRC-02 pp. 5–6, 14 (obs. 7) · REQ-15 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE); consumidores UI-08/09/10/20/21. |
| Reglas y decisiones | RN-09 · **DEC-09 abierta** («tiempo real», granularidad, volumen) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`: módulo de reportes. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-07: rutas de reportes bajo `/api/v1/admin/` a fijar; paginación. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F2-BE-02 - Ledger idempotente y transacciones de otorgamiento\|F2-BE-02]], [[05-Desarrollo/Lotes/F3-BE-02 - Canje atomico con saldo stock e idempotencia\|F3-BE-02]]; DEC-09. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-EXPORT (conciliación), T-HISTORY, T-BRAND · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real + recorrido integrado F5-T10)** · 2026-10-03 |

## Aceptación

- [ ] Cada KPI coincide con la suma de sus movimientos/canjes filtrados.
- [ ] Filtros por marca no mezclan datos de otras marcas.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
