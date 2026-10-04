---
title: "F1-BE-01 — Verificacion de token y frontera de autorizacion"
tags: [zontes, lote, f1, backend]
status: verificado-con-salvedades
fase: F1
frente: BE
bloqueos: []
updated: 2026-10-03
---

# F1-BE-01 — Verificacion de token y frontera de autorizacion

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: verificación con Admin SDK y `checkRevoked`, perfil en Firestore, `GET /api/v1/me`, `requireAuth`/`requireRole`. Probado con dobles (F1-T01, F1-T06). Evidencia en [[05-Desarrollo/Testing]] «Corridas F1». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F1-BE-01 · F1 — Identidad y vínculo · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Express verifica el ID token de Firebase (firma, expiración y revocación) con Admin SDK, carga el perfil (rol y estado) y expone `GET /api/v1/me`; `requireAuth` deja de responder 501 y se añade `requireRole`. |
| Fuente y página | SRC-02 pp. 1–2, 11, 14 (obs. 2), 15; SRC-03 p. 12 (obs. 2) · REQ-02, REQ-03, REQ-20 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE). |
| Reglas y decisiones | RN-01, RN-10 · ADR-02, ADR-10 · **DEC-02 abierta** (proyecto Firebase o emulador autorizado) · **DEC-03 abierta** (dónde vive el rol: custom claims o colección `admins`) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`: `src/auth/`, `src/firebase/admin.ts`, `src/routes/` (archivo de `/me`). Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-01 · [[02-Arquitectura/Contrato API v0 - F0]] §4–§5: `Authorization: Bearer`; 401 `UNAUTHENTICATED` (ausente, malformado, expirado, revocado); 403 `FORBIDDEN` (inactivo o rol insuficiente); 503 `AUTH_NOT_CONFIGURED`. Respuesta de `/me` propuesta, a aprobar. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | F0 verificada. DEC-02 y autorización para usar Firebase Auth Emulator (requiere `firebase-tools`, no instalado) o un proyecto de prueba sin datos reales. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-AUTHZ, T-ROLE · unitarias con `verifyIdToken` simulado (Vitest+Supertest) + integración con emulador o proyecto autorizado · `npm run check` · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Verificado con salvedades (2026-10-03): F1-T01…T11; salvedades: cambio de correo sin probar (política abierta en DEC-04; se cubre en F4-BE-02) y revisión visual de las vistas protegidas en tres tamaños sólo en pruebas de componentes y en el recorrido de Usuario, sin capturas registradas** · 2026-10-03 |

## Aceptación

- [ ] Token válido de cliente → 200 con `rol: cliente`; de admin → `rol: administrador`.
- [ ] Token ausente, malformado, expirado o revocado → 401 con sobre de error; nunca alcanza el handler.
- [ ] Usuario desactivado → 403 aunque el token sea válido.
- [ ] Cliente contra ruta con `requireRole("administrador")` → 403, aunque el FE se manipule.
- [ ] Sin `FIREBASE_PROJECT_ID` → 503 sin intentar credenciales.
- [ ] Ningún token ni dato personal en los registros.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
