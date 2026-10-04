---
title: "F8-D-01 — Conciliar decisiones y contratos SRC-06"
tags: [zontes, lote, f8]
status: planificado
fase: F8
frente: Core
updated: 2026-10-03
---

# F8-D-01 — Conciliar decisiones y contratos SRC-06

**Estado:** planificado por SRC-06; implementación y pruebas no ejecutadas. La aprobación de cambios de alcance y contratos se registra en [[02-Arquitectura/Impacto SRC-06 y decisiones F8]] antes de abrir el trabajo operativo.

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 1–5; REQ-25–28 |
| Objetivo | Registrar DEC-17/18/19 con autoridad de Usuario, definir la transición de comportamiento y versionar los contratos FE↔BE antes de editar producto. |
| Depende de | SRC-06; DEC-04/05/06/09/11/14/16; F1–F7 |
| Interfaz / referencia | UI-07/10/12/13/19/23/24 |
| Repositorio de implementación | Zontes-Core; rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [ ] DEC-17 resuelve importación frente a DEC-16, fuente de verdad, normalización de correo, conflictos y retención de archivos/reportes.
- [ ] DEC-18 resuelve vencimiento por asignación frente a DEC-06, grants de integración, datos históricos y corrección sin resta manual.
- [ ] DEC-19 delimita retirada de Tendencias, búsqueda/notificaciones y activos de Inicio; contratos con roles, errores e idempotencia quedan escritos.

## Verificación prevista

Revisión documental de matriz SRC-06 → REQ → DEC → tarea → prueba; aprobación de Usuario registrada en Decisiones técnicas. Sin pruebas de código en este lote. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
