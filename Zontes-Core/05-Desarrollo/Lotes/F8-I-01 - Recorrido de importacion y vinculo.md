---
title: "F8-I-01 — Recorrido de importacion y vinculo"
tags: [zontes, lote, f8]
status: planificado
fase: F8
frente: Integración
updated: 2026-10-03
---

# F8-I-01 — Recorrido de importacion y vinculo

**Estado:** planificado por SRC-06; implementación y pruebas no ejecutadas. La aprobación de cambios de alcance y contratos se registra en [[02-Arquitectura/Impacto SRC-06 y decisiones F8]] antes de abrir el trabajo operativo.

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 1–2; REQ-25 |
| Objetivo | Demostrar el flujo archivo → preview → confirmación → registro con correo verificado → marcas y saldos correctos. |
| Depende de | F8-BE-01/02; F8-FE-01/02; F1-FE-01/02 |
| Interfaz / referencia | UI-23/07/17/02 |
| Repositorio de implementación | FE_REPO + BE_REPO, con un único integrador; rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [ ] Mismo correo en tres marcas termina en una cuenta con tres asociaciones y saldos aislados; repetición por marca queda señalada.
- [ ] Filas inválidas/ambiguas no se vinculan; cancelar no escribe; reintentar confirmación no duplica; métricas y reporte concilian.
- [ ] Importar nunca crea acceso o rol admin; el cliente pendiente se enlaza sólo tras verificar el mismo correo.

## Verificación prevista

Recorrido FE↔BE con datos sintéticos y revisiones identificadas; pruebas T-IMPORT/T-LINK/T-BRAND/T-AUTHZ y evidencia. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
