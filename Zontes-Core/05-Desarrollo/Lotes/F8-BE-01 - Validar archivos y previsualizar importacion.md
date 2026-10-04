---
title: "F8-BE-01 — Validar archivos y previsualizar importacion"
tags: [zontes, lote, f8]
status: verificado
fase: F8
frente: BE
updated: 2026-10-04
---

# F8-BE-01 — Validar archivos y previsualizar importacion

**Estado (2026-10-04):** Implementado (`src/importacion/`, `POST /admin/importaciones/vista-previa`) y verificado con dobles y contra Firestore real (F8-T01/T02); mutaciones detectadas (F8-T03). Evidencia en [[05-Desarrollo/Testing]] «Corridas F8».

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

- [x] Rechaza marca ausente, formato inválido y columnas nombre/correo faltantes; informa fila y motivo para obligatorios vacíos o correo inválido.
- [x] Distingue repetición dentro de la misma marca de correo ya presente en otra marca; muestra asociaciones existentes/nuevas y casos ambiguos sin resolverlos automáticamente.
- [x] La vista previa puede cancelarse; no escribe cuentas Firebase, vínculos ni saldos y limita tamaño/volumen según contrato autorizado.

## Verificación prevista

Unitarias de parseo CSV/XLSX, encabezados, filas inválidas y colisiones; prueba de ausencia de escrituras. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
