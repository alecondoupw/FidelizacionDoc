---
title: "F3-BE-03 — Estados comprobante y reversa de canje"
tags: [zontes, lote, f3, backend]
status: bloqueado-por-decision
fase: F3
frente: BE
bloqueos: [DEC-07]
updated: 2026-10-03
---

# F3-BE-03 — Estados comprobante y reversa de canje

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **No iniciado.** Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F3-BE-03 · F3 — Beneficios y canje · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Cada canje tiene estados definidos y un comprobante o cupón con código trazable (QR si corresponde), visible sólo para su propietario; la reversa existe sólo si se decide. |
| Fuente y página | SRC-03 pp. 7–8, 13 (obs. 8); SRC-02 pp. 12, 15 (obs. 9) · REQ-12 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE); consumidor UI-15/16. |
| Reglas y decisiones | RN-08 · **DEC-07 abierta** (estados, cupón, vigencia, reversa, generación en FE o BE) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`; `@react-pdf/renderer` o generación en servidor según DEC-07. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-05: detalle de canje y comprobante del propietario. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F3-BE-02 - Canje atomico con saldo stock e idempotencia\|F3-BE-02]]; DEC-07. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-REDEEM, T-AUTHZ · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Bloqueado por decisión: DEC-07** · 2026-10-03 |

## Aceptación

- [ ] Otro cliente que pide el comprobante → 403/404 sin filtrar datos.
- [ ] El código del comprobante identifica un único canje.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
