---
title: "F5-FE-03 — Exportacion admin"
tags: [zontes, lote, f5, frontend]
status: bloqueado-por-decision
fase: F5
frente: FE
bloqueos: [DEC-09]
updated: 2026-10-03
---

# F5-FE-03 — Exportacion admin

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F5-FE-03 · F5 — Observabilidad de negocio · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | El admin elige filtros y formato, lanza la exportación y ve su estado, error o descarga. |
| Fuente y página | SRC-02 pp. 6–7 · REQ-16 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-11 · A12 |
| Reglas y decisiones | RN-11 · DEC-09 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`: área admin. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-07 exportación (F5-BE-02). · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F5-BE-02 - Exportacion autorizada\|F5-BE-02]]. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-EXPORT, T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado por decisión: DEC-09** · 2026-10-03 |

## Aceptación

- [ ] Sólo formatos aprobados en DEC-09.
- [ ] Estados de carga, vacío, error, sin permiso y éxito; confirmación en acciones irreversibles.
- [ ] Escritorio, tablet y móvil sin scroll horizontal de página; teclado, foco visible, contraste y textos accesibles.
- [ ] Cotejo con la referencia asignada y con [[02-Arquitectura/Guia visual y criterios anti slop]]; los valores del mockup no se copian como datos.
- [ ] Todo dato mostrado proviene de la respuesta del BE; ninguna regla sensible se calcula en el navegador.
- [ ] Admin sin mockup móvil: diseñar y verificar tablet/móvil según SRC-02 p. 8 (navegación compacta, formularios de una columna, tablas legibles o scroll justificado).
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
