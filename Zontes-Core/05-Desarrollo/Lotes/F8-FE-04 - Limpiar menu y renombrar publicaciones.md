---
title: "F8-FE-04 — Limpiar menu y renombrar publicaciones"
tags: [zontes, lote, f8]
status: implementado
fase: F8
frente: FE
updated: 2026-10-04
---

# F8-FE-04 — Limpiar menu y renombrar publicaciones

**Estado (2026-10-04):** Menú sin Tendencias ni Vencimiento (páginas retiradas; sin enlaces huérfanos), «Publicaciones por marca» en menú y título; API de tendencias retirada según DEC-19. Smoke 29/29. Evidencia en [[05-Desarrollo/Testing]] «Corridas F8».

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 2–3; REQ-27 |
| Objetivo | Quitar Tendencias y Vencimiento como apartados independientes y renombrar Contenido por marca sin alterar las acciones de publicaciones. |
| Depende de | F8-D-01; DEC-18/19; F5-FE-02; F6-FE-01 |
| Interfaz / referencia | UI-10/12/19; menú admin · [[09-Entradas/Referencias UI 2026-10-02/Administrador/A09-contenido-marca-admin.jpeg|A09]] sólo como composición histórica de UI-12 |
| Repositorio de implementación | FE_REPO (Next.js); rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [x] El menú y la navegación no muestran Tendencias ni Vencimiento; antiguos enlaces se redirigen o retiran según contrato aprobado, sin dejar rutas huérfanas.
- [x] Menú y título de UI-12 dicen Publicaciones por marca; botones, formularios, demás textos y permisos se conservan.
- [x] Dashboard, Actividad, Movimientos, Canjes y Exportación permanecen disponibles; la API de tendencias sólo se retira si DEC-19 lo confirma.

## Verificación prevista

Pruebas de navegación/regresión de publicaciones en tres tamaños; enlaces internos y accesibilidad. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
