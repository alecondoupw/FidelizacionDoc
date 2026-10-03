---
title: "F1-FE-02 — Mis marcas cliente"
tags: [zontes, lote, f1, frontend]
status: verificado-con-salvedades
fase: F1
frente: FE
bloqueos: []
updated: 2026-10-03
---

# F1-FE-02 — Mis marcas cliente

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: `/marcas` con marcas de `/me`, marca activa local (ADR-12), estado vacío y «Vincular nueva marca» deshabilitado (DEC-04). Sin saldos (F2) ni catálogo (F3). Evidencia en [[05-Desarrollo/Testing]] «Corridas F1». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F1-FE-02 · F1 — Identidad y vínculo · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | El cliente ve sólo las marcas vinculadas que confirma el BE, elige la marca activa y accede a su catálogo; el saldo por marca se integra en F2. |
| Fuente y página | SRC-03 pp. 4–5, 8 · REQ-06 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-17 · C02 |
| Reglas y decisiones | RN-09 · **DEC-04 abierta** (qué hace «Vincular nueva marca») · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente FE. FE_REPO `FidelizacionFronted`: vista de marcas del área cliente. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-01 `GET /api/v1/me` → `marcas` (propuesto). · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]], [[05-Desarrollo/Lotes/F1-FE-01 - Login registro y verificacion cliente y login admin\|F1-FE-01]]. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-BRAND, T-UI · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Verificado con salvedades (2026-10-03): F1-T01…T11; salvedades: cambio de correo sin probar (política abierta en DEC-04; se cubre en F4-BE-02) y revisión visual de las vistas protegidas en tres tamaños sólo en pruebas de componentes y en el recorrido de Paulo, sin capturas registradas** · 2026-10-03 |

## Aceptación

- [ ] La lista coincide exactamente con la respuesta del BE; sin marcas → estado vacío explicativo.
- [ ] El botón «Vincular nueva marca» no crea asociaciones manuales mientras no exista contrato (DEC-04).
- [ ] Estados de carga, vacío, error, sin permiso y éxito; confirmación en acciones irreversibles.
- [ ] Escritorio, tablet y móvil sin scroll horizontal de página; teclado, foco visible, contraste y textos accesibles.
- [ ] Cotejo con la referencia asignada y con [[02-Arquitectura/Guia visual y criterios anti slop]]; los valores del mockup no se copian como datos.
- [ ] Todo dato mostrado proviene de la respuesta del BE; ninguna regla sensible se calcula en el navegador.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
