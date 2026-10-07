---
title: "Icono Zontes y selector de acceso - 2026-10-07"
tags: [zontes, frontend, identidad, evidencia]
status: verificado-local
updated: 2026-10-07
---

# Icono Zontes y selector de acceso

## Petición y resultado

Petición directa de Paulo: utilizar el recurso Zontes aportado para el distintivo de la aplicación y el icono de navegador, y añadir botones circulares negros con las figuras de administrador y cliente en verde de la paleta.

El archivo encontrado es `public/imagenes/zontesIcon.jpg` (225 × 225), aunque en la petición se denominó PNG. Se conserva su imagen original. `MarcaApp` utiliza ese JPG en acceso y sidebars; `src/app/icon.jpg` es una copia idéntica para el mecanismo de metadatos de Next.js. Se retira el favicon predeterminado.

`SelectorAcceso` contiene dos enlaces de 48 × 48 px con fondo negro, figuras mediante máscaras alfa y color exacto `--zontes-lima: #dcfc36`. “Cliente” abre `/ingresar`; “Admin” abre `/admin/ingresar`. El rol actual lleva un anillo verde y `aria-current="page"`. Los enlaces tienen nombres accesibles y foco visible. Se integra exclusivamente en ambas páginas de ingreso. La selección sólo cambia la pantalla de autenticación.

## Activos y adaptación

Activos de producto dentro de `E:/Repositorios/Hackathon/MainRepo/Fidelazacion/FidelizacionFronted/`:

- `public/imagenes/zontesIcon.jpg`
- `src/app/icon.jpg`
- `public/imagenes/acceso-admin.png`
- `public/imagenes/acceso-cliente.png`

Se utilizó la herramienta integrada **imagegen**, con fondo transparente, una edición por figura aportada. La máscara CSS fija el verde exacto independientemente del color RGB generado.

Prompt administrador:

> Use case: background-extraction. Edit target: attached black silhouette icon. Asset type: small login role selector icon. Keep the head and shoulder silhouette with both gears exactly recognizable. Replace the black/dark shape with one flat solid lime green #dcfc36. Remove ALL white background and white internal gaps to actual transparency. Preserve original recognizable geometry and proportions, improve crisp edges for readability at 32px. Center in a square canvas with about 5% transparent margin. No button, no background disk, no text, no shadows, no gradients, no glow. Only green silhouette on genuinely transparent background.

Prompt cliente:

> Use case: background-extraction. Edit target: attached black silhouette icon. Asset type: small login role selector icon. Keep the simple circular user avatar and enclosing circle exactly recognizable. Replace the black/dark shape with one flat solid lime green #dcfc36. Remove ALL white background and white internal gaps to actual transparency. Preserve original recognizable geometry and proportions, improve crisp edges for readability at 32px. Center in a square canvas with about 5% transparent margin. No button, no background disk, no text, no shadows, no gradients, no glow. Only green silhouette on genuinely transparent background.

## Evidencia ejecutada

- Navegador Chrome real mediante Playwright, resoluciones 1440 × 1000 y 375 × 950.
- Recorrido cliente → admin → cliente mediante clic, selección y destinos correctos en ambas resoluciones.
- Activación mediante teclado Enter verificada.
- Cuatro vistas sin errores JavaScript y sin desbordamiento horizontal; revisión visual de capturas.
- Figuras servidas con HTTP 200; fondo negro y color RGB (220, 252, 54) comprobados.
- Logo cargado; icono de navegador servido y comparado byte a byte con el JPG original. Ninguna referencia al favicon anterior en el head.
- `vitest run src/components/shell/shell-f9.test.tsx`: cuatro pruebas aprobadas.

Evidencia local excluida de Git: `E:/Repositorios/Hackathon/MainRepo/Fidelazacion/.demo-local/verificacion-accesos-zontes.json` y `accesos-zontes-{cliente,administrador}-{1440,375}.png`.

Cambios locales; no se realizó commit ni push para esta petición.

Verificación final: npm run typecheck y ESLint de los cinco archivos afectados completados sin errores.
