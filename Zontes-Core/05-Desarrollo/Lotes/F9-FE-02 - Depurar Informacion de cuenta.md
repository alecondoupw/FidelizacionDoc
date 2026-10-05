---
title: "F9-FE-02 — Depurar Información de cuenta"
tags: [zontes, lote, f9, frontend]
status: pendiente
fase: F9
frente: FE
updated: 2026-10-05
---

# F9-FE-02 — Depurar Información de cuenta

| Campo | Contenido |
| --- | --- |
| Fuente | SRC-07, dos pedidos sobre «Información de cuenta»; C03/UI-18; DEC-04/08 |
| Objetivo | Retirar en la cuenta del cliente el bloque de «vínculo con clientes existentes» y la información de marca; dejar los datos de cuenta y acciones permitidas. |
| Repositorio | FE_REPO Next.js de [[05-Desarrollo/Entorno local]]; BE_REPO sin cambio previsto |
| Depende de | F9-D-01; F1-FE-03/F4-FE-03 existentes |
| Contrato | Identidad y campos editables del cliente según `/me` y DEC-08. El estado de vinculación sigue siendo dato de autorización, aunque no se exponga en esta vista. |
| Prueba | F9-T02: cliente vinculado/no vinculado, edición de nombre, cambio de contraseña, 1280/768/375 px. |

## Aceptación

- [ ] UI-18 no muestra sección, explicación ni enlace de «vínculo con clientes existentes»; tampoco muestra chips, tarjetas o detalles de marcas dentro de «Información de cuenta».
- [ ] Nombre/correo, edición permitida, seguridad de sesión y mensajes de error siguen claros; la eliminación visual no expone ni altera datos de otros clientes.
- [ ] Mis marcas (UI-17) conserva la consulta de marcas vinculadas como lugar apropiado; probar estados vacío/carga/error y foco.

**Índice:** [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]].
