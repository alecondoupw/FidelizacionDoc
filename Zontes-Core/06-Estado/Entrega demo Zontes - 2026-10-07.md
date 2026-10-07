---
title: "Entrega demo Zontes - 2026-10-07"
tags: [zontes, entrega, demo, git]
status: verificado-publicado-en-git
updated: 2026-10-07
---

# Entrega demo Zontes — 2026-10-07

Paulo autorizó documentar los cambios y hacer commit/push en main de frontend, backend y documentación. Fecha del equipo de Paulo: 2026-10-07, America/La_Paz.

## Código publicado

| Repositorio | Rama | Commit | Resultado |
| --- | --- | --- | --- |
| FidelizacionFronted | main | [d4d377a](https://github.com/alecondoupw/FidelizacionFronted/commit/d4d377ab4840f8e2c3fe88266b537aca01505302) | Push confirmado; SHA remoto coincide con HEAD. |
| FidelizacionBackend | main | [4a32dac](https://github.com/alecondoupw/FidelizacionBackend/commit/4a32dac47a9f51bc642386ff62d37eff4ddfb954) | Push confirmado; SHA remoto coincide con HEAD. |
| FidelizacionDoc | main | Esta entrega documental | Contiene documentación, manuales, evidencia e índices. |

## Cambios

- Frontend: identidad Zontes, logo y favicon; único acceso entre cliente/admin, figuras adaptadas y banner admin centrado.
- PWA: manifiesto, iconos móviles, botón de instalación, instrucciones para Safari/otros navegadores, detección de modo app y aviso sin conexión.
- Backend: autor y encabezado Zontes en comprobantes PDF, conservando contratos y reglas existentes.
- README de cada repositorio enlaza sus cambios y la guía de despliegue.
- Core: manuales de demo, cambios por frente, guía Render/Vercel, instalación móvil y referencias actualizadas.

Detalles: [[05-Desarrollo/Cambios frontend - identidad Zontes y PWA]], [[05-Desarrollo/Cambios backend - comprobantes Zontes y demo]], [[08-Produccion/Guia rapida - Render Vercel y demo 2026-10-07]], [[07-Manuales/Instalar Zontes en el celular - PWA]] y [[07-Manuales/Datos y accesos de demo - 2026-10-07]].

## Verificación previa a commit

| Frente | Comandos | Resultado |
| --- | --- | --- |
| Frontend | ESLint focalizado, npm run typecheck, pruebas shell-f9 y service-worker, npm run build | 8 pruebas aprobadas; lint/tipos/build sin errores. |
| Backend | ESLint comprobante.ts, npm run typecheck, pruebas canjes-http y config/env, npm run build | 20 pruebas aprobadas; lint/tipos/build sin errores. |
| Git | fetch, comparación HEAD...origin/main, diff --cached --check y revisión de secretos | Ambas bases coincidentes con main remoto antes de commit; archivos preparados sin secretos. |

Durante la implementación también se verificaron en Chrome: centro del banner (0 px de desviación), un solo enlace en ambos ingresos, teclado, ancho móvil y colores; manifest e instalabilidad sin errores en perfil normal; eventos de instalación simulados, instrucciones iOS y worker real con pantalla offline. Caché limitada al aviso e icono públicos.

No se repitieron pruebas que modificaran Firebase durante esta publicación. Los datos ficticios y cuentas existentes continúan en el proyecto de desarrollo; git pull y el despliegue no los siembran en otra base.

## Secretos y artefactos locales

.env, .env.local, JSON Admin SDK, contraseñas de prueba, script de carga, respaldos y perfiles de navegador de prueba quedan fuera de los commits. Las versiones iniciales descartadas de los iconos se conservan únicamente en .demo-local/iconos-v1; el producto utiliza los iconos v2.

Los registros anteriores de esta fecha describen las verificaciones antes de publicar y conservan sus límites históricos. Este documento registra la entrega posterior en GitHub.

## Pendiente de operación

Paulo publicará frontend y backend en HTTPS después de este agregado. Render/Vercel no se desplegaron en esta tarea. La instalación física en un celular todavía no se verificó. Las cuentas genéricas se comunican a Paulo fuera de Git; se recomienda mantenerlas como cuentas de demo.
