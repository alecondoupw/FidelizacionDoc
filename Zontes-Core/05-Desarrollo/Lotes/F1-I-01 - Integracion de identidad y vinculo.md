---
title: "F1-I-01 — Integracion de identidad y vinculo"
tags: [zontes, lote, f1, integracion]
status: bloqueado-por-entorno
fase: F1
frente: Integración
bloqueos: [DEC-02, DEC-03, DEC-04]
updated: 2026-10-03
---

# F1-I-01 — Integracion de identidad y vinculo

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado:** los lotes F1-BE/FE están implementados con dobles; falta el entorno real. Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F1-I-01 · F1 — Identidad y vínculo · Integración · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Demostrar FE↔BE el recorrido registro → vínculo → `/me` → logout con datos sintéticos, y que permisos, duplicados, marcas y cambio de correo se resuelven en el BE. |
| Fuente y página | SRC-02 pp. 1–3, 14–15; SRC-03 pp. 3–4 · REQ-02–REQ-05, REQ-20 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-01, UI-02, UI-17, UI-18, UI-22 |
| Reglas y decisiones | RN-01, RN-03, RN-10 · DEC-02, DEC-03, DEC-04 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Integrador único. FE_REPO `FidelizacionFronted` y BE_REPO `FidelizacionBackend`. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-01 e I-02 aprobados y versionados antes de cerrar. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]]/02/03, [[05-Desarrollo/Lotes/F1-FE-01 - Login registro y verificacion cliente y login admin\|F1-FE-01]]/02/03. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-ROLE, T-LINK, T-AUTHZ · evidencia en [[05-Desarrollo/Testing]] · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado: requiere el proyecto Firebase de desarrollo (DEC-02 resuelta, recurso aún no entregado) y usuarios de prueba creados por Paulo** · 2026-10-03 |

## Aceptación

- [ ] Rol cruzado rechazado por el BE aunque se manipule el FE.
- [ ] Token expirado y revocado rechazados; correo duplicado → 409.
- [ ] Cambio de correo según DEC-04, sin perder historial.
- [ ] Datos sólo sintéticos; ninguno real sin autorización.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
