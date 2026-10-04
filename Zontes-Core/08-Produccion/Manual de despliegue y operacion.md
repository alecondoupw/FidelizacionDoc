---
title: "Manual de despliegue y operación"
tags: [zontes, produccion, manual, f7]
status: preparado
updated: 2026-10-03
---

# Manual de despliegue y operación

Entregable de SRC-01 p. 2 (REQ-21, REQ-22) según **DEC-13**: frontend en **Vercel** y backend en **Render**, ambos en plan gratuito; vencimiento diario con **GitHub Actions**; respaldo propio en JSON. Paulo crea las cuentas, conecta GitHub y carga los secretos; ningún secreto vive en Git ni en este Core. Estado: **preparado y probado en local; despliegue pendiente de que Paulo cree las cuentas** (ver [[05-Desarrollo/Testing]] «Corridas F7»).

## 1. Arquitectura desplegada

```
Navegador ──► Vercel (Next.js, FidelizacionFronted)
   │  Firebase Auth (SDK cliente: inicio de sesión, verificación de correo)
   └──► Render (Express, FidelizacionBackend) ──► Firebase Admin SDK ──► Auth + Firestore
GitHub Actions (cron diario) ──► npm run puntos:vencer ──► Firestore
```

El navegador nunca toca Firestore: las reglas lo deniegan todo y el backend usa el Admin SDK, que autoriza cada operación en `src/auth`.

## 2. Límites del plan gratuito (aceptados en DEC-13)

| Servicio | Límite | Efecto |
| --- | --- | --- |
| Render Free | Se suspende tras 15 min sin tráfico; 750 h/mes; sin SLA | La primera petición tarda ~1 min. El FE espera hasta 75 s, avisa «Conectando con el servidor…» a los 5 s y despierta el backend al abrir la pantalla de acceso |
| Vercel Hobby | Uso personal y no comercial según sus términos | Válido para el prototipo y la demostración; una operación comercial requiere Vercel Pro |
| GitHub Actions | En repos públicos, los cron se desactivan tras 60 días sin actividad | Revisar la pestaña Actions; se reactivan con un clic |
| Límite de peticiones | En memoria de una instancia | Con varias instancias, cada una cuenta por separado |

## 3. Variables (sólo nombres)

**Backend (Render)** — `render.yaml` fija las no secretas:

| Variable | Valor | Origen |
| --- | --- | --- |
| `NODE_ENV` | `production` | render.yaml |
| `HOST` | `0.0.0.0` | render.yaml |
| `PORT` | la asigna Render | Render |
| `TRUST_PROXY` | `1` | render.yaml |
| `GOOGLE_APPLICATION_CREDENTIALS` | `/etc/secrets/firebase-admin.json` | render.yaml + archivo secreto |
| `FIREBASE_PROJECT_ID` | id del proyecto Firebase | Paulo en Render |
| `CORS_ALLOWED_ORIGINS` | URL de producción de Vercel, sin barra final | Paulo en Render |
| `INTEGRACION_CLAVES` | vacío, o `sistema:sha256` por sistema | Paulo en Render |
| `LIMITE_POR_MINUTO` | opcional (300) | Paulo en Render |

**Frontend (Vercel)** — se insertan al compilar; cambiar una exige volver a desplegar:

| Variable | Valor |
| --- | --- |
| `NEXT_PUBLIC_API_BASE_URL` | URL de Render, sin `/api/v1` ni barra final |
| `NEXT_PUBLIC_FIREBASE_API_KEY`, `NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN`, `NEXT_PUBLIC_FIREBASE_PROJECT_ID`, `NEXT_PUBLIC_FIREBASE_APP_ID` | Los mismos de `.env.local` (configuración web de Firebase; no son secretos) |

**GitHub (repo FidelizacionBackend → Settings → Secrets and variables → Actions):** secretos `FIREBASE_SERVICE_ACCOUNT` (contenido del JSON) y `FIREBASE_PROJECT_ID`; variable `VENCIMIENTO_ACTIVO` = `true`.

## 4. Despliegue paso a paso (lo hace Paulo)

1. **Cuenta de servicio de producción.** Firebase Console → Configuración del proyecto → Cuentas de servicio → «Generar nueva clave privada». Guardar el JSON fuera de cualquier repositorio. Usar una clave distinta de la de desarrollo permite revocarla sin afectar el trabajo local.
2. **Reglas de Firestore.** Firestore Database → Reglas → pegar el contenido de `FidelizacionBackend/firestore.rules` → Publicar. (El 2026-10-03 se comprobó que las lecturas y escrituras anónimas ya reciben 403; falta confirmar con un usuario autenticado, ver F7-T08).
3. **Backend en Render.** New → Blueprint → conectar GitHub y elegir `FidelizacionBackend` (rama `main`). Render lee `render.yaml` y pide `FIREBASE_PROJECT_ID`, `CORS_ALLOWED_ORIGINS` (de momento `http://localhost:3000`) e `INTEGRACION_CLAVES` (puede quedar vacía). Luego, en el servicio → Environment → **Secret Files** → `firebase-admin.json` con el contenido del JSON del paso 1. Esperar el despliegue y abrir `https://<servicio>.onrender.com/api/v1/health` → `{"status":"ok",…}`.
4. **Frontend en Vercel.** Add New → Project → importar `FidelizacionFronted`. Antes de desplegar, cargar las cinco variables de la tabla anterior (Production). Settings → Build and Deployment → Node.js 24.x. Desplegar y anotar la URL de producción.
5. **Cerrar el círculo.** En Render, `CORS_ALLOWED_ORIGINS` = URL de Vercel (Render reinicia el servicio). En Firebase → Authentication → Settings → **Dominios autorizados** → añadir el dominio de Vercel (sin él fallan los correos de verificación y de contraseña que devuelven a la aplicación).
6. **Vencimiento diario.** En GitHub cargar los dos secretos y la variable del §3; en Actions → «Vencimiento de puntos» → «Run workflow» para probarlo una vez (debe terminar en verde e imprimir «Lotes vencidos: N en M cuenta(s)»). Corre a las 00:10 de Bolivia.
7. **Verificación** (la registra el agente en Testing al recibir las URL):
   - `GET /api/v1/health` responde 200 con `X-Request-Id`.
   - Ingreso de admin y de cliente; Dashboard e Inicio con datos.
   - En el navegador, las peticiones a la API muestran `Server-Timing` (fases `token`, `perfil`, `total`).
   - Render → Logs muestra una línea JSON por petición, sin correos ni consultas.
   - Desde otro origen (p. ej. una URL de vista previa de Vercel) la API rechaza CORS.

## 5. Actualizar y volver atrás

- **Actualizar:** un push a `main` despliega solo en ambos servicios (`autoDeploy`). Antes de un cambio que toque datos: respaldo (§6).
- **Volver atrás:** Render → Deploys → «Rollback» al despliegue anterior; Vercel → Deployments → el anterior → «Promote to Production». Un rollback de código no deshace datos: si el cambio escribió datos, restaurar desde el respaldo previo.

## 6. Respaldos y restauración

| Tarea | Cuándo | Comando (en el equipo de Paulo, con `.env` de producción) |
| --- | --- | --- |
| Respaldo | Semanal y antes de cada despliegue que toque datos | `npm run respaldo:exportar -- --salida <carpeta segura>` |
| Simulacro de restauración | Mensual | `npm run respaldo:restaurar -- --archivo <json> --prefijo prueba_restauracion_ --limpiar` |
| Restauración real | Pérdida de datos | En un proyecto o colecciones vacías: `npm run respaldo:restaurar -- --archivo <json> --sobre-proyecto` |

- El JSON contiene **datos personales** (correos, nombres, movimientos): guardarlo cifrado o en un almacenamiento con acceso restringido, nunca en Git ni en este Core. Retención propuesta: 8 semanales y 6 mensuales (pendiente de confirmar).
- La restauración exige colecciones de destino vacías salvo `--permitir-no-vacio`; nunca borra fuera de un prefijo `prueba_*`; al terminar compara el destino con el archivo documento a documento y sale con error si hay diferencias.
- **Límite:** las cuentas de Firebase Auth (contraseñas, verificación) no están en el respaldo. Si se perdiera el proyecto entero, los perfiles restaurados conservan uid y correo, pero cada persona tendría que volver a crear su acceso; exportar Auth requiere `firebase-tools` (`firebase auth:export`), no instalado (pedir autorización si se quiere).
- Simulacro ejecutado el 2026-10-03 sobre el proyecto de desarrollo: 60 documentos, sin diferencias (F7-T06).

## 7. Observabilidad

- **Logs:** Render → Logs. Cada petición escribe `{ nivel, momento, requestId, metodo, ruta, estado, ms, rol? }`; las respuestas de salud correctas no se registran. Los 5xx añaden la traza con el mismo `requestId`, que viaja en la cabecera `X-Request-Id`; el usuario ve sus primeros 8 caracteres como «(referencia xxxxxxxx)» al final del mensaje de error, y basta buscarlos en Render → Logs.
- **Rendimiento:** cabecera `Server-Timing` en cada respuesta (`token`, `perfil`, `total`), visible en las herramientas del navegador.
- **Salud:** Render comprueba `/api/v1/health`; si falla, no promueve el despliegue.
- **Alertas:** el plan gratuito no las incluye; Render envía correo si un despliegue falla, y GitHub si falla el workflow de vencimiento.

## 8. Seguridad en operación

| Situación | Acción |
| --- | --- |
| Se filtra el JSON de la cuenta de servicio | Google Cloud Console → IAM → Cuentas de servicio → borrar esa clave; generar otra y reemplazarla en Render y GitHub |
| Se filtra una clave de integración | Quitar su línea de `INTEGRACION_CLAVES` en Render y generar otra con `npm run integracion:clave` |
| Un administrador ya no debe entrar | Panel → Administradores → desactivar o eliminar (efecto inmediato: el perfil se lee en cada petición) |
| Abuso o tráfico anómalo | El límite responde 429; bajar `LIMITE_POR_MINUTO` si hace falta |
| Vulnerabilidades de dependencias | `npm audit --omit=dev` en cada repo. Aceptadas el 2026-10-03: BE 2 moderadas (`uuid`/`gaxios`, dependencias de Firebase Admin); FE 4 altas de `@grpc/grpc-js` dentro de Firestore cliente, que el FE no importa (ESLint lo prohíbe) y que no llega al bundle del navegador (F7-T09) |

## 9. Integraciones (CRM y facturación)

Documentadas, no conectadas (DEC-13): `POST /api/v1/integracion/eventos` con `X-Api-Key`. Alta de un sistema, idempotencia y ejemplo en `FidelizacionBackend/docs/API.md` §Integración; colección Postman en `docs/postman/`.
