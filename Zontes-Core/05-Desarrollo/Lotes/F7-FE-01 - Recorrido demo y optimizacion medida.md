---
title: "F7-FE-01 — Recorrido demo y optimizacion medida"
tags: [zontes, lote, f7, frontend]
status: en-curso
fase: F7
frente: FE
bloqueos: []
updated: 2026-10-03
---

# F7-FE-01 — Recorrido demo y optimizacion medida

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Guion reproducible con datos sintéticos en [[07-Manuales/Guion de demostracion]]; rendimiento medido antes y después (Inicio −23 %, `/me` −33 %, F7-T07); espera y aviso para el backend suspendido; cabeceras de seguridad. **Falta ejecutar el guion completo** (T-DEMO) en local o en el despliegue, y repetir la medición en producción. Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F7-FE-01 · F7 — Entrega y operación · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Recorrido demo cliente y admin sin errores, con mejoras de rendimiento medidas, no supuestas. |
| Fuente y página | SRC-01 p. 2 · REQ-22 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | Todas |
| Reglas y decisiones | DEC-12 (hitos), DEC-13 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | Todos los aprobados. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | F1–F6 verificadas. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-DEMO, T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Preparado y medido; T-DEMO pendiente** · 2026-10-03 |
## Aceptación

- [x] Guion de demo reproducible con datos sintéticos.
- [x] Métricas antes/después registradas en el Core. (F7-T07; repetir en producción).
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
