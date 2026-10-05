---
title: "F9-FE-04 — Aplicar paleta en cliente y administrador"
tags: [zontes, lote, f9, frontend, diseno]
status: pendiente
fase: F9
frente: FE
updated: 2026-10-05
---

# F9-FE-04 — Aplicar paleta en cliente y administrador

| Campo | Contenido |
| --- | --- |
| Fuente | SRC-07/08; [[02-Arquitectura/Paleta Zontes propuesta F9]]; DEC-11/21 |
| Objetivo | Sustituir el índigo provisional por tokens Zontes aprobados y aplicarlos al shell, controles y estados de cliente/admin. |
| Repositorio | FE_REPO Next.js de [[05-Desarrollo/Entorno local]]; no instalar paquetes ni tomar activos externos por inferencia |
| Depende de | F9-D-01 y revisión de valores exactos de DEC-21 |
| Contrato | Sin cambio API; colores de marca en datos/leyendas y estados semánticos preservados. |
| Prueba | F9-T04: inventario de tokens/capturas de ambos roles, contraste y estados 1280/768/375 px. |

## Aceptación

- [ ] Tokens centralizados para fondo, superficie, borde, texto, acento, foco y estados; sin hexadecimales de tema dispersos en componentes.
- [ ] Sidebar, botones, enlaces, inputs, tarjetas, tablas, banners, modales y avisos coherentes en cliente y admin; hover/focus/disabled/loading/error legibles.
- [ ] Texto/fondo con contraste al menos WCAG AA (4,5:1 texto normal y 3:1 texto grande/componentes); foco visible y pruebas con teclado. No poner texto blanco sobre lima.
- [ ] Kiden/NIU/Zontes siguen distinguiéndose en saldo, gráficos y publicaciones; probar alto contraste y las tres anchuras. No copiar logotipo, foto o fuente del sitio sin autorización de activos (DEC-11). Las imágenes específicas R02/R03/R04 provistas por Usuario en SRC-09 se integran en F9-FE-03/06 sin recolorarlas ni filtrar los logos.

**Índice:** [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]].
