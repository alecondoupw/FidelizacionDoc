---
title: "Decisiones técnicas y procedencia"
tags: [zontes]
status: planificado
updated: 2026-10-02
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

[[02-Arquitectura/Base tecnica documentada]] clasifica el stack principal, herramientas UI y alternativas explícitas del anexo. Ningún paquete está instalado por documentarlo. Escoger fetch o Axios como único estándar; el formato de exportación y la generación del comprobante dependen del contrato y decisiones de fase.
