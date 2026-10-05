---
title: "F9-FE-05 — Sidebar Zontes y Novedades"
tags: [zontes, lote, f9, frontend, navegacion]
status: pendiente
fase: F9
frente: FE
updated: 2026-10-05
---

# F9-FE-05 — Sidebar Zontes y Novedades

| Campo | Contenido |
| --- | --- |
| Fuente | SRC-07; UI-13/28; C08 y mockups admin como referencia de estructura, no de texto final |
| Objetivo | Mostrar «Zontes» junto al icono del sidebar en cliente y admin; añadir «Novedades» al menú cliente con destino UI-28. |
| Repositorio | FE_REPO Next.js de [[05-Desarrollo/Entorno local]] |
| Depende de | F9-D-01 y F9-FE-03 para evitar acceso rápido duplicado |
| Contrato | `/novedades?marca=` conserva permisos/filtros de contenido; no abrir la ruta a un rol no autorizado. |
| Prueba | F9-T05: navegación de ambos roles, menú compacto/móvil, rutas, foco/estado activo y CTA de Inicio. |

## Aceptación

- [ ] Texto del distintivo del sidebar es «Zontes» en cliente y administrador; revisar sidebar expandido/contraído y menú móvil sin cambiar el icono por un logo no autorizado.
- [ ] «Novedades» aparece como destino persistente en sidebar cliente y en el menú accesible de tablet/móvil; estado activo correcto y destino UI-28. No crear destino Novedades admin por inferencia.
- [ ] Inicio conserva únicamente el CTA «Ver novedades» del banner; retirar acceso rápido independiente si existe. No perder rutas de Catálogo ni el cierre de sesión.
- [ ] Sin desbordes en 1280/768/375 px, objetivos táctiles adecuados, nombres accesibles y recorrido sólo con teclado.

**Índice:** [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]].
