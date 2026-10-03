---
title: "F3-FE-01 — Catalogo canje mis canjes y comprobante cliente"
tags: [zontes, lote, f3, frontend]
status: verificado-con-recorrido-parcial
fase: F3
frente: FE
bloqueos: []
updated: 2026-10-03
---

# F3-FE-01 — Catalogo canje mis canjes y comprobante cliente

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: `/catalogo`, `/catalogo/[id]` (confirmación y resultado), `/canjes`, `/canjes/[codigo]` (QR y descarga), «Ver beneficios» en Mis marcas, menú «Más» en móvil; admin `/admin/beneficios` (UI-25) y `/admin/canjes` (UI-26), propuestas sin mockup. Evidencia en [[05-Desarrollo/Testing]] «Corridas F3». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F3-FE-01 · F3 — Beneficios y canje · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | El cliente explora el catálogo de su marca, ve el detalle, confirma un canje, ve el resultado real y consulta Mis canjes y su comprobante. |
| Fuente y página | SRC-03 pp. 6–9 · REQ-11, REQ-12, REQ-18 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-05 · C06, C05 · UI-15 · C04 · UI-16 (sin imagen aislada) |
| Reglas y decisiones | RN-08, RN-09 · DEC-07 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`: área cliente. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-05 (F3-BE-01/02/03). · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F3-BE-01 - Catalogo de beneficios por marca\|F3-BE-01]]/02/03, [[05-Desarrollo/Lotes/F2-FE-01 - Inicio saldo e historial cliente\|F2-FE-01]]. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-REDEEM, T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real); recorrido integrado parcial (F3-T08)** · 2026-10-03 |

## Aceptación

- [ ] C04/C05 se separan en estados o rutas reales; el éxito sólo aparece tras respuesta OK del BE.
- [ ] Saldo insuficiente o sin stock muestra el motivo devuelto por el BE.
- [ ] Tras canjear, saldo e historial se refrescan desde el servidor.
- [ ] Estados de carga, vacío, error, sin permiso y éxito; confirmación en acciones irreversibles.
- [ ] Escritorio, tablet y móvil sin scroll horizontal de página; teclado, foco visible, contraste y textos accesibles.
- [ ] Cotejo con la referencia asignada y con [[02-Arquitectura/Guia visual y criterios anti slop]]; los valores del mockup no se copian como datos.
- [ ] Todo dato mostrado proviene de la respuesta del BE; ninguna regla sensible se calcula en el navegador.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
