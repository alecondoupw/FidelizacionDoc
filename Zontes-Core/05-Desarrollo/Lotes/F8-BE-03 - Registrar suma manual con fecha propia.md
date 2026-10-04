---
title: "F8-BE-03 — Registrar suma manual con fecha propia"
tags: [zontes, lote, f8]
status: planificado
fase: F8
frente: BE
updated: 2026-10-03
---

# F8-BE-03 — Registrar suma manual con fecha propia

**Estado:** planificado por SRC-06; implementación y pruebas no ejecutadas. La aprobación de cambios de alcance y contratos se registra en [[02-Arquitectura/Impacto SRC-06 y decisiones F8]] antes de abrir el trabajo operativo.

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 3; REQ-26 |
| Objetivo | Registrar asignación manual positiva con motivo y vencimiento elegido para ese lote, conservando ledger, actor e idempotencia. |
| Depende de | F8-D-01/DEC-18; F2-BE-02; DEC-05/14 |
| Interfaz / referencia | UI-24 como consumidor |
| Repositorio de implementación | BE_REPO (Express); rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [ ] El BE exige cliente por correo, marca vinculada, puntos > 0, motivo y fecha no anterior al día de registro en America/La_Paz; rechaza 0 y negativos.
- [ ] Cada operación guarda administrador, fecha, cliente, marca, cantidad, motivo y vencimiento propio; no cambia lotes previos ni mezcla marcas.
- [ ] Una confirmación repetida produce un solo movimiento; el contrato deja de permitir resta manual y documenta el destino del flujo de eventos/ajustes previo.

## Verificación prevista

Unitarias de zona horaria, fecha límite, rol, valores y reintentos; integración transaccional con ledger sintético. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
