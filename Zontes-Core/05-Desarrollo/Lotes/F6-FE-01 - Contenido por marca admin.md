---
title: "F6-FE-01 — Contenido por marca admin"
tags: [zontes, lote, f6, frontend]
status: verificado
fase: F6
frente: FE
bloqueos: []
updated: 2026-10-03
---

# F6-FE-01 — Contenido por marca admin

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: `/admin/contenido` (UI-12/A09) con pestañas por marca y conteos, búsqueda, filtros de estado y ventana, interruptor, vista previa como la verá el cliente, editor con vista previa en vivo y eliminación confirmada; en el cliente, carrusel de destacadas en Inicio y `/novedades` (UI-28). Evidencia en [[05-Desarrollo/Testing]] «Corridas F6» y [[06-Estado/Evidencias/F6-revision-visual]]. Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F6-FE-01 · F6 — Contenido y calidad visual · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Lista y editor de contenido por marca con estado y vista previa si se decide. |
| Fuente y página | SRC-02 p. 7 · REQ-17 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-12 · A09 |
| Reglas y decisiones | DEC-10 resuelta · DEC-11 parcial · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`: área admin. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-08 implementado: [[02-Arquitectura/Contrato API v0 - F0]] §11. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F6-BE-01 - Contenido por marca\|F6-BE-01]]. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-BRAND, T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (componentes + interfaz real F6-T07/T08 + revisión visual F6-T09)** · 2026-10-03 |
## Aceptación

- [x] Estados de carga, vacío, error, sin permiso y éxito; confirmación en acciones irreversibles.
- [x] Escritorio, tablet y móvil sin scroll horizontal de página; teclado, foco visible, contraste y textos accesibles.
- [x] Cotejo con la referencia asignada y con [[02-Arquitectura/Guia visual y criterios anti slop]]; los valores del mockup no se copian como datos.
- [x] Todo dato mostrado proviene de la respuesta del BE; ninguna regla sensible se calcula en el navegador.
- [x] Admin sin mockup móvil: diseñar y verificar tablet/móvil según SRC-02 p. 8 (navegación compacta, formularios de una columna, tablas legibles o scroll justificado).
- [x] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
