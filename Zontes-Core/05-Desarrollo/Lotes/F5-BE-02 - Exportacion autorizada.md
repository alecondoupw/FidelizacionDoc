---
title: "F5-BE-02 — Exportacion autorizada"
tags: [zontes, lote, f5, backend]
status: bloqueado-por-decision
fase: F5
frente: BE
bloqueos: [DEC-09]
updated: 2026-10-03
---

# F5-BE-02 — Exportacion autorizada

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F5-BE-02 · F5 — Observabilidad de negocio · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | La API exporta clientes, movimientos, canjes y reportes con los filtros efectivos, autorización, encabezados claros y volumen controlado. |
| Fuente y página | SRC-02 pp. 6–7, 12, 14 (obs. 8) · REQ-16 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE); consumidor UI-11. |
| Reglas y decisiones | RN-11 · **DEC-09 abierta** (formatos, volumen, colas) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`; SheetJS se instala aquí si DEC-09 lo confirma. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-07: exportación filtrada (síncrona o por trabajo según volumen). · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F5-BE-01 - Agregados y consultas de reportes\|F5-BE-01]]; DEC-09. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-EXPORT, T-AUTHZ · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado por decisión: DEC-09** · 2026-10-03 |

## Aceptación

- [ ] El archivo contiene exactamente las filas de la pantalla con los mismos filtros.
- [ ] No incluye columnas sensibles fuera de permiso.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
