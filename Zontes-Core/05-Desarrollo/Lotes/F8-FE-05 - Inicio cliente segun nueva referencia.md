---
title: "F8-FE-05 — Inicio cliente segun nueva referencia"
tags: [zontes, lote, f8]
status: planificado
fase: F8
frente: FE
updated: 2026-10-03
---

# F8-FE-05 — Inicio cliente segun nueva referencia

**Estado:** planificado por SRC-06; implementación y pruebas no ejecutadas. La aprobación de cambios de alcance y contratos se registra en [[02-Arquitectura/Impacto SRC-06 y decisiones F8]] antes de abrir el trabajo operativo.

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 4–5; REQ-28 |
| Objetivo | Componer Inicio con la nueva jerarquía visual y datos autorizados de la sesión, sin copiar valores ilustrativos. |
| Depende de | F8-D-01/DEC-19; F2-FE-01; F6-FE-01 |
| Interfaz / referencia | UI-13 · [[09-Entradas/Referencias UI 2026-10-03/SRC-06-inicio-cliente.png|SRC-06 p. 4]] + [[09-Entradas/Referencias UI 2026-10-02/Cliente/C08-inicio-cliente.jpeg|C08]] |
| Repositorio de implementación | FE_REPO (Next.js); rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [ ] Sidebar/header, saludo/fecha, búsqueda, notificaciones/perfil, banner con Explorar catálogo, puntos por marca, vencimientos, accesos y Mis marcas siguen SRC-06.
- [ ] Total de puntos sólo informativo; cada marca conserva saldo y canjes propios; Puntos por vencer identifica marca y fecha reales, o estado vacío claro.
- [ ] Cómo ganar puntos muestra sólo reglas activas; Gestionar marcas no vincula por selección; contempla sin marcas/puntos/movimientos y adapta 1280/768/375 px.

## Verificación prevista

Pruebas de componentes/contrato, visual con imagen preservada, teclado/foco, datos sintéticos y estados vacíos/error. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
