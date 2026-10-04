---
title: "Contrato API v0 — F0"
tags: [zontes, arquitectura, contrato, fase-0]
status: v1-identidad-implementada
updated: 2026-10-03
---

# Contrato API v0 — F0

Contrato HTTP inicial entre `FidelizacionFronted` (Next.js) y `FidelizacionBackend` (Express), salida de F0-I-02. Distingue tres niveles: **implementado y probado** (§1–§4), **propuesto para F1** (§5, no aprobado por Usuario) y **dependiente de decisión** (§6). Base: SRC-02 pp. 11–15, SRC-03 pp. 11–13, [[02-Arquitectura/Base tecnica documentada]], [[02-Arquitectura/Contratos de integracion por flujo]]. Rutas y evidencia: [[05-Desarrollo/Entorno local]], [[05-Desarrollo/Testing]].

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

## 5. I-01 / I-02 v1 — aprobado por Usuario e implementado (2026-10-03)

Aprobado como v1 el 2026-10-03 e implementado en F1 con dobles de prueba; la integración contra el proyecto Firebase de desarrollo está pendiente (DEC-02). Evidencia: [[05-Desarrollo/Testing]] «Corridas F1».

| Flujo | Endpoint | Respuesta | Errores |
| --- | --- | --- | --- |
| I-01 sesión | `GET /api/v1/me` (Bearer) | 200 `{ uid, rol: "cliente"\|"administrador", activo, marcas: ("zontes"\|"kiden"\|"niu")[], vinculo: "vinculado"\|"no_vinculado" }`, `Cache-Control: no-store` | 401 `UNAUTHENTICATED` (ausente, malformado, expirado, revocado, usuario deshabilitado) · 403 `REGISTRATION_REQUIRED` (usuario de Firebase sin perfil) · 403 `FORBIDDEN` (perfil inactivo) · 503 `AUTH_NOT_CONFIGURED` · 500 si Firebase falla (no se disfraza de 401) |
| I-01 rol | `requireRole("administrador")` para futuras rutas `/api/v1/admin/*` | — | 403 `FORBIDDEN` |
| I-02 registro/vínculo | `POST /api/v1/clientes/registro` (Bearer del usuario recién creado; **sin cuerpo**, el correo sale del token) | 201 `{ vinculo, marcas }` | 401 · 403 `EMAIL_NOT_VERIFIED` · 422 `VALIDATION_ERROR` (cuenta sin correo) · 409 `ALREADY_REGISTERED` · 409 `EMAIL_ALREADY_LINKED` |

**Añadidos al implementar, confirmados por Usuario el 2026-10-03 (ADR-11):** los códigos `REGISTRATION_REQUIRED` y `ALREADY_REGISTERED`, y la **exigencia de correo verificado** antes del vínculo (`EMAIL_NOT_VERIFIED`). Sin ella, cualquiera podría registrarse con el correo de otro cliente y heredar sus marcas y puntos; es una medida de seguridad, no un cambio de alcance, pero modifica el flujo de registro (paso de verificación por enlace).

**Normalización:** `trim` + minúsculas; único criterio de vínculo (ADR-04).

**Modelo Firestore (DEC-03):** `usuarios/{uid}` → `{ correo, rol, activo, marcas, vinculo, creadoEn }`; `correos/{sha256(correo)}` → `{ uid }` (unicidad sin usar el correo como ID); `auditoria/{auto}` → `{ accion, actor, objetivoUid, en, datos }` sin correos ni tokens. Registro y bootstrap escriben los tres documentos en una transacción. `FIRESTORE_PREFIX` aísla colecciones de prueba.

**Fuente legacy (DEC-04):** interfaz `FuenteLegacy.buscarPorCorreo` con doble sintético de dominio `ejemplo.test`: `cliente.zontes@` → Zontes; `cliente.kiden.niu@` → Kiden y NIU; `cliente.multimarca@` → las tres.
## 6. Dependencias abiertas

DEC-02 (proyecto Firebase y custodio), DEC-03 (administrador inicial), DEC-04 (contrato legacy), DEC-06 (zona horaria y vencimiento). Hasta resolverlas, §5 no se implementa como definitivo. Contratos I-03–I-09 se detallan al abrir su fase.

## 7. I-03 / I-04 — motor de puntos, implementado en F2 (2026-10-03)

Implementado según DEC-05/06/14; evidencia en [[05-Desarrollo/Testing]] «Corridas F2». Todas las fechas en ISO 8601 UTC; el vencimiento se calcula en America/La_Paz a fin de día.

| Actor | Endpoint | Respuesta | Errores |
| --- | --- | --- | --- |
| Cliente | `GET /me/saldo` | `{ total, marcas: [{ marca, disponible, proximoVencimiento: { fecha, puntos } \| null }] }` sólo de marcas vinculadas; vence lo caducado antes de responder | 401, 403 (no cliente) |
| Cliente | `GET /me/movimientos?marca&tipo&limite(1–100)&cursor` | `{ items: [{ id, marca, tipo, puntos (con signo), fecha, venceEn, evento, motivo }], siguiente }` del más reciente al más antiguo | 403 marca no vinculada, 422 |
| Admin | `GET/POST /admin/reglas`, `PATCH/DELETE /admin/reglas/{marca}__{evento}` | regla `{ id, marca, evento, puntos, activa, creadoEn, actualizadoEn, actualizadoPor }`; sin campo condición (cuerpo estricto) | 409 `RULE_EXISTS`, 404, 422 (negativos, decimales, campos extra) |
| Admin | `GET /admin/vigencias`, `PUT /admin/vigencias/{marca}`, `GET …/{marca}/historial` | `{ marca, activa, cantidad, unidad: dias\|meses\|anios }`; historial `{ en, actor, antes, despues }` | 422 (más de 10 años) |
| Admin | `POST /admin/eventos` `{ idExterno, evento, marca, correoCliente }` | 201 `{ resultado: otorgado, puntos, movimientoId, venceEn }` o `{ resultado: sin_puntos, motivo: sin_regla\|regla_inactiva }`; 200 con `repetido: true` al reintentar | 409 `IDEMPOTENCY_CONFLICT`, 422 `CLIENT_NOT_FOUND`/`CLIENT_INACTIVE`/`BRAND_NOT_LINKED` |
| Admin | `POST /admin/ajustes` `{ idExterno, marca, correoCliente, puntos (≠0), motivo (5–300) }` | 201 `{ movimientoId, puntos, disponible, repetido }` | 409 `INSUFFICIENT_BALANCE`, 409 `IDEMPOTENCY_CONFLICT`, 422 |
| Admin | `POST /admin/vencimientos/procesar` | `{ lotesVencidos, cuentas }`; reejecutable | — |
| Sistema externo | `POST /integracion/eventos` con `X-Api-Key` | igual que `/admin/eventos`; origen `api:{sistema}` | 401 clave ausente/inválida, 503 sin claves configuradas |

**Modelo Firestore F2 (sin índices compuestos):** `reglas/{marca}__{evento}`, `vigencias/{marca}`, `eventos/{sha256(origen|idExterno)}` (idempotencia), `usuarios/{uid}/marcas/{marca}` (saldo materializado), `…/movimientos/{id}` (id con la fecha invertida para que el orden ascendente sea del más reciente al más antiguo), `…/lotes/{id}`, `vencimientos/{uid}__{marca}__{lote}` (pendientes), `auditoria`. Los ids invertidos se adoptaron tras comprobar contra Firestore real que ordenar por id de forma descendente exige un índice adicional.

## 8. I-05 — catálogo y canje, implementado en F3 (2026-10-03)

Implementado según DEC-07 y ADR-13; evidencia en [[05-Desarrollo/Testing]] «Corridas F3». Fechas ISO 8601 UTC; la vigencia del cupón termina a fin de día en America/La_Paz.

| Actor | Endpoint | Respuesta | Errores |
| --- | --- | --- | --- |
| Cliente | `GET /catalogo?marca&categoria&q` | `{ items: [{ id, marca, nombre, descripcion, categoria, puntos, caracteristicas, disponibleDesde, vigenciaCuponDias, disponibilidad, variantes: [{ id, nombre, disponibilidad }] }] }` sólo activos de marcas vinculadas; búsqueda sin tildes; **no expone stock** | 403 marca no vinculada, 422 |
| Cliente | `GET /catalogo/{id}` | un beneficio con la misma forma | 404 si no existe, está inactivo o es de marca no vinculada |
| Cliente | `POST /canjes` `{ beneficioId, varianteId, idSolicitud }` | 201 `{ canje, disponible, repetido: false }`; 200 con `repetido: true` al reintentar el mismo `idSolicitud` | 404, 422 `NOT_AVAILABLE_YET`, 409 `OUT_OF_STOCK`, 409 `INSUFFICIENT_BALANCE`, 409 `IDEMPOTENCY_CONFLICT` |
| Cliente | `GET /me/canjes?marca&limite(1–100)&cursor` | `{ items: [canje], siguiente }` del más reciente al más antiguo | 422 |
| Cliente | `GET /me/canjes/{codigo}`, `…/comprobante` (PDF), `…/qr.svg` | canje `{ codigo, beneficioId, beneficioNombre, marca, varianteNombre, puntos, estado, emitidoEn, venceEn, entregadoEn, anuladoEn, motivoAnulacion }` | 404 si el canje es de otro cliente (no revela que existe) |
| Admin | `GET/POST /admin/beneficios`, `PUT /admin/beneficios/{id}` | beneficio completo con `activo`, stock por variante (`null` = sin límite) y `actualizadoEn/Por`; cuerpo estricto | 409 `ALREADY_EXISTS`, 404, 422 |
| Admin | `GET /admin/canjes/{codigo}` | canje | 404 |
| Admin | `POST /admin/canjes/{codigo}/entregar` | canje en `entregado` | 409 `INVALID_STATE` (no emitido o ya vencido) |
| Admin | `POST /admin/canjes/{codigo}/anular` `{ motivo (5–300) }` | `{ canje, disponible }`; devuelve puntos y una unidad de stock | 409 `INVALID_STATE` (entregado o anulado), 422 |

**Estados:** `emitido` → `entregado` (admin) · `emitido`/`vencido` → `anulado` (admin, con motivo, auditado). `vencido` no se guarda: se deriva al leer cuando `venceEn` pasó sin entrega. **Disponibilidad:** `agotado` (stock 0), `ultimas` (≤ 5), `proximamente` (antes de `disponibleDesde`), `disponible`; el beneficio está `agotado` si todas sus variantes lo están, `disponible` si alguna lo está y, si no, `ultimas`.

**Modelo Firestore F3 (sin índices compuestos):** `beneficios/{id}`, `usuarios/{uid}/canjes/{idInvertido}`, `codigos/{codigo}` → `{ uid, canjeId }` (unicidad y búsqueda por código), movimiento `canje` (−puntos) y, al anular, otro movimiento `canje` (+puntos, motivo «Anulación del canje …») con la reposición de los lotes consumidos; las porciones ya caducadas vuelven a vencer de inmediato. La carga inicial usa `npm run catalogo:cargar -- --archivo <ruta.json>` (ejemplo sintético en `datos/catalogo.ejemplo.json`) (crea los nuevos, no pisa los existentes).

## 9. I-06 — gestión de identidades, implementado en F4 (2026-10-03)

Implementado según DEC-03 (alta por invitación), DEC-04 (cambio de correo) y DEC-08 (edición y baja); evidencia en [[05-Desarrollo/Testing]] «Corridas F4». Todas las rutas `/admin/*` exigen rol administrador activo; un cliente recibe 403.

| Actor | Endpoint | Respuesta | Errores |
| --- | --- | --- | --- |
| Cualquiera autenticado | `PATCH /me` `{ nombre (2–80) }` | 204; cambia el nombre en Firebase Auth y audita `perfil.actualizado` | 422 (otros campos) |
| Admin | `GET /admin/administradores` | `{ items: [{ uid, nombre, correo, activo, creadoEn, ultimoAcceso, invitacionPendiente }] }` sin eliminados | — |
| Admin | `POST /admin/administradores` `{ nombre, apellido, correo }` | 201 administrador; cuenta de Auth sin contraseña. El navegador pide luego a Firebase el correo para definirla | 409 `EMAIL_IN_USE` (correo de cliente o de una cuenta de Auth sin perfil), 422 |
| Admin | `PATCH /admin/administradores/{uid}` `{ nombre?, activo? }` | administrador | 409 `SELF_ACTION` (desactivarse), 409 `LAST_ADMIN`, 404, 422 (correo u otros campos) |
| Admin | `DELETE /admin/administradores/{uid}` | 204; perfil anonimizado, correo liberado, cuenta de Auth borrada | 409 `SELF_ACTION`, 409 `LAST_ADMIN`, 404 |
| Admin | `GET /admin/clientes?correo&marca&activo&vinculo&limite(1–100)&cursor` | `{ items: [{ uid, nombre, correo, marcas, vinculo, activo, puntos, creadoEn, ultimoAcceso, verificacionPendiente }], siguiente }`; `correo` busca coincidencia exacta normalizada; `puntos` = saldo de marcas vinculadas | 422 |
| Admin | `GET /admin/clientes/{uid}` | cliente + `saldos: [{ marca, disponible, vinculada }]` + `historial` (auditoría de la persona, más reciente primero, con nombre del actor) | 404 (no existe, eliminado o es admin) |
| Admin | `PATCH /admin/clientes/{uid}` `{ nombre?, correo?, activo? }` | detalle; al cambiar el correo: vínculo recalculado sólo con el correo nuevo, `verificacionPendiente: true`, sesiones revocadas | 409 `EMAIL_IN_USE`, 404, 422 |
| Admin | `DELETE /admin/clientes/{uid}` | 204; baja + anonimización (DEC-08) | 404 |
| Admin | `GET /admin/auditoria?objetivo={uid}` | `{ items: historial }` | 422 |

**Tras un cambio de correo**, toda ruta protegida responde 403 `EMAIL_NOT_VERIFIED` hasta que el token del cliente traiga el correo verificado; el FE lleva a `/verificar-correo`.

**Modelo Firestore F4 (sin índices compuestos):** los perfiles se leen y escriben por el mismo almacén transaccional que puntos y canjes (`usuarios/{uid}`, `correos/{sha256}`, `auditoria/{id}`). Campos nuevos del perfil: `verificarCorreo: true` y `eliminado: true`. La protección del último administrador lee dentro de la transacción la consulta de administradores activos; Firestore bloquea esos documentos y una desactivación cruzada simultánea se reintenta y se rechaza (verificado contra el proyecto real). El filtro por marca usa `array-contains` combinado con igualdades y orden por id, sin índice adicional (verificado contra el proyecto real). Nombre y último acceso se leen de Firebase Auth.

## 10. I-07 — reportes, movimientos y exportación, implementado en F5 (2026-10-03)

Implementado según DEC-09 y ADR-15; evidencia en [[05-Desarrollo/Testing]] «Corridas F5». Sólo administradores (cliente → 403). Periodos `desde`/`hasta` como fechas locales de Bolivia AAAA-MM-DD, ambos incluidos, máximo 12 meses (`422 RANGE_TOO_LARGE`). Todas las respuestas llevan `Cache-Control: no-store`.

| Endpoint | Respuesta | Notas |
| --- | --- | --- |
| `GET /admin/reportes/resumen` | clientes vigentes (total, vinculados, sin vincular, por marca, nuevos en 30 días), puntos otorgados, utilizados (+vencidos), canjes (+pendientes de entrega) de los últimos 30 días con `variacion { absoluta, porcentaje\|null }` frente a los 30 anteriores; series mensuales de 6 meses; últimos registros y canjes | A13 |
| `GET /admin/reportes/actividad?desde&hasta&marca` | usuarios con actividad, nuevos registros, puntos generados/utilizados (neto de anulaciones)/vencidos, ajustes ±, canjes y anulados, actividades registradas, `porEvento [{ evento, movimientos, puntos, clientes }]` | A10 |
| `GET /admin/reportes/tendencias?metrica(otorgados\|utilizados\|canjes\|registros)&desde&hasta&marca` | `actual` y `anterior` (igual duración) con `serie [{ desde, valor }]` diaria ≤31 días, semanal ≤6 meses, mensual más allá; `variacion`; `porMarca` siempre de las tres | A11 |
| `GET /admin/reportes/canjes?desde&hasta&marca&estado&correo&limite&cursor` | totales, válidos, anulados, puntos, clientes, `beneficiosMasCanjeados`, `porMarca`, `items` con cliente y estado efectivo | A08; `correo` exacto |
| `GET /admin/movimientos?desde&hasta&marca&tipo&evento&limite&cursor` | `{ items: [{ id, fecha, cliente { nombre, correo }, marca, tipo, evento, puntos, motivo }], siguiente }` del más reciente al más antiguo | A07; un cliente eliminado aparece como «Cliente eliminado» sin correo |
| `GET /admin/exportaciones/{clientes\|movimientos\|canjes\|actividad}/vista-previa?…` | `{ filas, columnas, maximo: 10000 }` | A12 |
| `GET /admin/exportaciones/{tipo}?formato(csv\|xlsx)&…` | archivo adjunto; CSV UTF-8 con BOM, separador `;`, CRLF y textos que empiezan con `= + - @` neutralizados; `.xlsx` con encabezado | `422 TOO_MANY_ROWS` sobre 10.000 filas; audita `exportacion.generada` con formato, filas y filtros (sin correos) |

**Modelo Firestore F5 (sin índices compuestos):** `libro/{id del movimiento}` — copia global de cada movimiento (uid, marca, tipo, puntos, fecha, evento, origen, motivo, actor) escrita en la misma transacción que el movimiento del cliente; `codigos/{codigo}` amplía el índice con marca, beneficio, puntos, estado y fechas, actualizado al canjear, entregar y anular. Los reportes leen rangos de un único campo (`libro.fecha`, `codigos.emitidoEn`, `usuarios.creadoEn`) y filtran el resto en memoria con tope de 50.000 documentos; los totales de clientes usan la agregación `count()`. `npm run reportes:conciliar [-- --reparar]` compara el libro y el índice con los datos de cada cliente y completa lo que falte (datos anteriores a F5); nunca borra.

## 11. I-08 — contenido por marca, implementado en F6 (2026-10-03)

Implementado según DEC-10; evidencia en [[05-Desarrollo/Testing]] «Corridas F6». Respuestas de lectura con `Cache-Control: no-store`. Sin archivos: la imagen es una ilustración por marca generada en el FE (DEC-10/11); Storage queda para cuando haya activos autorizados.

| Endpoint | Rol | Cuerpo / respuesta | Notas |
| --- | --- | --- | --- |
| `GET /contenidos?marca&destacadas&limite(1–50, 20)` | cliente | `{ items: [{ id, marca, categoria, titulo, texto, enlace, destacada, publicarDesde }] }` | Sólo activas, dentro de su ventana y de marcas vinculadas; `marca` no vinculada → `403 FORBIDDEN` |
| `GET /admin/contenidos?marca` | admin | `{ items: [Publicacion + { estado: programada\|publicada\|finalizada, visible }] }` | `visible` = activa y dentro de la ventana hoy |
| `POST /admin/contenidos` | admin | `{ marca, categoria(noticia\|evento\|promocion), titulo(3–90), texto(≤600), enlace(https\|null), destacada, activa, publicarDesde, publicarHasta }` estricto → `201` | Fechas AAAA-MM-DD en hora de Bolivia, ambas incluidas; `hasta` anterior a `desde` → 422 |
| `PUT /admin/contenidos/{id}` | admin | mismo cuerpo → publicación | Audita sólo los campos cambiados |
| `PATCH /admin/contenidos/{id}` | admin | `{ activa }` estricto | Interruptor de la lista |
| `DELETE /admin/contenidos/{id}` | admin | `204` | Inexistente → 404 |

**Modelo Firestore F6:** `contenidos/{id}` con los campos del cuerpo más `creadoEn`, `actualizadoEn` y `actualizadoPor` (uid). Lecturas por igualdad de `marca` (una por marca vinculada del cliente) o de la colección completa en el panel, sin índices compuestos; ventana, destacadas, orden (más recientes primero) y límite se aplican en memoria. Auditoría: `contenido.creado`, `contenido.actualizado` (con `campos`) y `contenido.eliminado`, sin correos.


## 12. Operación transversal — implementado en F7 (2026-10-03)

Según DEC-13; evidencia en [[05-Desarrollo/Testing]] «Corridas F7». Referencia completa de los 52 endpoints y colección Postman en `FidelizacionBackend/docs/` (la prueba `src/docs/postman.test.ts` exige que coincidan con las rutas de Express).

| Aspecto | Regla |
| --- | --- |
| Límite de peticiones | 300 por minuto e IP en `/api/v1` (`LIMITE_POR_MINUTO`); `POST /clientes/registro` 20 cada 15 min por IP. Exceso → `429 RATE_LIMITED` con `Retry-After`, aplicado después de CORS. En memoria de la instancia |
| IP real | `TRUST_PROXY` = saltos de proxy de confianza (Render: 1) |
| `Server-Timing` | Fases `token`, `perfil` y `total` (ms) en cada respuesta; `Timing-Allow-Origin` = orígenes CORS |
| Registro | Una línea JSON por petición `{ nivel, momento, requestId, metodo, ruta, estado, ms, rol? }` sin consulta, cuerpo, token ni correo; salud correcta omitida |
| Autenticación | El perfil se lee en paralelo con la verificación del token y sólo se usa si el uid verificado coincide; peticiones simultáneas con el mismo token comparten una verificación (con revocación) en curso, sin guardar resultados (ADR-16) |
| FE | `GET /me` espera hasta 75 s (backend gratuito suspendido) y avisa a los 5 s; la pantalla de acceso llama a `/health` para despertarlo; un 5xx muestra «(referencia xxxxxxxx)» con el inicio del `requestId` |
| Cabeceras FE | `X-Frame-Options: DENY`, `X-Content-Type-Options: nosniff`, `Referrer-Policy: strict-origin-when-cross-origin`, `Permissions-Policy` restrictiva |
| Firestore | `firestore.rules` deniega todo acceso directo; sólo el Admin SDK del BE accede |
