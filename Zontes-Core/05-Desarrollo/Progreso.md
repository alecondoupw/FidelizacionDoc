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
| F1 — identidad y vínculo | **verificada con salvedades** (FE `71184a5`, BE `8fce35e` en `main`): dobles, Firestore real, Admin SDK real y recorrido integrado en navegador. Salvedades: cambio de correo sin probar (política abierta en DEC-04; se cubre en F4-BE-02) y revisión visual de las vistas protegidas en tres tamaños sólo en pruebas de componentes y en el recorrido de Paulo, sin capturas registradas | [[05-Desarrollo/Testing]] F1-T01…T11, [[05-Desarrollo/Lotes F1-F7 - indice]] |
| F2 — motor de puntos | **verificada con recorrido parcial** (BE `7e5589a`, FE `e4278a2` en `main`) (BE 116 pruebas + 61/61 Firestore real; FE 66 pruebas; recorrido real de reglas, otorgamiento y saldo). Sin probar por la interfaz real: vencimiento por marca, ajustes (incluido el rechazo por saldo insuficiente), edición/activación/eliminación de reglas y la vista del cliente no se ejercitaron por la interfaz con Firebase real. ADR-13 confirmada por Paulo | [[05-Desarrollo/Testing]] «Corridas F2» |
| F3 — beneficios y canje | **verificada con recorrido parcial** (BE `e8bbc7c`, FE `b2cf41b` en `main`) (BE 136 pruebas + 87/87 Firestore real, incluido canje concurrente; FE 83 pruebas; smoke BE 2/2 y FE 17/17; recorrido real: carga del catálogo y un canje). Sin probar por la interfaz real: entrega, anulación y edición de beneficios. DEC-07 aplicada; UI-25 Beneficios y UI-26 Canjes son propuestas sin mockup | [[05-Desarrollo/Testing]] «Corridas F3», [[02-Arquitectura/Contrato API v0 - F0]] §8 |
| F4 — administración de identidades | **verificada con recorrido parcial** (BE `403819b`, FE `6fb0035` en `main`) (BE 164 pruebas + 120/120 Firestore real, incluida la desactivación cruzada simultánea; FE 92 pruebas; smoke FE 21/21). DEC-03/04/08/16 aplicadas; ADR-14 (cuenta propia protegida, correo de admin no editable, búsqueda exacta por correo) pendiente de confirmar. Sin probar con Firebase Auth real: invitación, cambio de correo con verificación, baja, cambio de nombre y de contraseña (el recorrido no registró escrituras) | [[05-Desarrollo/Testing]] «Corridas F4», [[02-Arquitectura/Contrato API v0 - F0]] §9 |
| Lotes F5–F7 | creados; ninguno iniciado | [[05-Desarrollo/Lotes F1-F7 - indice]] |
| F1–F7 — producto | F1 verificada con salvedades; F2, F3 y F4 verificadas con recorrido parcial; F5–F7 sin iniciar | [[05-Desarrollo/Testing]] |
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
