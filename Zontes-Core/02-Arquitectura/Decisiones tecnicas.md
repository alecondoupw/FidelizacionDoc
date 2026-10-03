---
title: "Decisiones técnicas y procedencia"
tags: [zontes]
status: planificado
updated: 2026-10-03
---

# Decisiones técnicas y procedencia

| ID | Estado | Contenido y autoridad | Revisar si |
| --- | --- | --- | --- |
| ADR-01 | Base documental de desarrollo SRC-02 pp. 11–15 y SRC-03 pp. 11–13; Paulo indicó usar los PDF como información concreta | Next.js/TypeScript para interfaz cliente+admin; Express/TypeScript concentra API y reglas sensibles. La plantilla Next/Nest **no** selecciona NestJS. No implica código instalado. | Paulo cambia stack explícitamente |
| ADR-02 | Base documental de desarrollo SRC-02/03 | Firebase Authentication, Cloud Firestore, Firebase Storage si se usan archivos; Admin SDK sólo en Express. No implica proyecto o credenciales disponibles. | DEC-02/03 sobre acceso, costes y proyecto |
| ADR-03 | Regla consolidada SRC-02 pp.1,9–10 | Admin inicial precreado; nuevos admins sólo por admin; sin alta pública ni cliente→admin. | No cambiar por facilidad de demo |
| ADR-04 | Regla consolidada SRC-02 pp.2,9–10 | Vincular cliente previo únicamente por correo normalizado; no usar nombre/teléfono como segundo criterio. | Resolver duplicados y cambios de correo DEC-04 |
| ADR-05 | Regla consolidada SRC-02 pp.4,9–10 | Regla de puntos: evento+marca+puntos+estado; sin condición; cambios sólo a eventos futuros. | Definir vigencia y origen evento DEC-05/06 |
| ADR-06 | Diseño propuesto | Movimientos auditables, operación crítica idempotente/atómica en BE, saldo derivado o materializado reconciliable; fechas oficiales en BE. | Evidencia de concurrencia, canje y vencimiento |
| ADR-07 | Sistema visual documentado SRC-02 pp.8–9 | Dashboard SaaS plano de densidad media, tokens base; personalizar componentes, sin degradados/emoji. | Vistas futuras de Paulo y pruebas de accesibilidad |
| DEC-01 → resuelta | **Decisión de Paulo, 2026-10-03** | FE en `C:\Users\aleco\Documents\Fidelizacion\FidelizacionFronted`, BE en `C:\Users\aleco\Documents\Fidelizacion\FidelizacionBackend`; contenían sólo README; **dos repositorios Git independientes** (`alecondoupw/FidelizacionFronted`, `alecondoupw/FidelizacionBackend`). Responsables por repo no indicados. | Cambio de organización o de host |
| ADR-08 | Elegido por el agente en F0 por encargo de Paulo («selecciona un solo estándar»), dentro de la opción de SRC-02 p. 13 / SRC-03 p. 12; revisable por Paulo | **`fetch` nativo** como único estándar HTTP, encapsulado en `src/lib/api` del FE (errores del contrato, timeout, Bearer). Motivo: SRC-02 «fetch reduce dependencias»; SRC-03 «fetch ya viene integrado y suele ser suficiente»; interceptores se cubren con el cliente propio. Axios prohibido por ESLint en ambos repos. | Si un requisito real necesita algo que el cliente propio no resuelva |
| ADR-09 | Elegido por el agente en F0 con documentación oficial (operativo, sin cambio de stack); revisable por Paulo | Node 24 LTS + npm 11 + `package-lock.json`; TypeScript 5.9 / ESLint 9 en ambos repos (plantilla oficial `create-next-app` 16.3.8 y límite `typescript-eslint` <6.1); Express 5; Vitest en ambos; shadcn/ui estilo `base-nova` (opción por defecto de la CLI, sustituible al aplicar DEC-11). Detalle en [[05-Desarrollo/Entorno local]]. | Actualización mayor planificada |
| ADR-10 | Implementado por el agente en F0 (salida F0-I-02); revisable por Paulo | Contrato API v0: prefijo `/api/v1`, sobre de error único, fechas ISO 8601 UTC, Bearer sin cookies, CORS por lista, `X-Request-Id`. Ver [[02-Arquitectura/Contrato API v0 - F0]]. I-01/I-02 quedan como propuesta. | Revisión de contrato en F1 |

[[02-Arquitectura/Base tecnica documentada]] clasifica el stack principal, herramientas UI y alternativas explícitas del anexo. El formato de exportación y la generación del comprobante dependen del contrato y decisiones de fase.
