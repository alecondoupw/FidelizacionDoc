---
title: "F8-BE-04 — Vencer remanente automaticamente"
tags: [zontes, lote, f8]
status: verificado
fase: F8
frente: BE
updated: 2026-10-04
---

# F8-BE-04 — Vencer remanente automaticamente

**Estado (2026-10-04):** Cada lote vence en su propia fecha; el cron diario (F7) y la consulta del saldo vencen sólo el remanente, sin repetir. La configuración por marca se retiró sin tocar los lotes existentes, que conservan su fecha. Evidencia en [[05-Desarrollo/Testing]] «Corridas F8».

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 3; REQ-26 |
| Objetivo | Hacer indisponible al final del día Bolivia el remanente de cada asignación y reflejarlo en historial sin doble descuento. |
| Depende de | F8-BE-03; F2-BE-03; F3-BE-02; DEC-18 |
| Interfaz / referencia | UI-03/13/14/20 como consumidores |
| Repositorio de implementación | BE_REPO (Express); rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [x] El vencimiento usa la fecha propia de cada lote; canjes consumen lotes según política vigente y sólo vence el remanente.
- [x] La ejecución programada y la lectura/reconciliación son idempotentes; la UI no depende de Procesar ahora.
- [x] Lotes históricos conservan su fecha original; transición/migración se verifica antes de cambiar o retirar configuración por marca. (sin migración: no se modifican lotes ni movimientos; la colección `vigencias` queda como histórico sin uso).

## Verificación prevista

Pruebas T-EXP/T-HISTORY/T-BRAND: mismo día, cruce de medianoche Bolivia, consumo parcial, concurrencia y doble ejecución. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
