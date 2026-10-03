---
title: "F4-FE-03 — Edicion de perfil permitida"
tags: [zontes, lote, f4, frontend]
status: bloqueado-por-decision
fase: F4
frente: FE
bloqueos: [DEC-08]
updated: 2026-10-03
---

# F4-FE-03 — Edicion de perfil permitida

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F4-FE-03 · F4 — Administración de identidades · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Cliente y admin editan sólo los campos que DEC-08 permita, con contraseña y preferencias según contrato. |
| Fuente y página | SRC-03 pp. 8–9; SRC-02 pp. 1–3 · REQ-06, REQ-14 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-18 · C03 · UI-22 · A04 |
| Reglas y decisiones | **DEC-08 abierta** · DEC-03 (contraseña admin) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`: vistas de perfil. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | Mutaciones de perfil a definir con DEC-08. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F1-FE-03 - Mi perfil cliente y admin en consulta\|F1-FE-03]]; [[05-Desarrollo/Lotes/F4-BE-02 - Gestion de clientes y revinculacion\|F4-BE-02]]; DEC-08. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-AUTHZ, T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado por decisión: DEC-08** · 2026-10-03 |

## Aceptación

- [ ] Sólo se ofrecen campos con contrato de edición.
- [ ] Estados de carga, vacío, error, sin permiso y éxito; confirmación en acciones irreversibles.
- [ ] Escritorio, tablet y móvil sin scroll horizontal de página; teclado, foco visible, contraste y textos accesibles.
- [ ] Cotejo con la referencia asignada y con [[02-Arquitectura/Guia visual y criterios anti slop]]; los valores del mockup no se copian como datos.
- [ ] Todo dato mostrado proviene de la respuesta del BE; ninguna regla sensible se calcula en el navegador.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
