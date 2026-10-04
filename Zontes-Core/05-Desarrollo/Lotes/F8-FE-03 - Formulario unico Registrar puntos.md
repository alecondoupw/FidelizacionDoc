---
title: "F8-FE-03 — Formulario unico Registrar puntos"
tags: [zontes, lote, f8]
status: planificado
fase: F8
frente: FE
updated: 2026-10-03
---

# F8-FE-03 — Formulario unico Registrar puntos

**Estado:** planificado por SRC-06; implementación y pruebas no ejecutadas. La aprobación de cambios de alcance y contratos se registra en [[02-Arquitectura/Impacto SRC-06 y decisiones F8]] antes de abrir el trabajo operativo.

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 3; REQ-26 |
| Objetivo | Reemplazar la pantalla actual por un único Ajuste de puntos que sólo suma y pide vencimiento por operación. |
| Depende de | F8-BE-03/04; DEC-18; F2-FE-02 |
| Interfaz / referencia | UI-24; A05/A06 sólo como estilo histórico |
| Repositorio de implementación | FE_REPO (Next.js); rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [ ] Campos: correo con búsqueda/nombre, marca vinculada, Puntos a sumar (>0), motivo y fecha obligatoria no pasada.
- [ ] La confirmación muestra cliente, marca, cantidad, motivo y vencimiento; botón final Registrar puntos y bloqueo de envío doble.
- [ ] Retira bloque Registrar evento, selector Evento, resta manual, Procesar ahora y textos de corregir con otro ajuste; usa el copy exacto de SRC-06 p. 3.

## Verificación prevista

Pruebas de formulario y doble clic; 1280/768/375 px, teclado, mensajes 4xx del BE y estados de envío. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
