---
title: "F1-BE-02 — Bootstrap del administrador inicial"
tags: [zontes, lote, f1, backend]
status: implementado-sin-integracion
fase: F1
frente: BE
bloqueos: [entorno-firebase]
updated: 2026-10-03
---

# F1-BE-02 — Bootstrap del administrador inicial

Lote ejecutable creado tras la puerta F0 con [[05-Desarrollo/Plantilla de lote de trabajo]]. **Resultado 2026-10-03:** Implementado: `bootstrapAdministrador` + comando `npm run admin:bootstrap`. Probado con dobles: crea una vez, es idempotente, rechaza un segundo admin y nunca promueve a un cliente. **Pendiente:** que Paulo lo ejecute en el proyecto de desarrollo. Evidencia en [[05-Desarrollo/Testing]] «Corridas F1». Índice: [[05-Desarrollo/Lotes F1-F7 - indice]].

| Campo | Contenido |
| --- | --- |
| ID / fase / frente | F1-BE-02 · F1 — Identidad y vínculo · BE · [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Existe un procedimiento seguro e idempotente para precrear el administrador inicial, sin ningún endpoint público de registro admin; los admins posteriores sólo los crea un admin (F4-BE-01). |
| Fuente y página | SRC-02 pp. 1–3 · REQ-02 · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | No aplica. |
| Reglas y decisiones | RN-01 · ADR-03 · **DEC-03 abierta** (mecanismo y custodio del acceso) · DEC-02 · [[04-Reglas-de-negocio/_Indice de reglas]] · [[02-Arquitectura/Decisiones pendientes]] |
| Responsable y rutas | Responsable: por asignar por Paulo (DEC-01 no fijó responsables). Ejecutor sugerido: agente BE. BE_REPO `FidelizacionBackend`: script de operación (propuesta `scripts/`), sin ruta HTTP. Rutas absolutas en [[05-Desarrollo/Entorno local]]. |
| Contrato FE↔BE | Sin API pública. Procedimiento documentado para el manual de despliegue (F7-BE-02). · [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]]; DEC-02; DEC-03. |
| Aceptación | Ver lista siguiente. |
| Prueba y evidencia | T-ROLE · prueba del script contra emulador/proyecto autorizado · `npm run check` · resultados en [[05-Desarrollo/Testing]] con fecha, revisión FE/BE y datos sintéticos |
| Estado | **Implementado y probado con dobles; integración con Firebase real pendiente (F1-I-01)** · 2026-10-03 |

## Aceptación

- [ ] No existe ruta HTTP que cree o eleve un admin sin token de admin activo.
- [ ] Ejecutar el procedimiento dos veces no duplica el admin.
- [ ] Queda un evento de auditoría con actor `bootstrap`, fecha y hora.
- [ ] Un cliente no puede convertirse en admin por ningún flujo.
- [ ] Las credenciales del admin inicial nunca se escriben en Git ni en el Core.
- [ ] Positivos y negativos ejecutados; `npm run check` en el o los repos tocados; evidencia y estado actualizados en [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

Cierre según [[05-Desarrollo/Criterio de terminado]]. Mientras un bloqueo siga abierto, el lote no está listo para implementar; una respuesta de Paulo se registra antes en [[02-Arquitectura/Decisiones tecnicas]].
