---
title: "F8-I-04 — Datos y responsive de Inicio cliente"
tags: [zontes, lote, f8]
status: verificado-con-salvedades
fase: F8
frente: Integración
updated: 2026-10-04
---

# F8-I-04 — Datos y responsive de Inicio cliente

**Estado (2026-10-04):** Revisado con la sesión de cliente de Usuario: datos reales, buscador, avisos y accesos; 1280/768/375 px sin desborde ni controles sin nombre. Diferencias con la imagen: sin fotos ni logotipos (DEC-11), iniciales en lugar de logotipo, saludo neutro «Hola de nuevo». Salvedad: la cuenta de prueba tenía 0 puntos, así que el vencimiento con datos se probó sólo en componentes. Evidencia en [[05-Desarrollo/Testing]] «Corridas F8».

| Campo | Contenido |
| --- | --- |
| Fuente | [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 4–5; REQ-28 |
| Objetivo | Cotejar Inicio real contra SRC-06 y probar navegación y datos con cliente sin marcas y con 1–3 marcas. |
| Depende de | F8-FE-05; F8-I-01/02; F1-FE-02; F3-FE-01 |
| Interfaz / referencia | UI-13/17/03/05/15/14/18 |
| Repositorio de implementación | FE_REPO + BE_REPO, con un único integrador; rutas en [[05-Desarrollo/Entorno local]] |
| Contrato | Roles, request/response, errores e idempotencia deben versionarse antes de programar; ver [[02-Arquitectura/Contratos de integracion por flujo]] |
| Evidencia futura | [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]]; revisión de código/entorno identificada |

## Aceptación

- [x] Saldo total coincide con suma informativa de marcas, pero ningún canje cruza marca; vencimiento y reglas coinciden con respuestas BE.
- [x] Buscador llega a catálogo y accesos rápidos a sus secciones; notificaciones siguen origen/estado acordado en DEC-19 sin inventar datos.
- [x] En escritorio/tablet/móvil no se oculta información esencial ni aparece scroll horizontal; se documentan diferencias justificadas con la imagen.

## Verificación prevista

Recorrido FE↔BE y capturas 1280/768/375 px; T-HOME/T-BRAND/T-UI con evidencia y límite. No marcar este lote verificado hasta registrar resultado real, límites y evidencia. Cierre según [[05-Desarrollo/Criterio de terminado]].

**Índice:** [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].
