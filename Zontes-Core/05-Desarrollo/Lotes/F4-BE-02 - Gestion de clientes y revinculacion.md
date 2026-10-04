---
title: "F4-BE-02 — Gestion de clientes y revinculacion"
tags: [zontes, lote, f4, backend]
status: verificado-con-recorrido-parcial
fase: F4
frente: BE
bloqueos: []
updated: 2026-10-03
---

# F4-BE-02 — Gestion de clientes y revinculacion

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: `/admin/clientes` con búsqueda exacta por correo, filtros de marca, estado y vínculo, detalle con saldos e historial, edición de nombre, correo y estado (el correo recalcula el vínculo, exige verificar y revoca sesiones) y baja + anonimización (DEC-04/08). Evidencia en [[05-Desarrollo/Testing]] «Corridas F4». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F4-BE-02 · F4 — Administración de identidades · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Un admin busca y filtra clientes, ve su detalle, edita campos permitidos, reevalúa el vínculo al cambiar el correo, activa/desactiva y elimina sin dejar puntos o canjes inconsistentes. |
| Fuente y página | SRC-02 p. 3 · REQ-14 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE); consumidor UI-07. |
| Reglas y decisiones | RN-03 · **DEC-08 abierta** (campos, borrado, retención) · **DEC-04** (cambio de correo) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`: módulo de clientes. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-06: rutas bajo `/api/v1/admin/clientes` a fijar; paginación y filtros. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F1-BE-03 - Normalizacion de correo y vinculo legacy\|F1-BE-03]]; DEC-04/08. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-LINK, T-HISTORY, T-AUTHZ · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real; Auth con doble); recorrido integrado parcial (F4-T07)** · 2026-10-03 |

## Aceptación

- [ ] Cambio de correo vuelve a evaluar el vínculo sólo por correo normalizado.
- [ ] Eliminar o desactivar conserva el historial auditable según DEC-08.
- [ ] Campos no permitidos → 422/403.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
