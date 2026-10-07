---
title: "Instalar Zontes en el celular - PWA"
tags: [zontes, manual, pwa, movil]
status: preparado-para-publicar
updated: 2026-10-07
---

# Instalar Zontes en el celular

## Qué se preparó

Zontes puede añadirse a la pantalla de inicio con su icono y abrirse en modo app independiente, sin barra de direcciones, en navegadores compatibles. El botón con icono de descarga del aviso móvil ya está habilitado:

- Si el navegador ofrece la instalación, el botón abre su confirmación nativa.
- Si requiere instalación manual, el botón explica los pasos.
- Dentro de la app instalada se oculta el aviso.
- Si no hay internet, se muestra un aviso para reconectarse. Los puntos, canjes y demás módulos necesitan conexión.

La confirmación depende del usuario y del navegador; la página no puede instalarse automáticamente. Los navegadores y sistemas no ofrecen todos la misma experiencia. [Instalación y compatibilidad — MDN](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable).

## Antes de probarlo en tu celular

Paulo indicó que publicará la web después de este agregado. Esta copia todavía usa localhost; la instalación física no se ha verificado.

1. Publica **esta versión actualizada del frontend** en Vercel u otro alojamiento HTTPS. Incluye manifest, carpeta public/pwa y public/sw.js.
2. Publica también el backend Express en HTTPS para utilizar el sistema desde el teléfono.
3. En el frontend de producción, configura NEXT_PUBLIC_API_BASE_URL con la URL pública del backend, sin /api/v1. Conserva la configuración cliente de Firebase.
4. En el backend, agrega el origen HTTPS del frontend a CORS_ALLOWED_ORIGINS.
5. Revisa los dominios autorizados de Firebase Authentication para los flujos que requieran el dominio publicado.
6. Abre la URL pública del frontend en el celular, en una pestaña normal.

Guía de publicación existente: [Render y Vercel](E:/Repositorios/Hackathon/MainRepo/Fidelazacion/GUIA-DESPLIEGUE-RENDER-VERCEL.md).

Una dirección localhost en tu celular apunta al propio celular, no a tu computadora. Una IP de la computadora por HTTP en la red local no sustituye el HTTPS de publicación para instalar la PWA. [Requisitos de instalación — MDN](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable).

## Android

Para la experiencia de app independiente, utiliza preferentemente **Chrome**:

1. Abre el sitio publicado.
2. Toca el icono de descarga del aviso “Zontes en tu celular”.
3. Confirma la instalación ofrecida por el navegador.
4. Si aparece una guía, abre el menú del navegador y busca “Instalar app” o “Añadir a pantalla de inicio”.
5. Abre Zontes desde su nuevo icono.

Brave, Opera y otros navegadores pueden ofrecer otra modalidad de acceso directo. El soporte y la presencia de barras varían; el botón ofrece instrucciones cuando no recibe una solicitud nativa de instalación. [Compatibilidad móvil — MDN](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable).

## iPhone / iPad

1. Abre el sitio en **Safari**.
2. Toca el icono de descarga para consultar la guía.
3. Usa **Compartir → Añadir a pantalla de inicio**.
4. Si aparece **Abrir como app**, déjalo activado.
5. Toca **Añadir** y abre Zontes desde el icono nuevo.

Safari utiliza este flujo manual. El navegador debe permitir la opción en el dispositivo. [Añadir una web a la pantalla de inicio — Apple](https://support.apple.com/guide/iphone/bookmark-a-website-iph42ab2f3a7/ios).

## Qué comprobar después de publicar

- El icono Zontes aparece en la pantalla de inicio.
- Al abrir desde el icono, no se muestra la barra de direcciones en el navegador compatible.
- El aviso de instalación se oculta dentro de la app.
- El ingreso, puntos y canjes funcionan con el backend público.
- Al perder conexión aparece “Sin conexión”; al recuperarla, “Volver a intentar” abre el ingreso.

## Implementación y evidencia local

Código en E:/Repositorios/Hackathon/MainRepo/Fidelazacion/FidelizacionFronted/:

- src/app/manifest.ts: nombre, identidad, inicio /ingresar, scope / y display standalone.
- public/pwa/icon-192.png, icon-512.png y apple-touch-icon.png: exportaciones del JPG Zontes original.
- src/app/layout.tsx: metadatos móviles, icono Apple y color de tema.
- src/components/movil/aviso-app-movil.tsx: instalación disponible, cancelación, guía manual y detección de modo app.
- public/sw.js: sólo conserva el aviso offline y el icono público; las páginas y API usan la red sin guardarse en esta caché.
- public/pwa/offline.html: pantalla de reconexión.
- src/components/acceso/panel-acceso.tsx: banner admin centrado en ambos ejes.

Verificación del 2026-10-07:

- Centro del bloque de texto admin coincide con el centro del banner: desviación 0 px en X e Y.
- Chrome real con perfil dedicado normal: Page.getInstallabilityErrors sin errores; manifest sin errores.
- Manifest, iconos 192/512 y metadatos Apple verificados por HTTP/DOM.
- Simulados los eventos de confirmación, cancelación y appinstalled; escenarios de instrucciones iOS, navegador sin evento, HTTP no seguro y modo app.
- Service worker registrado y activo; navegación sin internet muestra el aviso; regreso al ingreso con red restaurada.
- Caché inspeccionada: sólo /pwa/offline.html y /pwa/icon-192.png.
- Ocho pruebas Vitest aprobadas: cuatro del shell y cuatro sobre límites de la caché y comportamiento del worker.
- Typecheck, ESLint de código y build de producción aprobados.

Evidencia reproducible local, excluida de Git: E:/Repositorios/Hackathon/MainRepo/Fidelazacion/.demo-local/verificacion-pwa.json, verificacion-pwa-instalabilidad.json y verificar-pwa.cjs. Las instrucciones iOS se probaron mediante emulación de agente de usuario en Chrome; no equivalen a una prueba en un iPhone físico.

No se publicó ni se instaló en un teléfono durante esta tarea. Los cambios siguen locales, sin commit ni push.
