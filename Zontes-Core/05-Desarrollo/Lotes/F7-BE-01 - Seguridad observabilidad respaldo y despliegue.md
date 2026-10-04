---
title: "F7-BE-01 — Seguridad observabilidad respaldo y despliegue"
tags: [zontes, lote, f7, backend]
status: en-curso
fase: F7
frente: BE
bloqueos: []
updated: 2026-10-03
---

# F7-BE-01 — Seguridad observabilidad respaldo y despliegue

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** DEC-13 resuelta. Implementado: registro JSON por petición, `Server-Timing`, límite de peticiones, `TRUST_PROXY`, `firestore.rules`, respaldo/restauración JSON con simulacro real sin diferencias, `render.yaml` y cron de vencimiento en GitHub Actions; revisión de dependencias. **Falta el despliegue**, que hace Usuario con [[08-Produccion/Manual de despliegue y operacion]]. Evidencia en [[05-Desarrollo/Testing]] «Corridas F7». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F7-BE-01 · F7 — Entrega y operación · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Observabilidad, revisión de seguridad, backup y restauración probados y despliegue en un entorno autorizado. |
| Fuente y página | SRC-01 p. 2; SRC-02 p. 2 · REQ-21, REQ-22 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica. |
| Reglas y decisiones | **DEC-13 abierta** (entorno, backups, integraciones) · DEC-02 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE + Usuario para autorizaciones. BE_REPO `FidelizacionBackend`. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | Todos los aprobados. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | F1–F6; DEC-13. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-DEMO · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado en local; despliegue pendiente de las cuentas de Usuario (F7-T10)** · 2026-10-03 |
## Aceptación

- [x] Restauración probada desde backup. (F7-T06).
- [ ] Despliegue sólo tras autorización expresa.
- [x] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
