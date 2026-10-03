---
title: "F2-FE-01 — Inicio saldo e historial cliente"
tags: [zontes, lote, f2, frontend]
status: verificado-con-recorrido-parcial
fase: F2
frente: FE
bloqueos: []
updated: 2026-10-03
---

# F2-FE-01 — Inicio saldo e historial cliente

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: `/inicio`, `/puntos`, `/historial` con estados de carga/error, tabla→tarjetas y paginación. Sin «saldo resultante» por movimiento (C07): ningún contrato lo provee. Evidencia en [[05-Desarrollo/Testing]] «Corridas F2». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F2-FE-01 · F2 — Motor de puntos · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Inicio, Mis puntos e Historial muestran el mismo saldo por marca, los vencimientos con la fecha del BE y los movimientos filtrables del propietario. |
| Fuente y página | SRC-03 pp. 4–6, 9 · REQ-06, REQ-10, REQ-18 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-13 · C08 · UI-03 · C07 · UI-14 · C01 |
| Reglas y decisiones | RN-07, RN-09 · DEC-06 (zona de presentación de fechas) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`: vistas del área cliente. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-04: saldo por marca y movimientos paginados del propietario (rutas a fijar en F2-BE-02). · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F2-BE-02 - Ledger idempotente y transacciones de otorgamiento\|F2-BE-02]], [[05-Desarrollo/Lotes/F1-FE-02 - Mis marcas cliente\|F1-FE-02]]. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-POINTS, T-HISTORY, T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real); recorrido integrado parcial (F2-T08)** · 2026-10-03 |

## Aceptación

- [ ] Las tres vistas usan la misma fuente; tras un movimiento nuevo coinciden.
- [ ] El total agregado es informativo; saldo y vencimiento se muestran por marca.
- [ ] Historial con filtros; tabla → tarjetas en móvil sin scroll horizontal.
- [ ] Estados de carga, vacío, error, sin permiso y éxito; confirmación en acciones irreversibles.
- [ ] Escritorio, tablet y móvil sin scroll horizontal de página; teclado, foco visible, contraste y textos accesibles.
- [ ] Cotejo con la referencia asignada y con [[02-Arquitectura/Guia visual y criterios anti slop]]; los valores del mockup no se copian como datos.
- [ ] Todo dato mostrado proviene de la respuesta del BE; ninguna regla sensible se calcula en el navegador.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
