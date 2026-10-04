---
title: "F8-I-02 — Conciliar suma canje y vencimiento"
tags: [zontes, lote, f8]
status: planificado
fase: F8
frente: Integración
updated: 2026-10-03
---

# F8-I-02 — Conciliar suma canje y vencimiento

**Estado:** planificado por SRC-06; implementación y pruebas no ejecutadas. La aprobación de cambios de alcance y contratos se registra en [[02-Arquitectura/Impacto SRC-06 y decisiones F8]] antes de abrir el trabajo operativo.

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 3, 5; REQ-26/28 |
| Objetivo | Recorrer asignación manual, saldo, canje parcial, vencimiento e historial en FE↔BE. |
| Depende de | F8-BE-03/04; F8-FE-03; F2-FE-01; F3-BE-02 |
| Interfaz / referencia | UI-24/03/13/14/20 |
| Repositorio de implementación | FE_REPO + BE_REPO, con un único integrador; rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [ ] Una suma aparece en saldo, Puntos por vencer y movimientos de la marca correcta con fecha del BE.
- [ ] Tras canje y vencimiento sólo se descuenta remanente una vez; repetir confirmación/proceso no altera el resultado.
- [ ] No existe resta manual desde la pantalla; descuentos legítimos por canje o vencimiento siguen visibles y reconciliables.

## Verificación prevista

Recorrido integrado con reloj controlado y datos sintéticos; T-GRANT-DATE/T-EXP/T-HISTORY/T-POINTS. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
