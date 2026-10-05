---
title: "F9-I-01 — Regresión visual y funcional de ambas vistas"
tags: [zontes, lote, f9, integracion]
status: pendiente
fase: F9
frente: integracion
updated: 2026-10-05
---

# F9-I-01 — Regresión visual y funcional de ambas vistas

| Campo | Contenido |
| --- | --- |
| Fuente | SRC-07/08/09; UI-02/13/17/18/28 y shell cliente/admin; [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]] |
| Objetivo | Confirmar que los cambios F9 son reales, consistentes, responsive y no rompen permisos ni datos existentes. |
| Repositorio | FE_REPO; BE_REPO sólo lectura/pruebas de contrato si se necesita; evidencia en `Zontes-Core/` |
| Depende de | F9-FE-01…06 |
| Prueba | F9-T01…T08 con revisión FE identificada, capturas y resultado por rol/ancho. |

## Aceptación

- [ ] Cliente: Inicio, Mis marcas, Información de cuenta y Novedades cumplen el texto/controles solicitados; admin: wordmark «Zontes» y paleta coherente. R02 se ve en el hero, R03 en ingreso cliente y R04 en crear cuenta; R01 sólo guía composición. Registrar captura real de 1280/768/375 px por superficie afectada.
- [ ] Recorrer CTA y sidebar Novedades, catálogo, saldo, marcas, perfil y sesión; comprobar cliente sin marcas y con varias marcas, y rechazo de marca ajena.
- [ ] Verificar foco, orden de tabulación, nombres accesibles, contraste, targets táctiles, carga/vacío/error y ausencia de scroll horizontal de página.
- [ ] Ejecutar check/smoke FE y las pruebas de contrato BE pertinentes; registrar comandos, revisiones y límites en [[05-Desarrollo/Testing]]. Actualizar [[07-Manuales/Manual de usuario]], [[07-Manuales/Guion de demostracion]], [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]] tras pruebas.

**Índice:** [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]]. No cerrar F9 con sólo revisión documental.
