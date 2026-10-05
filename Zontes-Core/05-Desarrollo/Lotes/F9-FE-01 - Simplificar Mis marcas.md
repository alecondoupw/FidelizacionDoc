---
title: "F9-FE-01 — Simplificar Mis marcas"
tags: [zontes, lote, f9, frontend]
status: pendiente
fase: F9
frente: FE
updated: 2026-10-05
---

# F9-FE-01 — Simplificar Mis marcas

| Campo | Contenido |
| --- | --- |
| Fuente | SRC-07, punto «quitar el botón de marca active en el apartado de marcas»; C02/UI-17; ADR-12 |
| Objetivo | Retirar de `/marcas` el control visible para fijar «Marca activa», conservando la lista de marcas autorizadas y sus accesos. |
| Repositorio | FE_REPO Next.js de [[05-Desarrollo/Entorno local]]; BE_REPO sin cambio previsto |
| Depende de | F9-D-01; F1-FE-02 existente |
| Contrato | `/me` decide las marcas vinculadas; ninguna marca ajena aparece; la preferencia local sólo puede apuntar a una de ellas. |
| Prueba | F9-T01: DOM/teclado en cliente con 0, 1 y 3 marcas; catálogo/contenido por marca y móvil. |

## Aceptación

- [ ] No se renderiza botón, chip accionable ni texto «Marca activa» en UI-17; no queda control sin propósito en 1280/768/375 px.
- [ ] Las marcas vinculadas y el acceso al catálogo funcionan; marcas no vinculadas siguen excluidas.
- [ ] Eliminar o adaptar pruebas que exigían el control anterior, conservando pruebas de aislamiento por marca. No modificar el vínculo BE ni borrar preferencias locales existentes sin una decisión aparte.

**Índice:** [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]].
