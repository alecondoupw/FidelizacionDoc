---
title: "F4-FE-02 — Clientes admin"
tags: [zontes, lote, f4, frontend]
status: verificado-con-recorrido-parcial
fase: F4
frente: FE
bloqueos: []
updated: 2026-10-03
---

# F4-FE-02 — Clientes admin

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: `/admin/clientes` y `/admin/clientes/[uid]` (UI-07) con filtros, búsqueda exacta, edición con confirmación del cambio de correo, saldos (incluidas marcas desvinculadas), historial y baja confirmada; `/verificar-correo` (UI-27 propuesta). Evidencia en [[05-Desarrollo/Testing]] «Corridas F4». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F4-FE-02 · F4 — Administración de identidades · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Vista de clientes con filtros, detalle, vínculo, edición permitida y estado. |
| Fuente y página | SRC-02 pp. 3, 8–9 · REQ-14, REQ-18 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-07 · A01 |
| Reglas y decisiones | RN-03 · DEC-04, DEC-08 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`: área admin. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-06 (F4-BE-02). · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F4-BE-02 - Gestion de clientes y revinculacion\|F4-BE-02]]. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-LINK, T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real; Auth con doble); recorrido integrado parcial (F4-T07)** · 2026-10-03 |

## Aceptación

- [ ] El estado de vínculo mostrado es el del BE; editar correo avisa de la reevaluación.
- [ ] Estados de carga, vacío, error, sin permiso y éxito; confirmación en acciones irreversibles.
- [ ] Escritorio, tablet y móvil sin scroll horizontal de página; teclado, foco visible, contraste y textos accesibles.
- [ ] Cotejo con la referencia asignada y con [[02-Arquitectura/Guia visual y criterios anti slop]]; los valores del mockup no se copian como datos.
- [ ] Todo dato mostrado proviene de la respuesta del BE; ninguna regla sensible se calcula en el navegador.
- [ ] Admin sin mockup móvil: diseñar y verificar tablet/móvil según SRC-02 p. 8 (navegación compacta, formularios de una columna, tablas legibles o scroll justificado).
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
