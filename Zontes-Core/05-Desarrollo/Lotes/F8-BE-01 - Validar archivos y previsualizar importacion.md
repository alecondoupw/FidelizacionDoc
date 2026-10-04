---
title: "F8-BE-01 — Validar archivos y previsualizar importacion"
tags: [zontes, lote, f8]
status: planificado
fase: F8
frente: BE
updated: 2026-10-03
---

# F8-BE-01 — Validar archivos y previsualizar importacion

**Estado:** planificado por SRC-06; implementación y pruebas no ejecutadas. La aprobación de cambios de alcance y contratos se registra en [[02-Arquitectura/Impacto SRC-06 y decisiones F8]] antes de abrir el trabajo operativo.

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 1–2; REQ-25 |
| Objetivo | Aceptar CSV o XLSX de una sola marca por operación y devolver vista previa determinista sin escribir clientes ni cuentas. |
| Depende de | F8-D-01 y DEC-17; F1-BE-03 |
| Interfaz / referencia | UI-23/A02 como consumidor |
| Repositorio de implementación | BE_REPO (Express); rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [ ] Rechaza marca ausente, formato inválido y columnas nombre/correo faltantes; informa fila y motivo para obligatorios vacíos o correo inválido.
- [ ] Distingue repetición dentro de la misma marca de correo ya presente en otra marca; muestra asociaciones existentes/nuevas y casos ambiguos sin resolverlos automáticamente.
- [ ] La vista previa puede cancelarse; no escribe cuentas Firebase, vínculos ni saldos y limita tamaño/volumen según contrato autorizado.

## Verificación prevista

Unitarias de parseo CSV/XLSX, encabezados, filas inválidas y colisiones; prueba de ausencia de escrituras. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
