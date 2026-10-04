---
title: "F2-BE-02 — Ledger idempotente y transacciones de otorgamiento"
tags: [zontes, lote, f2, backend]
status: verificado-con-recorrido-parcial
fase: F2
frente: BE
bloqueos: []
updated: 2026-10-03
---

# F2-BE-02 — Ledger idempotente y transacciones de otorgamiento

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: libro de lotes con idempotencia origen + id externo (DEC-05), transacciones, saldo materializado conciliable, ajustes (DEC-14) y API de integración con clave. Evidencia en [[05-Desarrollo/Testing]] «Corridas F2». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F2-BE-02 · F2 — Motor de puntos · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Un evento autorizado (origen + ID) busca la regla activa exacta y, en una transacción, registra evento, movimiento y fecha de vencimiento; el saldo por marca se deriva de movimientos y es reconciliable. |
| Fuente y página | SRC-01 p. 1; SRC-02 pp. 4–5, 14 (obs. 3–4); SRC-03 p. 12 (obs. 3) · REQ-07, REQ-10, REQ-20 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE). |
| Reglas y decisiones | RN-05, RN-06 · ADR-06 · [[04-Reglas-de-negocio/Ciclo de puntos y canjes]] · **DEC-05 abierta** (emisor, autenticidad, ID estable, reintentos) · **DEC-06** (lotes) · **DEC-14** (corrección) · DEC-02 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`: módulos de eventos y movimientos. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-03 entrada de eventos e I-04 saldo/movimientos; idempotencia por origen+ID. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F2-BE-01 - Reglas de puntos por marca y evento\|F2-BE-01]]; DEC-05/06/14; emulador Firestore autorizado para concurrencia. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-POINTS, T-HISTORY, T-BRAND · pruebas de concurrencia en emulador · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real); recorrido integrado parcial (F2-T08)** · 2026-10-03 |

## Aceptación

- [ ] Mismo origen+ID enviado dos veces → un solo movimiento.
- [ ] Regla inactiva o inexistente → no otorga y queda trazado.
- [ ] Eventos concurrentes conservan saldo correcto y aislamiento por marca.
- [ ] Una corrección crea un movimiento nuevo; nunca borra historia.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
