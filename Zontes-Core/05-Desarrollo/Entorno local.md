---
title: "Entorno local y repositorios"
tags: [zontes, entorno]
status: verificado-F0
updated: 2026-10-03
---

# Entorno local y repositorios

## Rutas confirmadas por Paulo (DEC-01, 2026-10-03)

Respuesta literal al abrir F0: frontend `…\FidelizacionFronted`; backend `…\FidelizacionBackend`; contenido «Sólo README; inicializar»; Git «Dos repos independientes».

| Frente | Ruta absoluta en este host (Windows) | Repositorio | Revisión F0 |
| --- | --- | --- | --- |
| Core (este baúl) | `C:\Users\aleco\Documents\Fidelizacion\FidelizacionDoc\Zontes-Core` | [FidelizacionDoc](https://github.com/alecondoupw/FidelizacionDoc), rama `main` | commit de documentación F0 sobre `591032d` |
| FE_REPO | `C:\Users\aleco\Documents\Fidelizacion\FidelizacionFronted` | [FidelizacionFronted](https://github.com/alecondoupw/FidelizacionFronted), rama `main` | `f29da45` sobre `4f8ad6e` (`main`) |
| BE_REPO | `C:\Users\aleco\Documents\Fidelizacion\FidelizacionBackend` | [FidelizacionBackend](https://github.com/alecondoupw/FidelizacionBackend), rama `main` | `747e191` sobre `e9e0dd2` (`main`) |

Paulo autorizó commit y push el 2026-10-03. Se publicó primero en la rama `f0/base-tecnica` de cada repo y, por decisión de Paulo el mismo día, se fusionó en `main` por avance rápido (sin commits de fusión). Desde entonces `main` de FE y BE apunta a la revisión F0. La rama `f0/base-tecnica` se borró en local y remoto en los tres repos tras comprobar que estaba contenida en `main`; cada repo queda sólo con `main`. Remotos verificados con `git ls-remote`.

El nombre `FidelizacionFronted` conserva la grafía del repositorio existente. La raíz `E:/Repositorios/Hackathon/Zontes` que figuraba en la semilla no corresponde a este host; las rutas válidas son las de la tabla. Estas rutas son de este equipo: en otro host se registra su propia fila.

## Runtime y gestor

| Componente | Versión | Motivo |
| --- | --- | --- |
| Node.js | 24.14.1 (línea 24 LTS) | Firebase Admin SDK exige Node ≥ 22; Next 16 ≥ 20.9; ESLint/Vitest admiten 24. `.nvmrc` = `24`; `engines` `>=24 <25` con `engine-strict=true` |
| npm | 11.11.0 | Ya instalado; sin herramientas nuevas (pnpm no instalado). Lockfile `package-lock.json` por repo |
| Git | 2.53.0.windows.2 | — |

Fuentes oficiales consultadas el 2026-10-03: instalación de Next.js (docs versión 16.3.8: Node ≥ 20.9, TypeScript ≥ 5.1, `next lint` retirado en favor de la CLI de ESLint), configuración de Firebase Admin (Node 22+, ADC/`GOOGLE_APPLICATION_CREDENTIALS`), calendario de versiones de Node.js, metadatos `engines`/`peerDependencies` del registro npm y la documentación incluida en `node_modules/next/dist/docs/`.

## Versiones efectivas instaladas

**Frontend** — `next` 16.3.8 · `react`/`react-dom` 19.2.8 · `typescript` 5.9.3 · `tailwindcss` + `@tailwindcss/postcss` 4.3.3 · shadcn/ui (CLI `shadcn` 4.21.1 en dev, estilo `base-nova`, `@base-ui/react` 1.8.0, `cn` 0.4.0, `class-variance-authority` 0.7.1, `tw-animate-css` 1.4.0) · `lucide-react` 1.50.0 · `react-hook-form` 7.89.0 + `@hookform/resolvers` 5.9.1 · `zod` 4.6.5 · `recharts` 3.10.1 · `@tanstack/react-table` 9.2.4 · `date-fns` 4.4.0 · `firebase` 12.19.0 (sólo Auth) · dev: `eslint` 9.39.5, `eslint-config-next` 16.3.8, `eslint-config-prettier` 10.1.8, `prettier` 3.9.9, `vitest` 5.0.3, `@types/node` 24.19.1.

**Backend** — `express` 5.2.1 · `firebase-admin` 14.5.0 · `zod` 4.6.5 · `date-fns` 4.4.0 · `helmet` 8.3.0 · `cors` 2.8.6 · dev: `typescript` 5.9.3, `tsx` 4.23.15, `vitest` 5.0.3, `supertest` 7.3.1, `eslint` 9.39.5, `@eslint/js` 9.39.5, `typescript-eslint` 8.71.0, `eslint-config-prettier` 10.1.8, `globals` 17.13.0, `prettier` 3.9.9, `@types/*`.

**Por qué TypeScript 5.9 y ESLint 9 y no las últimas:** `create-next-app@16.3.8` genera `typescript ^5` y `eslint ^9`; `typescript-eslint` 8.71 exige TypeScript `<6.1`, lo que descarta TypeScript 7.0. Se usa la misma pareja en BE para alinear reglas. Subir a TypeScript 6.0 / ESLint 10 es una actualización posterior separada.

**No instalado en F0, por diseño del lote:** SheetJS y `@react-pdf/renderer` (DEC-07/09), Firebase Storage (sin archivos autorizados), Axios (ADR-08), Postman (herramienta manual externa), React Testing Library/jsdom (pruebas de componentes desde F1).

## Comandos

| Acción | FE (`FidelizacionFronted`) | BE (`FidelizacionBackend`) |
| --- | --- | --- |
| Instalación limpia | `npm ci` | `npm ci` |
| Variables locales | `cp .env.example .env.local` | `cp .env.example .env` |
| Desarrollo | `npm run dev` → `http://localhost:3000` | `npm run dev` → `http://127.0.0.1:4000` |
| Cadena completa | `npm run check` (formato → lint → typecheck → test → build) | `npm run check` |
| Arranque de prueba | `npm run smoke` (tras build; puerto 3100) | `npm run smoke` (tras build; puerto 4100) |
| FE→BE | `INTEGRATION_API_BASE_URL=http://localhost:4000 npm run test:integration` con el BE en marcha | — |

## Variables de entorno (sólo nombres)

| Repo | Variable | Uso | Valor en F0 |
| --- | --- | --- | --- |
| FE | `NEXT_PUBLIC_API_BASE_URL` | URL base del BE, sin `/api/v1`; se inserta en build | local `http://localhost:4000` |
| FE | `NEXT_PUBLIC_FIREBASE_API_KEY`, `_AUTH_DOMAIN`, `_PROJECT_ID`, `_APP_ID` | SDK cliente Auth | vacías (DEC-02) |
| BE | `NODE_ENV`, `HOST`, `PORT` | Arranque | `development`, `127.0.0.1`, `4000` |
| BE | `CORS_ALLOWED_ORIGINS` | Orígenes FE, separados por coma | `http://localhost:3000` |
| BE | `FIREBASE_PROJECT_ID`, `GOOGLE_APPLICATION_CREDENTIALS` | Admin SDK vía ADC; el archivo de credenciales vive fuera del repo | vacías (DEC-02) |

Custodio de valores reales: pendiente de DEC-02. `.env*` (salvo `.env.example`), `*.pem` y archivos de cuenta de servicio están ignorados por Git en ambos repos. No registrar aquí valores, tokens ni correos reales.

## Problemas encontrados y resolución

| Problema | Resolución / estado |
| --- | --- |
| `npm audit` FE: `@grpc/grpc-js` ≤1.13.5 (high, 2 avisos) vía `firebase` → `@firebase/firestore` (fija `~1.9.0`) | Sin versión compatible; `audit fix --force` bajaría firebase a 9.14. **Riesgo aceptado y mitigado:** el FE no usa Firestore (regla ESLint que prohíbe `firebase/firestore`, `firebase/storage`, `firebase-admin`). Revisar en cada actualización de firebase |
| `npm audit` FE dev: `braces` (high, sin versión corregida) vía `fast-glob` en `eslint-config-next` y CLI `shadcn` | Sólo herramientas de desarrollo; sin corrección publicada. `shadcn` se movió a `devDependencies` para dejar producción con un único paquete raíz vulnerable |
| `npm audit` BE: `uuid` <11.1.1 (moderate) vía `gaxios` 6.7.1 ← `@google-cloud/storage` ← `firebase-admin` | `audit fix` no aplica (gaxios 6.x fija `uuid ^9`). Aviso sobre v3/v5/v6 con `buf`; gaxios usa v4. Riesgo aceptado; Storage no se usa en F0 |
| Zod 4 ejecuta `refine` aunque `z.url()` falle → `CORS_ALLOWED_ORIGINS="*"` lanzaba `Invalid URL` sin mensaje controlado | Detectado por prueba; corregido con `URL.canParse` |
| Smoke FE en Windows: aserción libuv `UV_HANDLE_CLOSING` al llamar `process.exit` con el hijo cerrándose | Esperar `exit` del hijo y usar `process.exitCode` (ambos scripts) |
| `TaskStop` de la sesión no termina el hijo `node` en Windows | Procesos verificados por línea de comandos y cerrados por PID |
| `typecheck` del FE sin `LayoutProps` antes del primer build | Script `next typegen && tsc --noEmit` |
| `npm ls` marca 6 paquetes WASM opcionales como *extraneous* | Están en el lockfile como opcionales de respaldo; peculiaridad de npm en win32, sin efecto |
| Next.js activa telemetría anónima por defecto | No se modificó configuración del usuario; desactivable con `npx next telemetry disable` si Paulo lo decide |
| Con el BE detenido, Chrome tarda ~5–10 s en mostrar `NETWORK_ERROR` en `/diagnostico` (reintentos a `localhost`) | Aceptable en F0; el tiempo de espera del cliente es 10 s |

Ver [[05-Desarrollo/Testing]] para resultados, [[02-Arquitectura/Contrato API v0 - F0]] para el contrato y [[05-Desarrollo/Ramas y entregas]] para la política de entrega.
