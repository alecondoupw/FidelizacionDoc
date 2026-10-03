---
title: "Contrato API v0 — F0"
tags: [zontes, arquitectura, contrato, fase-0]
status: v1-identidad-implementada
updated: 2026-10-03
---

# Contrato API v0 — F0

Contrato HTTP inicial entre `FidelizacionFronted` (Next.js) y `FidelizacionBackend` (Express), salida de F0-I-02. Distingue tres niveles: **implementado y probado** (§1–§4), **propuesto para F1** (§5, no aprobado por Paulo) y **dependiente de decisión** (§6). Base: SRC-02 pp. 11–15, SRC-03 pp. 11–13, [[02-Arquitectura/Base tecnica documentada]], [[02-Arquitectura/Contratos de integracion por flujo]]. Rutas y evidencia: [[05-Desarrollo/Entorno local]], [[05-Desarrollo/Testing]].

## 1. Convenciones transversales — implementado

| Aspecto | Regla v0 | Dónde vive |
| --- | --- | --- |
| Transporte | HTTP/JSON; prefijo versionado `/api/v1` | BE `src/app.ts` · FE `src/lib/api/contract.ts` |
| Cliente HTTP | `fetch` nativo como único estándar (ADR-08); Axios prohibido por ESLint en ambos repos | FE `src/lib/api/client.ts` |
| Autenticación | `Authorization: Bearer <Firebase ID token>`; sin cookies (`credentials: "omit"`, CORS sin credenciales) | FE `client.ts` · BE `src/auth/authorization.ts` |
| CORS | Lista explícita `CORS_ALLOWED_ORIGINS`; métodos GET/POST/PUT/PATCH/DELETE; cabeceras `Content-Type`, `Authorization`, `X-Request-Id`; expone `X-Request-Id` | BE `src/app.ts` |
| Correlación | `X-Request-Id` en toda respuesta; se respeta el entrante sólo si cumple `^[A-Za-z0-9._-]{8,64}$` | BE `src/http/request-id.ts` |
| Fechas | ISO 8601 en **UTC** (`...Z`) en la API; la zona de presentación y el cálculo de vencimiento quedan para DEC-06 | BE `routes/health.ts` |
| Cuerpo | JSON ≤ 100 kB | BE `src/app.ts` |
| Compartición de esquemas | Duplicada a propósito en FE y BE con esta nota como fuente; cambio = actualizar nota + pruebas de ambos lados | — |

## 2. Sobre de error — implementado

```json
{ "error": { "code": "NOT_FOUND", "message": "Ruta no encontrada.", "requestId": "…", "details": "opcional" } }
```

`message` es apto para mostrar y nunca incluye trazas, tokens ni datos personales. 5xx se registra en el servidor con su `requestId`.

| HTTP | `code` | Uso en v0 |
| --- | --- | --- |
| 400 | `INVALID_JSON` · `BAD_REQUEST` · `VALIDATION_ERROR` | JSON mal formado; validación Zod desde F1 |
| 401 | `UNAUTHENTICATED` | Falta token o no es `Bearer` |
| 403 | `FORBIDDEN` | Rol, estado, propietario o marca insuficientes (F1+) |
| 404 | `NOT_FOUND` | Ruta o recurso inexistente |
| 413 | `PAYLOAD_TOO_LARGE` | Cuerpo > 100 kB |
| 415 | `UNSUPPORTED_MEDIA_TYPE` | Codificación no soportada |
| 500 | `INTERNAL_ERROR` | Fallo no controlado, sin detalle |
| 501 | `NOT_IMPLEMENTED` | Frontera de autenticación de F0 con token aún no verificable |
| 503 | `AUTH_NOT_CONFIGURED` | Admin SDK sin proyecto Firebase (DEC-02) |

Errores sólo del cliente FE (`status: 0` o respuesta inválida): `NETWORK_ERROR`, `TIMEOUT` (10 s por defecto), `INVALID_RESPONSE`.

## 3. `GET /api/v1/health` — implementado

Público, sin token ni datos personales, `Cache-Control: no-store`.

```json
{ "status": "ok", "service": "fidelizacion-backend", "version": "0.1.0", "time": "2026-10-03T04:30:31.761Z" }
```

## 4. Frontera de autorización — implementada en modo «falla cerrado»

`requireAuth()` es el único punto donde Express verificará identidad. En F0: sin token → 401; con token → 501, el handler protegido nunca se alcanza. No está montada en rutas de producto. Orden previsto (F1-BE-01): verificar ID token con Admin SDK incluida revocación → cargar perfil (rol, estado) → autorizar rol → autorizar propietario y marca por recurso. El Admin SDK se inicializa de forma perezosa con Application Default Credentials y omite las reglas de Firestore, por eso nada lo invoca sin pasar por esta frontera.

## 5. I-01 / I-02 v1 — aprobado por Paulo e implementado (2026-10-03)

Aprobado como v1 el 2026-10-03 e implementado en F1 con dobles de prueba; la integración contra el proyecto Firebase de desarrollo está pendiente (DEC-02). Evidencia: [[05-Desarrollo/Testing]] «Corridas F1».

| Flujo | Endpoint | Respuesta | Errores |
| --- | --- | --- | --- |
| I-01 sesión | `GET /api/v1/me` (Bearer) | 200 `{ uid, rol: "cliente"\|"administrador", activo, marcas: ("zontes"\|"kiden"\|"niu")[], vinculo: "vinculado"\|"no_vinculado" }`, `Cache-Control: no-store` | 401 `UNAUTHENTICATED` (ausente, malformado, expirado, revocado, usuario deshabilitado) · 403 `REGISTRATION_REQUIRED` (usuario de Firebase sin perfil) · 403 `FORBIDDEN` (perfil inactivo) · 503 `AUTH_NOT_CONFIGURED` · 500 si Firebase falla (no se disfraza de 401) |
| I-01 rol | `requireRole("administrador")` para futuras rutas `/api/v1/admin/*` | — | 403 `FORBIDDEN` |
| I-02 registro/vínculo | `POST /api/v1/clientes/registro` (Bearer del usuario recién creado; **sin cuerpo**, el correo sale del token) | 201 `{ vinculo, marcas }` | 401 · 403 `EMAIL_NOT_VERIFIED` · 422 `VALIDATION_ERROR` (cuenta sin correo) · 409 `ALREADY_REGISTERED` · 409 `EMAIL_ALREADY_LINKED` |

**Añadidos al implementar (precisan la confirmación de Paulo):** los códigos `REGISTRATION_REQUIRED` y `ALREADY_REGISTERED`, y la **exigencia de correo verificado** antes del vínculo (`EMAIL_NOT_VERIFIED`). Sin ella, cualquiera podría registrarse con el correo de otro cliente y heredar sus marcas y puntos; es una medida de seguridad, no un cambio de alcance, pero modifica el flujo de registro (paso de verificación por enlace).

**Normalización:** `trim` + minúsculas; único criterio de vínculo (ADR-04).

**Modelo Firestore (DEC-03):** `usuarios/{uid}` → `{ correo, rol, activo, marcas, vinculo, creadoEn }`; `correos/{sha256(correo)}` → `{ uid }` (unicidad sin usar el correo como ID); `auditoria/{auto}` → `{ accion, actor, objetivoUid, en, datos }` sin correos ni tokens. Registro y bootstrap escriben los tres documentos en una transacción. `FIRESTORE_PREFIX` aísla colecciones de prueba.

**Fuente legacy (DEC-04):** interfaz `FuenteLegacy.buscarPorCorreo` con doble sintético de dominio `ejemplo.test`: `cliente.zontes@` → Zontes; `cliente.kiden.niu@` → Kiden y NIU; `cliente.multimarca@` → las tres.
## 6. Dependencias abiertas

DEC-02 (proyecto Firebase y custodio), DEC-03 (administrador inicial), DEC-04 (contrato legacy), DEC-06 (zona horaria y vencimiento). Hasta resolverlas, §5 no se implementa como definitivo. Contratos I-03–I-09 se detallan al abrir su fase.
