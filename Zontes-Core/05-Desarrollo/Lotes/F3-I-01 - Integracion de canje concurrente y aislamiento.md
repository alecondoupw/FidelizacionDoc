---
title: "F3-I-01 — Integracion de canje concurrente y aislamiento"
tags: [zontes, lote, f3, integracion]
status: verificado-con-recorrido-parcial
fase: F3
frente: Integración
bloqueos: []
updated: 2026-10-03
---

# F3-I-01 — Integracion de canje concurrente y aislamiento

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Verificado con dobles y contra Firestore real (canje concurrente, aislamiento por marca y propietario); falta el recorrido FE↔BE en navegador por Usuario. Evidencia en [[05-Desarrollo/Testing]] «Corridas F3». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F3-I-01 · F3 — Beneficios y canje · Integración · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Demostrar FE↔BE canje feliz, rechazos seguros, concurrencia y aislamiento entre marcas. |
| Fuente y página | SRC-01 p. 1; SRC-03 pp. 6–9, 12 · REQ-11, REQ-12 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | UI-05, UI-15, UI-16 |
| Reglas y decisiones | RN-08, RN-09 · DEC-07 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Integrador único. FE_REPO `FidelizacionFronted` y BE_REPO `FidelizacionBackend`. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-05 aprobado y versionado. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F3-BE-01 - Catalogo de beneficios por marca\|F3-BE-01]]/02/03, [[05-Desarrollo/Lotes/F3-FE-01 - Catalogo canje mis canjes y comprobante cliente\|F3-FE-01]]. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-REDEEM, T-BRAND · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real); recorrido integrado parcial (F3-T08)** · 2026-10-03 |

## Aceptación

- [ ] Dos canjes simultáneos del último stock: uno se rechaza.
- [ ] Un cliente de Zontes no ve ni canjea beneficios de Kiden/NIU sin vínculo.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
