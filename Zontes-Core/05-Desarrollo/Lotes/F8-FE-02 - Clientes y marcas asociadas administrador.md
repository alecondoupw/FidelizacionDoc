---
title: "F8-FE-02 — Clientes y marcas asociadas administrador"
tags: [zontes, lote, f8]
status: planificado
fase: F8
frente: FE
updated: 2026-10-03
---

# F8-FE-02 — Clientes y marcas asociadas administrador

**Estado:** planificado por SRC-06; implementación y pruebas no ejecutadas. La aprobación de cambios de alcance y contratos se registra en [[02-Arquitectura/Impacto SRC-06 y decisiones F8]] antes de abrir el trabajo operativo.

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 2; REQ-25 |
| Objetivo | Actualizar listado y detalle para mostrar todas las marcas y el estado de vinculación de cada cliente importado o registrado. |
| Depende de | F8-BE-02; F4-FE-02; DEC-17 |
| Interfaz / referencia | UI-07 · [[09-Entradas/Referencias UI 2026-10-02/Administrador/A01-clientes-admin.jpeg|A01]]; SRC-06 pp. 1–2 define nuevos campos/estado |
| Repositorio de implementación | FE_REPO (Next.js); rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [ ] Búsqueda por correo y filtro por marca reflejan la respuesta autorizada del BE; cada cliente muestra 0–3 asociaciones y su estado.
- [ ] El listado no presenta Crear cliente manualmente; la gestión de administradores sigue en UI-06 independiente.
- [ ] Saldo y movimientos se muestran por marca, incluso tras reimportación, sin suma canjeable compartida.

## Verificación prevista

Pruebas FE con cliente pendiente, verificado, multimarcas y sin marcas; visual y accesibilidad en tres tamaños. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
