---
title: "F6-FE-03 — Pulido responsive accesibilidad y marcas"
tags: [zontes, lote, f6, frontend]
status: verificado-con-salvedades
fase: F6
frente: FE
bloqueos: [DEC-11]
updated: 2026-10-03
---

# F6-FE-03 — Pulido responsive accesibilidad y marcas

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Pulido con la línea visual provisional (DEC-11 parcial): contraste del interruptor, desbordes, filas y rejillas en tablet, barra móvil y menú «Más», textos coherentes. La identidad final queda para cuando Usuario entregue activos autorizados. Evidencia en [[06-Estado/Evidencias/F6-revision-visual]]. Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F6-FE-03 · F6 — Contenido y calidad visual · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Pulir responsive, foco, copy y diferenciación entre Zontes, Kiden y NIU con la identidad aprobada. |
| Fuente y página | SRC-02 pp. 8–9; SRC-03 pp. 2, 9–10 · REQ-18, REQ-19 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | Todas |
| Reglas y decisiones | ADR-07 · **DEC-11 parcial**: línea provisional · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`: tokens en `src/app/globals.css` y componentes. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | No aplica. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F6-FE-02 - Cotejo visual de cada UI-ID\|F6-FE-02]]; DEC-11. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Verificado con línea provisional; identidad final pendiente de DEC-11** · 2026-10-03 |
## Aceptación

- [ ] Tokens de identidad final aplicados sin activos no autorizados.
- [x] Estados de carga, vacío, error, sin permiso y éxito; confirmación en acciones irreversibles.
- [x] Escritorio, tablet y móvil sin scroll horizontal de página; teclado, foco visible, contraste y textos accesibles.
- [x] Cotejo con la referencia asignada y con [[02-Arquitectura/Guia visual y criterios anti slop]]; los valores del mockup no se copian como datos.
- [x] Todo dato mostrado proviene de la respuesta del BE; ninguna regla sensible se calcula en el navegador.
- [x] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
