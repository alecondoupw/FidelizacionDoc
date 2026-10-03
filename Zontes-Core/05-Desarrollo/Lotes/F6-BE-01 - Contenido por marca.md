---
title: "F6-BE-01 — Contenido por marca"
tags: [zontes, lote, f6, backend]
status: verificado
fase: F6
frente: BE
bloqueos: []
updated: 2026-10-03
---

# F6-BE-01 — Contenido por marca

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: colección `contenidos/{id}` con publicación por marca (DEC-10), rutas cliente `/contenidos` y admin `/admin/contenidos` con auditoría; el cliente sólo recibe publicaciones activas, en ventana y de sus marcas. Sin archivos (no hay activos autorizados; DEC-11). Evidencia en [[05-Desarrollo/Testing]] «Corridas F6». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F6-BE-01 · F6 — Contenido y calidad visual · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | El admin crea, edita, activa/desactiva y elimina contenido de una marca; el cliente sólo recibe contenido activo de sus marcas. |
| Fuente y página | SRC-01 p. 1; SRC-02 p. 7 · REQ-17 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE); consumidor UI-12. |
| Reglas y decisiones | RN-09 · DEC-10 resuelta · DEC-11 parcial (sin archivos) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`; Storage sólo con archivos autorizados. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-08 implementado: [[02-Arquitectura/Contrato API v0 - F0]] §11. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]]; DEC-10/11. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-BRAND, T-AUTHZ · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real + interfaz real F6-T07/T08)** · 2026-10-03 |
## Aceptación

- [x] Contenido inactivo o de otra marca nunca llega al cliente.
- [x] Archivos privados sólo con acceso autorizado. No aplica en F6: no se suben archivos (DEC-10/11).
- [x] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
