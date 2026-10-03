---
title: "F1-FE-03 — Mi perfil cliente y admin en consulta"
tags: [zontes, lote, f1, frontend]
status: verificado-con-salvedades
fase: F1
frente: FE
bloqueos: []
updated: 2026-10-03
---

# F1-FE-03 — Mi perfil cliente y admin en consulta

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: `/perfil` y `/admin/perfil` en modo consulta con cierre de sesión. Edición y cambio de contraseña quedan en F4-FE-03. Evidencia en [[05-Desarrollo/Testing]] «Corridas F1». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F1-FE-03 · F1 — Identidad y vínculo · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Cliente y admin consultan sus datos de identidad y cierran sesión; la edición queda para F4-FE-03 tras contrato. |
| Fuente y página | SRC-03 pp. 8–9; SRC-02 pp. 1–2 · REQ-03, REQ-06 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-18 · C03 · UI-22 · A04 |
| Reglas y decisiones | DEC-08 abierta (campos editables; no bloquea consulta) · DEC-03 (cambio de contraseña admin) · DEC-02 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`: vistas de perfil de ambos roles. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-01 `GET /api/v1/me` (propuesto). · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]], [[05-Desarrollo/Lotes/F1-FE-01 - Login registro y verificacion cliente y login admin\|F1-FE-01]]. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-UI, T-AUTHZ · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Verificado con salvedades (2026-10-03): F1-T01…T11; salvedades: cambio de correo sin probar (política abierta en DEC-04; se cubre en F4-BE-02) y revisión visual de las vistas protegidas en tres tamaños sólo en pruebas de componentes y en el recorrido de Paulo, sin capturas registradas** · 2026-10-03 |

## Aceptación

- [ ] Sólo se muestran campos devueltos por `/me`; ningún control de edición sin contrato.
- [ ] Logout cierra la sesión de Firebase y vuelve al acceso del rol; sesión expirada redirige al login.
- [ ] Estados de carga, vacío, error, sin permiso y éxito; confirmación en acciones irreversibles.
- [ ] Escritorio, tablet y móvil sin scroll horizontal de página; teclado, foco visible, contraste y textos accesibles.
- [ ] Cotejo con la referencia asignada y con [[02-Arquitectura/Guia visual y criterios anti slop]]; los valores del mockup no se copian como datos.
- [ ] Todo dato mostrado proviene de la respuesta del BE; ninguna regla sensible se calcula en el navegador.
- [ ] Admin sin mockup móvil: diseñar y verificar tablet/móvil según SRC-02 p. 8 (navegación compacta, formularios de una columna, tablas legibles o scroll justificado).
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
