---
title: "Cambios frontend - identidad Zontes y PWA"
tags: [zontes, frontend, cambios]
status: implementado-verificado-local
updated: 2026-10-07
---

# Cambios del frontend

Solicitudes directas de Paulo, aplicadas sobre main después de actualizar a eea0a76.

## Identidad e interfaz

- Zontes sustituye MOTO LOYALTY en títulos, accesos y metadatos.
- MarcaApp utiliza el logo original zontesIcon.jpg en acceso y sidebars; la pestaña también utiliza ese logo.
- SelectorAcceso muestra un único botón circular negro con figura verde #dcfc36, en la misma cabecera de ambos ingresos.
- En /ingresar, el botón Admin lleva a /admin/ingresar; en el ingreso admin, Cliente lleva a /ingresar.
- Figura cliente sin círculo exterior; figura admin con cabeza redonda y engranajes.
- Banner admin centrado en ambos ejes, con la nota de seguridad separada abajo.
- Se conservan las fotografías y simplificaciones F9 incorporadas desde origin/main.

## Versión instalable para móviles

- Aviso de instalación para anchos menores de 768 px; oculto dentro de la app instalada.
- Manifest con inicio /ingresar, scope /, display standalone, nombre e iconos de Zontes.
- Iconos PNG 192/512 y Apple 180 px exportados desde el logo original.
- Botón habilitado: confirmación nativa cuando el navegador ofrece beforeinstallprompt; instrucciones para Safari y otros navegadores.
- Estados de instalación, cancelación y appinstalled; detección de apertura como app.
- Pantalla “Sin conexión” con reintento. El sistema de puntos y beneficios requiere red.

La PWA necesita HTTPS en la web publicada. La experiencia instalada depende del navegador; se recomienda Chrome en Android y Safari en iPhone para apertura independiente. La web no instala nada sin confirmación. [Compatibilidad — MDN](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable).

## Código y contratos

| Ruta | Responsabilidad |
| --- | --- |
| src/components/marca/marca-app.tsx | Identidad compartida. |
| src/components/acceso/selector-acceso.tsx y panel-acceso.tsx | Cambio de ingreso y composición. |
| src/components/movil/aviso-app-movil.tsx | Instalación, instrucciones y modo app. |
| src/app/manifest.ts y layout.tsx | Manifiesto y metadatos móviles. |
| public/pwa y public/sw.js | Iconos y pantalla offline. |
| src/lib/pwa/service-worker.test.ts | Límites de caché y uso de la red. |

El selector cambia la pantalla; Express sigue autorizando el rol. La PWA no requiere nuevos endpoints ni cambios de datos. El worker guarda sólo el aviso offline y su icono, nunca páginas protegidas, tokens ni respuestas de API.

## Configuración y evidencia

NEXT_PUBLIC_API_BASE_URL apunta al backend sin /api/v1. Las cuatro NEXT_PUBLIC_FIREBASE_* corresponden al mismo proyecto Firebase del backend y se configuran antes del build.

Ocho pruebas focalizadas, typecheck, ESLint y build de producción aprobados. Chrome con perfil normal no reportó errores de manifest/instalabilidad. Banner con desviación de centro de 0 px en X/Y. Flujos nativo aceptado/cancelado simulados; guía iOS mediante emulación de agente de usuario; worker y navegación offline comprobados en Chrome. Publicación e instalación física en teléfono pendientes.

Ver [[08-Produccion/Guia rapida - Render Vercel y demo 2026-10-07]], [[07-Manuales/Instalar Zontes en el celular - PWA]] y [[06-Estado/Entrega demo Zontes - 2026-10-07]].
