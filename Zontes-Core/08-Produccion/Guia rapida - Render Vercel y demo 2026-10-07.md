---
title: "Guia rapida - Render Vercel y demo 2026-10-07"
tags: [zontes, render, vercel, despliegue]
status: preparado-sin-desplegar
updated: 2026-10-07
---

# Guía rápida: Render, frontend y cuentas de demo

## Backend en Render

New → Web Service, repositorio **alecondoupw/FidelizacionBackend**:

| Campo | Valor |
| --- | --- |
| Rama | main |
| Runtime | Node |
| Root Directory | Vacío: repositorio independiente. |
| Build Command | npm ci --include=dev && npm run build |
| Start Command | npm start |
| Health Check Path | /api/v1/health |
| Auto Deploy | Activado para main. |
| Instancia | Plan que elijas; render.yaml incluye Free. |

TypeScript está en devDependencies: --include=dev permite compilar con NODE_ENV=production. [Servicios Express — Render](https://render.com/docs/deploy-node-express-app).

### Variables de Render

| Variable | Valor |
| --- | --- |
| NODE_VERSION | 24 |
| NODE_ENV | production |
| HOST | 0.0.0.0 |
| TRUST_PROXY | 1 |
| FIREBASE_PROJECT_ID | ID del proyecto Firebase de la demo; consulta tu configuración local. |
| GOOGLE_APPLICATION_CREDENTIALS | /etc/secrets/firebase-admin.json |
| CORS_ALLOWED_ORIGINS | https://TU-FRONTEND.vercel.app |
| LEGACY_SOURCE | importacion |
| FIRESTORE_PREFIX | Vacío para colecciones actuales; se puede omitir. |
| LIMITE_POR_MINUTO | 300; opcional, valor predeterminado. |

PORT lo asigna Render. INTEGRACION_CLAVES se omite si no usas integraciones externas. CORS acepta varios orígenes separados por coma, sin ruta ni barra final; puedes añadir http://localhost:3000 para pruebas locales. [Puerto y host — Render](https://render.com/docs/web-services), [Node — Render](https://render.com/docs/node-version).

### Firebase: archivo secreto

Environment → Secret Files → Add Secret File:

1. Filename: firebase-admin.json.
2. Contents: contenido del JSON de cuenta de servicio del proyecto autorizado.
3. Guarda y despliega.

Render lo monta en /etc/secrets/firebase-admin.json. La ruta Windows E:/... no sirve en Render. El JSON nunca se carga al frontend ni se sube a Git. [Archivos secretos — Render](https://render.com/docs/configure-environment-variables).

Prueba con la URL asignada:

```powershell
$backendDemoUrl = "https://TU-BACKEND.onrender.com"
Invoke-RestMethod "$backendDemoUrl/api/v1/health"
```

Después comprueba un ingreso y consulta protegida: la salud del proceso por sí sola no valida Firebase. Para conservar la demo usa el mismo proyecto y prefijo de colecciones.

## Frontend local

Node.js 24 y npm 11. .env.local vive junto a package.json de FidelizacionFronted. Este equipo ya lo tiene configurado.

```powershell
Set-Location "E:\Repositorios\Hackathon\MainRepo\Fidelazacion\FidelizacionFronted"
npm ci
npm run dev
```

En una copia nueva, copia .env.example a .env.local y completa las variables. El backend debe estar arrancado o la URL base debe apuntar a Render.

- Cliente: http://localhost:3000/ingresar.
- Admin: http://localhost:3000/admin/ingresar.

Para ejecutar producción local, libera primero el puerto 3000 del servidor de desarrollo:

```powershell
npm run build
npm start
```

## Variables del frontend / Vercel

```dotenv
NEXT_PUBLIC_API_BASE_URL=https://TU-BACKEND.onrender.com
NEXT_PUBLIC_FIREBASE_API_KEY=TU_CONFIGURACION_WEB_FIREBASE
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=TU_CONFIGURACION_WEB_FIREBASE
NEXT_PUBLIC_FIREBASE_PROJECT_ID=TU_CONFIGURACION_WEB_FIREBASE
NEXT_PUBLIC_FIREBASE_APP_ID=TU_CONFIGURACION_WEB_FIREBASE
```

Obtén las cuatro variables Firebase del .env.local existente o de la configuración web de Firebase. La URL base no lleva /api/v1; en local se usa http://localhost:4000. NEXT_PUBLIC_* se incorpora al build: al cambiar valores, recompila o redespliega.

En Vercel configura framework Next.js, Node 24, Root Directory vacío y estas cinco variables en Production antes de publicar.

```powershell
npx vercel login
npx vercel link
```

Crea o enlaza el proyecto. Una vez cargadas las variables:

```powershell
npx vercel deploy --prod
```

[Publicar con Vercel CLI](https://vercel.com/docs/cli/deploy). Al obtener el dominio, agrégalo a CORS_ALLOWED_ORIGINS en Render y revisa los dominios Firebase para los flujos de autenticación que los requieran.

## Cuentas de prueba

| Rol | Correo | Ruta |
| --- | --- | --- |
| Administrador | adminzontes@test.com | /admin/ingresar |
| Cliente | clientezontes@test.com | /ingresar |

Las contraseñas se entregan a Paulo fuera del repositorio, en CREDENCIALES-PRUEBA.local.md. Las cuentas ya existen en el Firebase de desarrollo; no se crean al instalar dependencias. El cliente genérico comienza sin puntos.

## Instalación móvil

Después de publicar, abre la URL HTTPS desde el celular y toca el icono de descarga. El navegador ofrece la instalación o instrucciones. Safari usa Compartir → Añadir a pantalla de inicio. Pasos y límites en [[07-Manuales/Instalar Zontes en el celular - PWA]].

Esta entrega publica código y documentación en GitHub; el despliegue de Render/Vercel y la instalación física en celular quedan para Paulo.
