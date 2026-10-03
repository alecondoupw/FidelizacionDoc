---
title: "F5-I-01 — Integracion y conciliacion de reportes"
tags: [zontes, lote, f5, integracion]
status: verificado
fase: F5
frente: Integración
bloqueos: []
updated: 2026-10-03
---

# F5-I-01 — Integracion y conciliacion de reportes

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Conciliación verificada con dobles y contra Firestore real (pantalla, archivo y libro coinciden con los movimientos); falta el recorrido FE↔BE en navegador por Paulo y reparar en el proyecto real los datos anteriores a F5 (F5-T06). Evidencia en [[05-Desarrollo/Testing]] «Corridas F5». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F5-I-01 · F5 — Observabilidad de negocio · Integración · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Conciliar cifras de pantalla y archivo con ledger y canjes, y comprobar comportamiento con volumen. |
| Fuente y página | SRC-02 pp. 5–7, 14 · REQ-15, REQ-16 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-08–UI-11, UI-20, UI-21 |
| Reglas y decisiones | RN-11 · DEC-09 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Integrador único. FE_REPO `FidelizacionFronted` y BE_REPO `FidelizacionBackend`. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-07 aprobado y versionado. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F5-BE-01 - Agregados y consultas de reportes\|F5-BE-01]]/02, [[05-Desarrollo/Lotes/F5-FE-01 - Dashboard actividad movimientos y canjes admin\|F5-FE-01]]/02/03. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-EXPORT · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real + recorrido integrado F5-T10)** · 2026-10-03 |

## Aceptación

- [ ] Cifras de dashboard = reporte = exportación para el mismo filtro.
- [ ] Volumen de prueba definido en DEC-09.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
