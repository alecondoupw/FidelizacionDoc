---
title: "F6-FE-03 — Pulido responsive accesibilidad y marcas"
tags: [zontes, lote, f6, frontend]
status: bloqueado-por-decision
fase: F6
frente: FE
bloqueos: [DEC-11]
updated: 2026-10-03
---

# F6-FE-03 — Pulido responsive accesibilidad y marcas

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F6-FE-03 · F6 — Contenido y calidad visual · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Pulir responsive, foco, copy y diferenciación entre Zontes, Kiden y NIU con la identidad aprobada. |
| Fuente y página | SRC-02 pp. 8–9; SRC-03 pp. 2, 9–10 · REQ-18, REQ-19 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | Todas |
| Reglas y decisiones | ADR-07 · **DEC-11 abierta** · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`: tokens en `src/app/globals.css` y componentes. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | No aplica. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F6-FE-02 - Cotejo visual de cada UI-ID\|F6-FE-02]]; DEC-11. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado por decisión: DEC-11** · 2026-10-03 |

## Aceptación

- [ ] Tokens de identidad final aplicados sin activos no autorizados.
- [ ] Estados de carga, vacío, error, sin permiso y éxito; confirmación en acciones irreversibles.
- [ ] Escritorio, tablet y móvil sin scroll horizontal de página; teclado, foco visible, contraste y textos accesibles.
- [ ] Cotejo con la referencia asignada y con [[02-Arquitectura/Guia visual y criterios anti slop]]; los valores del mockup no se copian como datos.
- [ ] Todo dato mostrado proviene de la respuesta del BE; ninguna regla sensible se calcula en el navegador.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
