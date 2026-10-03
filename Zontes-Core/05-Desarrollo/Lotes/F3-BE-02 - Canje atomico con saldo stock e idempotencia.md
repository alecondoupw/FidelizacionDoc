---
title: "F3-BE-02 — Canje atomico con saldo stock e idempotencia"
tags: [zontes, lote, f3, backend]
status: verificado-con-recorrido-parcial
fase: F3
frente: BE
bloqueos: []
updated: 2026-10-03
---

# F3-BE-02 — Canje atomico con saldo stock e idempotencia

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: `POST /canjes` transaccional con idempotencia por `idSolicitud`, stock por variante, saldo y lotes por vencimiento más próximo; concurrencia de la última unidad verificada contra Firestore real. Evidencia en [[05-Desarrollo/Testing]] «Corridas F3». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F3-BE-02 · F3 — Beneficios y canje · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Un canje valida saldo y disponibilidad y, en una transacción, descuenta puntos, ajusta stock y registra canje y movimiento; un reintento con la misma clave no duplica. |
| Fuente y página | SRC-02 p. 14 (obs. 3–4); SRC-03 pp. 7–9, 12 (obs. 3) · REQ-12, REQ-20 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE). |
| Reglas y decisiones | RN-08 · ADR-06 · **DEC-07 abierta** · DEC-06 (orden de consumo de lotes) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`: módulo de canjes. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-05: solicitud de canje con clave de idempotencia; 409 saldo/stock insuficiente. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F2-BE-02 - Ledger idempotente y transacciones de otorgamiento\|F2-BE-02]], [[05-Desarrollo/Lotes/F3-BE-01 - Catalogo de beneficios por marca\|F3-BE-01]]; DEC-06/07. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-REDEEM, T-BRAND · concurrencia en emulador · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real); recorrido integrado parcial (F3-T08)** · 2026-10-03 |

## Aceptación

- [ ] Saldo o stock insuficiente → rechazo sin efectos parciales.
- [ ] Dos canjes concurrentes nunca dejan saldo negativo ni entregan dos veces.
- [ ] El canje aparece en saldo, historial y Mis canjes con la misma fuente.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
