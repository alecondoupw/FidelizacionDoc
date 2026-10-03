---
title: "F1-BE-03 — Normalizacion de correo y vinculo legacy"
tags: [zontes, lote, f1, backend]
status: verificado-con-salvedades
fase: F1
frente: BE
bloqueos: []
updated: 2026-10-03
---

# F1-BE-03 — Normalizacion de correo y vinculo legacy

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: `POST /api/v1/clientes/registro` con normalización, correo verificado (ADR-11), adaptador legacy con doble sintético (DEC-04) y unicidad por correo en transacción. Probado con dobles. Evidencia en [[05-Desarrollo/Testing]] «Corridas F1». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F1-BE-03 · F1 — Identidad y vínculo · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Al registrarse un cliente, Express normaliza el correo, busca coincidencia exacta en la fuente existente autorizada y deja la cuenta vinculada (con sus marcas) o no vinculada, sin duplicar identidades por correo. |
| Fuente y página | SRC-02 p. 2; SRC-03 pp. 3–4 · REQ-04, REQ-05 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE). |
| Reglas y decisiones | RN-03, RN-09 · ADR-04 · **DEC-04 abierta y material** (API/esquema legacy, duplicados, cambio de correo, multiplicidad de marcas) · DEC-02 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`: módulo de clientes y adaptador de la fuente legacy detrás de una interfaz con doble de prueba. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-02 · `POST /api/v1/clientes/registro` **propuesto** en [[02-Arquitectura/Contrato API v0 - F0]] §5; 409 correo ya vinculado, 422 validación. Sólo campos que la fuente real entregue. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]]; DEC-04 (contrato de la fuente); acceso autorizado a la fuente o a un doble acordado. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-LINK, T-AUTHZ · unitarias de normalización + integración con doble/fuente autorizada · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Verificado con salvedades (2026-10-03): F1-T01…T11; salvedades: cambio de correo sin probar (política abierta en DEC-04; se cubre en F4-BE-02) y revisión visual de las vistas protegidas en tres tamaños sólo en pruebas de componentes y en el recorrido de Paulo, sin capturas registradas** · 2026-10-03 |

## Aceptación

- [ ] Correo con mayúsculas/espacios coincide tras normalización → vinculado con las marcas de la fuente.
- [ ] Sin coincidencia → no vinculado; no se crea vínculo manual.
- [ ] Correo ya registrado → 409; nunca dos cuentas de fidelización para el mismo correo.
- [ ] Nombre, teléfono o documento jamás se usan como criterio de vínculo.
- [ ] La respuesta no expone datos legacy no autorizados.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
