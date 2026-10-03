---
title: "Progreso y estado de entrega"
tags: [zontes, estado]
status: activo
updated: 2026-10-03
---

# Progreso y estado de entrega

| Frente | Estado al 2026-10-03 | Evidencia |
| --- | --- | --- |
| Contexto/alcance/base técnica de los PDF | documentado y trazado; detalles operativos abiertos | [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]], [[02-Arquitectura/Base tecnica documentada]], [[02-Arquitectura/Decisiones pendientes]] |
| F0 — instalación separada FE/BE | **verificada localmente** en ambos repos (instalación limpia, lint, typecheck, test, build, smoke, FE→BE). Código F0 publicado con autorización de Paulo en `main`: `FidelizacionFronted` `f29da45` (sobre `4f8ad6e`) y `FidelizacionBackend` `747e191` (sobre `e9e0dd2`); fusionado en `main` por avance rápido | [[05-Desarrollo/Lote F0 - instalacion separada frontend y backend]], [[05-Desarrollo/Entorno local]], [[05-Desarrollo/Testing]] (F0-T01…T11), [[02-Arquitectura/Contrato API v0 - F0]] |
| Lotes F1–F7 | creados como notas ejecutables; ninguno iniciado; la mayoría bloqueados por decisiones abiertas | [[05-Desarrollo/Lotes F1-F7 - indice]] |
| F1–F7 — producto | 0 fases implementadas/verificadas | no hay evidencia de producto |
| UI | 23 superficies mapeadas (UI-23 condicionada); 0 vistas de producto construidas. FE sólo tiene `/` y `/diagnostico` técnicas | [[03-Modulos/Mapa de vistas frontend]], [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]] |
| Testing | 11 pruebas técnicas F0 pasadas; 0 escenarios de producto (T-ROLE…T-DEMO) ejecutados | [[05-Desarrollo/Testing]] |
| Skills/servicios | 0 instalaciones de skills/MCP; dependencias de producto F0 instaladas por encargo; 0 servicios Firebase conectados | [[05-Desarrollo/Skills y herramientas]] |

## Puerta F0 frente a [[05-Desarrollo/Criterio de terminado]]

| Criterio | Estado | Evidencia |
| --- | --- | --- |
| Rutas confirmadas por Paulo al iniciar la fase | cumplido | [[05-Desarrollo/Entorno local]] (DEC-01) |
| Dos instalaciones separadas, cada una con manifiesto y lockfile | cumplido | dos repos Git independientes, `package.json` + `package-lock.json` propios |
| Reproducibles | cumplido en este host | F0-T01/T02 `npm ci` exit 0 sobre el lockfile |
| Lint/build/smoke por repositorio | cumplido | F0-T03…T06 |
| Llamada local FE→BE | cumplido | F0-T07 (Node), F0-T08 (navegador), F0-T09 (negativo) |
| Contrato inicial I-01/I-02, errores y fechas | cumplido en v0: implementado transversal + salud; I-01/I-02 como **propuesta no aprobada** dependiente de DEC-02/03/04 | [[02-Arquitectura/Contrato API v0 - F0]] |
| Documentación actualizada | cumplido | esta nota, Entorno, Testing, Bitácora, Decisiones |

Límite: la reproducibilidad se probó en un host Windows; no hay CI. La puerta no prueba reglas de negocio. El código está versionado y `main` de cada repo contiene la revisión F0.

No convertir “documentado” en “funcional”. Actualizar con fecha, commit/revisión de cada repositorio, prueba ejecutada y aprobación de Paulo cuando aplique. Si cambia una fuente, actualizar primero entrada y decisión afectadas.
