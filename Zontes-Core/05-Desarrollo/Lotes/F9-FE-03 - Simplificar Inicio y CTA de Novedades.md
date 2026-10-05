---
title: "F9-FE-03 — Simplificar Inicio y CTA de Novedades"
tags: [zontes, lote, f9, frontend]
status: pendiente
fase: F9
frente: FE
updated: 2026-10-05
---

# F9-FE-03 — Simplificar Inicio y CTA de Novedades

| Campo | Contenido |
| --- | --- |
| Fuente | SRC-07/09, pedidos de Inicio e imágenes [[09-Entradas/Referencias UI 2026-10-05/Manifiesto de imagenes F9\|R01/R02]]; SRC-06 p. 4/C08 históricos; UI-13/28, DEC-19/20/22 |
| Objetivo | Ajustar el card hero de Inicio según la composición R01 usando R02; quitar «Cómo ganar puntos» y «Explorar catálogo»; dejar «Ver novedades» como única acción del banner hacia UI-28. |
| Repositorio | FE_REPO Next.js de [[05-Desarrollo/Entorno local]]; BE_REPO sin cambio previsto |
| Depende de | F9-D-01; F8-FE-05 existente |
| Contrato | Banner y `/novedades?marca=` siguen mostrando sólo publicaciones activas de marcas vinculadas; saldos/vencimientos no cambian. |
| Prueba | F9-T03: contenido y CTA; F9-T08: colocación/recorte de R02, carga y lectura en 1280/768/375 px, teclado y estados vacíos. |

## Aceptación

- [ ] «Cómo ganar puntos» y sus tarjetas no aparecen en Inicio; las reglas BE no se eliminan y la administración de reglas no cambia.
- [ ] El banner no ofrece «Explorar catálogo»; su CTA visible es «Ver novedades» y abre UI-28 con un filtro válido si lo hay.
- [ ] R02 ocupa el card hero ancho bajo el encabezado de Inicio; en escritorio texto/CTA HTML a la izquierda sobre el área de cielo y tres vehículos/logos integrados a la derecha, conforme a R01. No usar R01 como imagen de fondo ni duplicar logos. En móvil ajustar encuadre o apilar texto e imagen dentro del mismo card para conservar vehículos, logotipos y legibilidad; no estirar ni cortar contenido clave.
- [ ] Reservar dimensiones y servir tamaños adecuados con optimización de Next.js; si falla R02, texto/CTA siguen operativos. No aplicar filtros de color que alteren las marcas.
- [ ] El carrusel de destacadas, saldos, vencimientos, avisos y accesos funcionales restantes conservan datos/estados reales. Si hay un botón independiente «Novedades» en el cuerpo de Inicio, retirarlo al crear el acceso de sidebar en F9-FE-05.
- [ ] Actualizar pruebas y referencias del manual al estado nuevo, sin reetiquetar F8-T08 como prueba F9.

**Índice:** [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]].
