---
title: "F4-BE-01 — Gestion de administradores y ultimo activo"
tags: [zontes, lote, f4, backend]
status: verificado-con-recorrido-parcial
fase: F4
frente: BE
bloqueos: []
updated: 2026-10-03
---

# F4-BE-01 — Gestion de administradores y ultimo activo

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: `/admin/administradores` con alta por invitación (cuenta de Auth sin contraseña), edición de nombre, activación y baja anonimizada; último activo protegido dentro de la transacción (desactivación cruzada simultánea verificada contra Firestore real) y cuenta propia protegida (ADR-14 propuesta). Evidencia en [[05-Desarrollo/Testing]] «Corridas F4». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F4-BE-01 · F4 — Administración de identidades · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Un admin lista, crea, edita lo permitido, activa/desactiva y elimina otros admins; el último admin activo no puede eliminarse ni desactivarse, tampoco por operaciones concurrentes; todo se audita. |
| Fuente y página | SRC-02 pp. 2–3 · REQ-13 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE); consumidor UI-06. |
| Reglas y decisiones | RN-01, RN-02 · ADR-03 · **DEC-03 abierta** (alta: invitación o contraseña inicial) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`: módulo de administradores. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-06: rutas bajo `/api/v1/admin/administradores` a fijar; 409 último activo. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]], [[05-Desarrollo/Lotes/F1-BE-02 - Bootstrap del administrador inicial\|F1-BE-02]]; DEC-03. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-ROLE, T-AUTHZ · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real; Auth con doble); recorrido integrado parcial (F4-T07)** · 2026-10-03 |

## Aceptación

- [ ] Sólo un admin activo crea admins; un cliente nunca se promueve.
- [ ] Dos desactivaciones cruzadas simultáneas no dejan cero admins activos.
- [ ] Auditoría con actor, fecha y hora.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
