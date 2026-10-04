---
title: "F2-BE-03 — Vencimiento por marca y auditoria"
tags: [zontes, lote, f2, backend]
status: verificado-con-recorrido-parcial
fase: F2
frente: BE
bloqueos: []
updated: 2026-10-03
---

# F2-BE-03 — Vencimiento por marca y auditoria

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: vigencia por marca con historial, vencimiento America/La_Paz a fin de día (DEC-06), vencimiento perezoso al leer saldo y proceso reejecutable (`npm run puntos:vencer`, `POST /admin/vencimientos/procesar`). Programación periódica pendiente de DEC-13. Evidencia en [[05-Desarrollo/Testing]] «Corridas F2». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F2-BE-03 · F2 — Motor de puntos · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | La vigencia se configura por marca (días/meses/años, activación); el BE calcula el vencimiento al otorgar y un proceso reejecutable vence sólo puntos no consumidos, dejando movimiento; los cambios de configuración son prospectivos y auditados. |
| Fuente y página | SRC-01 p. 1; SRC-02 pp. 5, 14 (obs. 6) · REQ-09 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica (BE); consumidor UI-19. |
| Reglas y decisiones | RN-05, RN-07 · **DEC-06 abierta** (zona horaria, cálculo de calendario, orden de consumo, saldo parcial) · DEC-13 (dónde se ejecuta el proceso programado) · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Usuario (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`: módulo de vigencia y proceso de expiración. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | I-04; configuración admin de vigencia bajo `/api/v1/admin/` a fijar. · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F2-BE-02 - Ledger idempotente y transacciones de otorgamiento\|F2-BE-02]]; DEC-06; DEC-13 para la ejecución programada. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-EXP, T-HISTORY · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y verificado (dobles + Firestore real); recorrido integrado parcial (F2-T08)** · 2026-10-03 |

## Aceptación

- [ ] Bordes de calendario (fin de mes, año bisiesto) según DEC-06.
- [ ] Reejecutar la expiración no descuenta dos veces.
- [ ] Cambiar la vigencia no altera vencimientos ya calculados.
- [ ] Cada vencimiento genera movimiento visible en historial.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Usuario se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
