---
title: "F8-FE-01 — Flujo de importacion administrador"
tags: [zontes, lote, f8]
status: implementado
fase: F8
frente: FE
updated: 2026-10-04
---

# F8-FE-01 — Flujo de importacion administrador

**Estado (2026-10-04):** Implementado en `/admin/clientes/importar` (UI-23) y verificado con pruebas de componentes. Falta la revisión visual en tres tamaños con una sesión de administrador. Evidencia en [[05-Desarrollo/Testing]] «Corridas F8».

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 1–2; REQ-25 |
| Objetivo | Ofrecer en Clientes el botón Importar clientes, selección de marca y archivo, preview, confirmación, resultado y reporte. |
| Depende de | F8-BE-01/02; DEC-17 |
| Interfaz / referencia | UI-23 · [[09-Entradas/Referencias UI 2026-10-02/Administrador/A02-importacion-clientes-admin.jpeg|A02]]; SRC-06 pp. 1–2 prevalece para comportamiento |
| Repositorio de implementación | FE_REPO (Next.js); rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [x] El flujo muestra nombre, correo, marca, asociaciones existentes/nuevas, filas excluidas y motivos antes de confirmar; permite cancelar.
- [x] Al confirmar, muestra indicadores no excluyentes, reporte descargable y errores por fila sin exponer datos de otra marca; no ofrece alta manual de clientes.
- [ ] Estados de carga/error/permiso/éxito y diseño usable en escritorio, tablet y móvil con foco y controles accesibles.

## Verificación prevista

Pruebas de componente y navegador con contrato BE; capturas UI-23 en 1280/768/375 px y prueba de teclado. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
