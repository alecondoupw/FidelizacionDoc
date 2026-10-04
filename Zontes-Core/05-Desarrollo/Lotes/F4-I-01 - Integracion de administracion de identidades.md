---
title: "F4-I-01 — Integracion de administracion de identidades"
tags: [zontes, lote, f4, integracion]
status: verificado-con-recorrido-parcial
fase: F4
frente: Integración
bloqueos: []
updated: 2026-10-03
---

# F4-I-01 — Integracion de administracion de identidades

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Verificado con dobles y contra Firestore real (rol, último activo, acciones prohibidas, auditoría); falta el recorrido FE↔BE en navegador por Usuario con Firebase Auth real. Evidencia en [[05-Desarrollo/Testing]] «Corridas F4». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F4-I-01 · F4 — Administración de identidades · Integración · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Probar FE↔BE que un cliente nunca se promueve, que el último admin activo está protegido y que las acciones prohibidas se rechazan en el servidor. |
| Fuente y página | SRC-02 pp. 1–3 · REQ-13, REQ-14 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-06, UI-07, UI-18, UI-22 |
| Reglas y decisiones | RN-01–RN-03 · DEC-03, DEC-08 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Integrador único. FE_REPO `FidelizacionFronted` y BE_REPO `FidelizacionBackend`. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-06 aprobado y versionado. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F4-BE-01 - Gestion de administradores y ultimo activo\|F4-BE-01]]/02/03, [[05-Desarrollo/Lotes/F4-FE-01 - Administradores admin\|F4-FE-01]]/02/03. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-ROLE, T-LINK, T-AUTHZ · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real; Auth con doble); recorrido integrado parcial (F4-T07)** · 2026-10-03 |

## Aceptación

- [ ] Petición directa a la API con rol cliente → 403 en toda ruta admin.
- [ ] Auditoría completa de cada acción probada.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
