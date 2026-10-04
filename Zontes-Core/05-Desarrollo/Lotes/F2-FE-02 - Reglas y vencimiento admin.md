---
title: "F2-FE-02 — Reglas y vencimiento admin"
tags: [zontes, lote, f2, frontend]
status: verificado-con-recorrido-parcial
fase: F2
frente: FE
bloqueos: []
updated: 2026-10-03
---

# F2-FE-02 — Reglas y vencimiento admin

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: `/admin/reglas` con resumen dinámico y confirmación al eliminar; `/admin/vencimiento` sin el campo de fecha de A06 (sería retroactivo, contra SRC-02 p. 5); `/admin/registrar` (UI-24 propuesta) para eventos y ajustes. Evidencia en [[05-Desarrollo/Testing]] «Corridas F2». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F2-FE-02 · F2 — Motor de puntos · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | El admin gestiona reglas (lista, filtros, crear/editar con vista previa singular/plural, activar/desactivar, eliminar con confirmación) y la vigencia por marca con su historial. |
| Fuente y página | SRC-02 pp. 3–5, 8–9 · REQ-07, REQ-08, REQ-09, REQ-18, REQ-19 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-04 · A05 · UI-19 · A06 |
| Reglas y decisiones | RN-04, RN-05, RN-07 · DEC-06 (sólo parte de vigencia) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`: área admin; formularios con React Hook Form + Zod; tablas con TanStack Table. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-03 reglas y configuración de vigencia (de F2-BE-01/03). · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F2-BE-01 - Reglas de puntos por marca y evento\|F2-BE-01]]; [[05-Desarrollo/Lotes/F2-BE-03 - Vencimiento por marca y auditoria\|F2-BE-03]] para vigencia. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-RULE, T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real); recorrido integrado parcial (F2-T08)** · 2026-10-03 |

## Aceptación

- [ ] Sin campo condición; vista previa «otorga 1 punto / N puntos».
- [ ] La UI explica que los cambios sólo afectan eventos futuros.
- [ ] Errores 409/422 del BE se muestran junto al campo correspondiente.
- [ ] Estados de carga, vacío, error, sin permiso y éxito; confirmación en acciones irreversibles.
- [ ] Escritorio, tablet y móvil sin scroll horizontal de página; teclado, foco visible, contraste y textos accesibles.
- [ ] Cotejo con la referencia asignada y con [[02-Arquitectura/Guia visual y criterios anti slop]]; los valores del mockup no se copian como datos.
- [ ] Todo dato mostrado proviene de la respuesta del BE; ninguna regla sensible se calcula en el navegador.
- [ ] Admin sin mockup móvil: diseñar y verificar tablet/móvil según SRC-02 p. 8 (navegación compacta, formularios de una columna, tablas legibles o scroll justificado).
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
