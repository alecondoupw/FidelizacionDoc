---
title: "F4-FE-04 — Importacion CSV de clientes condicionada"
tags: [zontes, lote, f4, frontend]
status: condicionado
fase: F4
frente: FE
bloqueos: [DEC-16]
updated: 2026-10-03
---

# F4-FE-04 — Importacion CSV de clientes condicionada

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F4-FE-04 · F4 — Administración de identidades · FE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Sólo si Paulo aprueba DEC-16: carga CSV de clientes existentes con validación, deduplicación, errores por fila y auditoría. |
| Fuente y página | Ninguna en SRC-01/02/03; sólo el mockup A02 · relación con REQ-04 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-23 · A02 (propuesta visual) |
| Reglas y decisiones | **DEC-16 abierta**: fuera del alcance comprometido · RN-03 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). FE_REPO `FidelizacionFronted` y contrato BE condicionado. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | No existe; se define sólo si se aprueba. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | DEC-16; [[05-Desarrollo/Lotes/F4-BE-02 - Gestion de clientes y revinculacion\|F4-BE-02]]. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-LINK si se aprueba · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Condicionado: fuera de alcance hasta DEC-16** · 2026-10-03 |

## Aceptación

- [ ] No se implementa ni se presenta como requisito mientras DEC-16 esté abierta.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
