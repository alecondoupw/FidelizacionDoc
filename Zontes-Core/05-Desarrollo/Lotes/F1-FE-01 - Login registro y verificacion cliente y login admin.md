---
title: "F1-FE-01 — Login registro y verificacion cliente y login admin"
tags: [zontes, lote, f1, frontend]
status: bloqueado-por-decision
fase: F1
frente: FE
bloqueos: [DEC-02, DEC-04]
updated: 2026-10-03
---

# F1-FE-01 — Login registro y verificacion cliente y login admin

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F1-FE-01 · F1 — Identidad y vínculo · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | El cliente inicia sesión o se registra por pasos con Firebase Auth y ve la verificación con resultado vinculado/no vinculado; el admin entra por su acceso separado; logout y sesión expirada funcionan en ambos. |
| Fuente y página | SRC-02 pp. 1–2; SRC-03 pp. 3–4 · REQ-02, REQ-03, REQ-05, REQ-18 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-01 (sin imagen), UI-02: C10 registro, C09 verificación; login cliente sin imagen |
| Reglas y decisiones | RN-01, RN-03 · **DEC-02 abierta** (proyecto Auth) · **DEC-04 abierta** (mensajes de vínculo y marcas) · DEC-11 identidad final (no bloquea estructura) · DEC-12 prioridad · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`: `src/app/` (segmentos de auth por definir en el lote), `src/lib/firebase`, `src/lib/api` (`getIdToken`). Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-01 `GET /api/v1/me`; I-02 registro (propuestos). Errores según sobre v0. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]], [[05-Desarrollo/Lotes/F1-BE-03 - Normalizacion de correo y vinculo legacy\|F1-BE-03]] para integrar; DEC-02; React Testing Library/jsdom a instalar en el lote. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-UI, T-LINK, T-AUTHZ · componentes (RTL) + `npm run test:integration` contra BE + navegador · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado por decisión: DEC-02, DEC-04** · 2026-10-03 |

## Aceptación

- [ ] Errores de login genéricos: no revelan si una cuenta existe.
- [ ] Se diseña e implementa el caso sin coincidencia, no sólo el éxito de C09.
- [ ] Documento/teléfono son opcionales y no se presentan como criterio de vínculo.
- [ ] Un cliente que navega a rutas admin es redirigido y el BE responde 403.
- [ ] Recuperación de contraseña sólo si Paulo la habilita (opcional en SRC-02 p. 2).
- [ ] Estados de carga, vacío, error, sin permiso y éxito; confirmación en acciones irreversibles.
- [ ] Escritorio, tablet y móvil sin scroll horizontal de página; teclado, foco visible, contraste y textos accesibles.
- [ ] Cotejo con la referencia asignada y con [[02-Arquitectura/Guia visual y criterios anti slop]]; los valores del mockup no se copian como datos.
- [ ] Todo dato mostrado proviene de la respuesta del BE; ninguna regla sensible se calcula en el navegador.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
