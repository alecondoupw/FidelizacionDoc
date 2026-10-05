---
title: "Paleta Zontes propuesta F9"
tags: [zontes, diseno, f9]
status: propuesta
updated: 2026-10-05
---

# Paleta Zontes propuesta F9

Fuente visual: [[09-Entradas/Referencia web Zontes Bolivia 2026-10-05|SRC-08]]. Usuario pidió aplicar una paleta basada en ese sitio a cliente y administrador (SRC-07). **Los hexadecimales observados en CSS son evidencia; la asignación de roles y los colores complementarios son propuesta de diseño** pendiente de revisión al ejecutar F9. Sustituiría el índigo provisional de DEC-11, sin cambiar los colores que identifican datos de Zontes/Kiden/NIU.

![[02-Arquitectura/Paleta Zontes propuesta F9.svg]]

| Token propuesto | Valor | Procedencia | Uso previsto |
| --- | --- | --- | --- |
| `brand.ink` | `#1A1A1A` | CSS global del sitio | sidebar, encabezados, texto principal |
| `brand.lime` | `#DCFC36` | CSS global del sitio | CTA principal, navegación activa, foco sobre fondo oscuro |
| `brand.white` | `#FFFFFF` | CSS del sitio | texto en oscuro, tarjetas |
| `brand.red` | `#D2253D` | CSS de portada | acento editorial puntual; **no** sustituir el rojo semántico de error sin prueba |
| `surface.canvas` | `#F7F8F3` | propuesta derivada | fondo claro de ambos roles |
| `surface.border` | `#DDE2D4` | propuesta derivada | divisores y tarjetas; no usar como único contorno interactivo |
| `control.border` | `#67735A` | propuesta derivada | borde visible de campos y controles sobre blanco |
| `text.muted` | `#4B5563` | propuesta derivada | texto secundario en superficie clara |

**Reglas de aplicación:** texto oscuro sobre lima (contraste aproximado 14,9:1); blanco sobre tinta (17,4:1); blanco sobre rojo de portada (5,2:1). Nunca texto blanco sobre lima. `control.border` sobre blanco ofrece contraste aproximado 5,0:1; el borde claro es sólo decorativo. El foco debe ser visible tanto en superficie clara como en sidebar oscuro. Éxito, aviso y error conservan colores y etiquetas semánticas independientes de la paleta corporativa. Los gráficos por marca mantienen leyenda y contraste; no convertir todas las marcas en lima. La UI cliente y admin comparten tokens de identidad, con densidad y componentes adecuados a cada rol. Mantener la tipografía actual hasta resolver licencia y activos de DEC-11.

**Puerta de validación:** comparar portada oficial y pantallas reales; aprobar la selección exacta de tokens y revisar contraste de texto, bordes, hover, disabled, estados de error y 1280/768/375 px antes de sustituir la línea provisional. Véanse [[05-Desarrollo/Lotes/F9-FE-04 - Aplicar paleta en cliente y administrador]] y [[05-Desarrollo/Lotes/F9-I-01 - Regresion visual y funcional de ambas vistas]].
