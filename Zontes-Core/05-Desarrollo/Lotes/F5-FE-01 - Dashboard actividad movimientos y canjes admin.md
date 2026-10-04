---
title: "F5-FE-01 — Dashboard actividad movimientos y canjes admin"
tags: [zontes, lote, f5, frontend]
status: verificado
fase: F5
frente: FE
bloqueos: []
updated: 2026-10-03
---

# F5-FE-01 — Dashboard actividad movimientos y canjes admin

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: `/admin/dashboard` (entrada del panel) con KPI que abren su desglose, `/admin/actividad`, `/admin/movimientos` y `/admin/reporte-canjes` con filtros de periodo y marca en hora de Bolivia; navegación del panel agrupada como A13. Evidencia en [[05-Desarrollo/Testing]] «Corridas F5». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F5-FE-01 · F5 — Observabilidad de negocio · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Dashboard con KPI que abren su desglose, y vistas de actividad, movimientos y canjes con filtros. |
| Fuente y página | SRC-02 pp. 5–7, 8–9 · REQ-15, REQ-18, REQ-19 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-21 · A13 · UI-08 · A10 · UI-20 · A07 · UI-09 · A08 |
| Reglas y decisiones | DEC-09 · DEC-07 (estados de canje) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`: área admin con Recharts y TanStack Table. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-07 (F5-BE-01). · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F5-BE-01 - Agregados y consultas de reportes\|F5-BE-01]]. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-EXPORT, T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real + recorrido integrado F5-T10)** · 2026-10-03 |

## Aceptación

- [ ] Dashboard y reportes usan los mismos agregados; un KPI abre los movimientos que lo componen.
- [ ] Sin edición manual de saldo en movimientos.
- [ ] Estados de carga, vacío, error, sin permiso y éxito; confirmación en acciones irreversibles.
- [ ] Escritorio, tablet y móvil sin scroll horizontal de página; teclado, foco visible, contraste y textos accesibles.
- [ ] Cotejo con la referencia asignada y con [[02-Arquitectura/Guia visual y criterios anti slop]]; los valores del mockup no se copian como datos.
- [ ] Todo dato mostrado proviene de la respuesta del BE; ninguna regla sensible se calcula en el navegador.
- [ ] Admin sin mockup móvil: diseñar y verificar tablet/móvil según SRC-02 p. 8 (navegación compacta, formularios de una columna, tablas legibles o scroll justificado).
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
