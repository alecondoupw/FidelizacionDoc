---
title: "F9-D-01 — Conciliar alcance visual y tokens"
tags: [zontes, lote, f9]
status: pendiente
fase: F9
frente: Core
updated: 2026-10-05
---

# F9-D-01 — Conciliar alcance visual y tokens

| Campo | Contenido |
| --- | --- |
| Fuente | SRC-07/08 en [[09-Entradas/Referencia web Zontes Bolivia 2026-10-05]]; SRC-09 en [[09-Entradas/Referencias UI 2026-10-05/Manifiesto de imagenes F9]]; DEC-11/19/22, ADR-12; C02/C03/C08 y A01–A13 históricos |
| Objetivo | Dejar trazable el nuevo objetivo de UI-13/17/18/28 y del shell admin/cliente; separar pedido aprobado de selección cromática propuesta. |
| Repositorio | Sólo `Zontes-Core/` en FidelizacionDoc |
| Depende de | Ningún lote F9; tomar como base el estado real documentado de F8 |
| Entregable | DEC-20 (alcance solicitado), DEC-21 (tokens propuestos), DEC-22 (asignación de imágenes), mapa y manifiesto actualizados, [[02-Arquitectura/Paleta Zontes propuesta F9]]. |
| Prueba | Revisión documental: cada petición SRC-07 tiene UI-ID, lote, criterio de aceptación y fuente; no atribuir ejecución. |

## Aceptación

- [ ] Confirmar en FE la ubicación y texto exacto de cada control, incluidas variantes móvil y admin; registrar diferencias con el mockup sin inventar una función nueva.
- [ ] Tratar «Ver novedades» del banner y «Novedades» del sidebar como dos puntos de entrada al mismo UI-28, sin otro acceso rápido duplicado en Inicio.
- [ ] Obtener revisión de la selección exacta de tokens de DEC-21 antes de reemplazar la línea provisional; mantener abierta la licencia de activos de DEC-11.
- [ ] Comprobar que ocultar bloques no equivale a borrar datos/contratos de vínculo, marcas o puntos.
- [ ] Validar en FE el slot del hero y de ambos formularios; usar R01 sólo como composición y R02/R03/R04 como imágenes asignadas. Registrar variantes móviles y evitar el copy de R01 que contradice DEC-20.

**Evidencia futura:** [[05-Desarrollo/Testing]] F9-D-01 y [[06-Estado/Bitacora]]. Índice: [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]].
