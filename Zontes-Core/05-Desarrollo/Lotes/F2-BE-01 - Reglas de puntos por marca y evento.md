---
title: "F2-BE-01 — Reglas de puntos por marca y evento"
tags: [zontes, lote, f2, backend]
status: pendiente
fase: F2
frente: BE
bloqueos: [DEC-02]
updated: 2026-10-03
---

# F2-BE-01 — Reglas de puntos por marca y evento

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F2-BE-01 · F2 — Motor de puntos · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | El admin crea, consulta, filtra, edita, activa/desactiva y elimina reglas evento+marca+puntos+estado; la combinación es única, no existe campo condición y cada cambio queda versionado y auditado. |
| Fuente y página | SRC-02 pp. 3–5, 14 (obs. 5) · REQ-07, REQ-08 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE); consumidor UI-04. |
| Reglas y decisiones | RN-04, RN-05 · ADR-05 · DEC-02 (persistencia Firestore) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`: módulo de reglas con repositorio sobre Firestore. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-03 (admin FE → Express): rutas de reglas bajo `/api/v1/admin/` a fijar en el lote; 409 combinación duplicada, 422 evento o puntos inválidos, 403 no admin. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]] (rol admin); DEC-02. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-RULE, T-HISTORY, T-AUTHZ · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Pendiente: depende de F1-BE-01 y DEC-02** · 2026-10-03 |

## Aceptación

- [ ] Sólo Compra, Referido, Mantenimiento y Asistencia a eventos; otro valor → 422.
- [ ] Puntos enteros positivos; duplicado marca+evento → 409.
- [ ] Editar o eliminar no modifica movimientos ya otorgados.
- [ ] Auditoría con actor, fecha y valores antes/después.
- [ ] Cliente → 403.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
