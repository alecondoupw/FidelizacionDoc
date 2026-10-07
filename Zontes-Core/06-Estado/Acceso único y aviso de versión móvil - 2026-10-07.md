---
title: "Acceso único y aviso de versión móvil - 2026-10-07"
tags: [zontes, frontend, identidad, evidencia]
status: verificado-local
updated: 2026-10-07
---

# Acceso único y aviso de versión móvil

## Solicitud y cambio implementado

Corrección directa de Paulo al selector anterior: un solo botón, en el mismo lugar en ambos ingresos, que muestre el rol de destino y cambie a su pantalla. Persona cliente sin aro exterior; cabeza de administrador circular. Solicitud adicional: aviso exclusivo de vista móvil recomendando la versión móvil, con icono de descarga todavía sin función.

Se conserva `SelectorAcceso` como interfaz existente, con un único enlace. En `/ingresar` muestra Admin y abre `/admin/ingresar`; en el ingreso de admin muestra Cliente y abre `/ingresar`. Se coloca en la esquina derecha de una cabecera común de `PanelAcceso`, por encima del panel visual y del formulario, con posición consistente entre roles. Fondo negro, figura `#dcfc36`, 48 × 48 px, nombre accesible y foco visible.

Las imágenes nuevas son `public/imagenes/acceso-cliente-v2.png` y `public/imagenes/acceso-admin-v2.png` dentro de `E:/Repositorios/Hackathon/MainRepo/Fidelazacion/FidelizacionFronted/`. El personaje cliente no lleva círculo envolvente. El admin mantiene los engranajes y la cabeza es circular.

## Aviso móvil

Componente `src/components/movil/aviso-app-movil.tsx`, compartido desde `src/app/layout.tsx`. Aparece al usar un ancho inferior a 768 px mediante la regla responsive del proyecto, y se oculta a partir de 768 px. No depende de identificar el dispositivo por user agent. No es un modal ni bloquea el formulario.

Texto: “Zontes en tu celular”, “Te recomendamos descargar la versión móvil.” y “Descarga próximamente.”. Botón circular con icono Download, nombre accesible, explicación asociada y atributo nativo disabled. No URL, manejador de descarga ni archivo instalable en este cambio.

## Adaptación de activos

Herramienta integrada **imagegen**, fondo transparente. El CSS utiliza el alfa como máscara para aplicar exactamente el verde de la página.

Prompt administrador:

> Use case: precise-object-edit / background-extraction. Edit target: provided black user icon. Asset: small UI login role switch figure. Replace the long oval face/head with a PERFECTLY ROUND circular head, like the standard user avatar. Retain the torso/shoulders and both recognizable gears behind the person. Ensure the entire circle has transparent gap separating it from gears and shoulders. Round head centrally placed, roughly 35% of total icon width. Render clean flat solid lime green #dcfc36 silhouette on genuine transparent background, removing all original white background/internal gaps. Crisp smooth geometric edges like a vector icon; NO texture, speckles, brush strokes, stray pixels, gradients, shadows, text, button or background disk. Square canvas, centered composition, entire icon contained within 80% of canvas for safe clear margin. Suitable for 32px display.

Prompt cliente:

> Use case: precise-object-edit / background-extraction. Edit target: provided black user icon. Asset: small UI login role switch figure. REMOVE the entire outer circular border/ring, leaving ONLY the person's circular head and shoulder/bust silhouette. No surrounding ring, no outline, no circle around the body. Head must be a perfect circle separated from shoulders by a clear transparent gap. Render clean flat solid lime green #dcfc36 silhouette on genuine transparent background, removing all original white background/internal gaps. Crisp smooth geometric edges like a vector icon; NO texture, speckles, brush strokes, stray pixels, gradients, shadows, text, button or background disk. Square canvas, centered composition, entire icon contained within 80% of canvas for safe clear margin. Suitable for 32px display.

## Evidencia ejecutada

- Chrome real / Playwright a 1440 × 1000 y 375 × 950.
- Un solo enlace en cada ingreso; clic cliente → admin → cliente y Enter correctos.
- Coordenadas y dimensiones del botón comparadas entre roles: iguales en ambos anchos.
- Aviso móvil visible a 375 y 767 px; oculto a 768 y 1440 px.
- Aviso también presente en registro, al compartir el layout raíz.
- Botón de descarga deshabilitado y estado explicado mediante aria-describedby.
- Iconos nuevos HTTP 200; fondo negro y verde RGB (220, 252, 54).
- Sin errores JavaScript ni desbordamiento horizontal.
- Cuatro pruebas existentes de shell aprobadas; typecheck y ESLint de los cuatro archivos afectados aprobados.

Capturas y registro locales excluidos de Git en `E:/Repositorios/Hackathon/MainRepo/Fidelazacion/.demo-local/`: `acceso-unico-{cliente,admin}-{1440,375}.png` y `verificacion-acceso-unico-movil.json`.

Sustituye el comportamiento de dos botones documentado en [[Icono Zontes y selector de acceso - 2026-10-07]]. Cambios locales sin commit ni push.
