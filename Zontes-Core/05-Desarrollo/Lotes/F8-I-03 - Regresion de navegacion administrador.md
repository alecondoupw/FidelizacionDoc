---
title: "F8-I-03 — Regresion de navegacion administrador"
tags: [zontes, lote, f8]
status: pendiente
fase: F8
frente: Integración
updated: 2026-10-04
---

# F8-I-03 — Regresion de navegacion administrador

**Estado (2026-10-04):** Smoke de rutas y pruebas de componentes en verde; falta el recorrido visual con sesión de administrador en tres tamaños. Evidencia en [[05-Desarrollo/Testing]] «Corridas F8».

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 2–3; REQ-27 |
| Objetivo | Verificar que el panel ofrece sólo las entradas aprobadas y mantiene los flujos no afectados. |
| Depende de | F8-FE-03/04; DEC-18/19 |
| Interfaz / referencia | UI-10/12/19/24 y menú |
| Repositorio de implementación | FE_REPO + BE_REPO, con un único integrador; rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [ ] No hay enlaces a Tendencias/Vencimiento ni formularios de evento/resta; Registrar puntos y Publicaciones por marca abren la vista correcta.
- [ ] Publicaciones conserva altas, edición, estado, filtros y botones; los demás apartados siguen accesibles con permisos adecuados.
- [ ] Escritorio, tablet y móvil mantienen navegación completa sin desborde ni pérdida de controles.

## Verificación prevista

Recorrido navegador FE↔BE con admin y cliente sin permiso; T-NAV/T-UI y regresión F5/F6. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
