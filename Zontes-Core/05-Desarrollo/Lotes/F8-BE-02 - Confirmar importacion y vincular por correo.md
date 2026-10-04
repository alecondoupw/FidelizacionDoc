---
title: "F8-BE-02 — Confirmar importacion y vincular por correo"
tags: [zontes, lote, f8]
status: planificado
fase: F8
frente: BE
updated: 2026-10-03
---

# F8-BE-02 — Confirmar importacion y vincular por correo

**Estado:** planificado por SRC-06; implementación y pruebas no ejecutadas. La aprobación de cambios de alcance y contratos se registra en [[02-Arquitectura/Impacto SRC-06 y decisiones F8]] antes de abrir el trabajo operativo.

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 1–2; REQ-25 |
| Objetivo | Confirmar sólo filas válidas con cuenta cliente única por correo verificado, marcas acumulativas e idempotencia en reimportación. |
| Depende de | F8-BE-01; F1-BE-03; F4-BE-02; DEC-17 |
| Interfaz / referencia | UI-23 y UI-07; consumidor UI-17 |
| Repositorio de implementación | BE_REPO (Express); rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [ ] Importar una segunda o tercera marca agrega asociación sin borrar las anteriores; repetir el archivo no duplica cuentas, filas ni vínculos ni sobrescribe conflictos.
- [ ] Una cuenta ya verificada se vincula; sin cuenta verificada queda pendiente; coincidencias ambiguas se aíslan para revisión y jamás se convierten en administradores.
- [ ] Entrega reporte descargable y auditable con importados, vinculados, pendientes, duplicados y errores; explica que vinculados pueden estar dentro de importados.

## Verificación prevista

Pruebas transaccionales con datos sintéticos: 1/2/3 marcas, reimportación, carrera concurrente, correo no verificado, ambigüedad y aislamiento de saldo. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
