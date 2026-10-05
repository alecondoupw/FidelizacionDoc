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
| F0 — instalación separada FE/BE | **verificada localmente** en ambos repos (instalación limpia, lint, typecheck, test, build, smoke, FE→BE). Código F0 publicado con autorización de Usuario en `main`: `FidelizacionFronted` `f29da45` (sobre `4f8ad6e`) y `FidelizacionBackend` `747e191` (sobre `e9e0dd2`); fusionado en `main` por avance rápido | [[05-Desarrollo/Lote F0 - instalacion separada frontend y backend]], [[05-Desarrollo/Entorno local]], [[05-Desarrollo/Testing]] (F0-T01…T11), [[02-Arquitectura/Contrato API v0 - F0]] |
| F1 — identidad y vínculo | **verificada con salvedades** (FE `71184a5`, BE `8fce35e` en `main`): dobles, Firestore real, Admin SDK real y recorrido integrado en navegador. Salvedades: cambio de correo sin probar (política abierta en DEC-04; se cubre en F4-BE-02) y revisión visual de las vistas protegidas en tres tamaños sólo en pruebas de componentes y en el recorrido de Usuario, sin capturas registradas | [[05-Desarrollo/Testing]] F1-T01…T11, [[05-Desarrollo/Lotes F1-F7 - indice]] |
| F2 — motor de puntos | **verificada con recorrido parcial** (BE `7e5589a`, FE `e4278a2` en `main`) (BE 116 pruebas + 61/61 Firestore real; FE 66 pruebas; recorrido real de reglas, otorgamiento y saldo). Sin probar por la interfaz real: vencimiento por marca, ajustes (incluido el rechazo por saldo insuficiente), edición/activación/eliminación de reglas y la vista del cliente no se ejercitaron por la interfaz con Firebase real. ADR-13 confirmada por Usuario | [[05-Desarrollo/Testing]] «Corridas F2» |
| F3 — beneficios y canje | **verificada con recorrido parcial** (BE `e8bbc7c`, FE `b2cf41b` en `main`) (BE 136 pruebas + 87/87 Firestore real, incluido canje concurrente; FE 83 pruebas; smoke BE 2/2 y FE 17/17; recorrido real: carga del catálogo y un canje). Sin probar por la interfaz real: entrega, anulación y edición de beneficios. DEC-07 aplicada; UI-25 Beneficios y UI-26 Canjes son propuestas sin mockup | [[05-Desarrollo/Testing]] «Corridas F3», [[02-Arquitectura/Contrato API v0 - F0]] §8 |
| F4 — administración de identidades | **verificada con recorrido parcial** (BE `403819b`, FE `6fb0035` en `main`) (BE 164 pruebas + 120/120 Firestore real, incluida la desactivación cruzada simultánea; FE 92 pruebas; smoke FE 21/21). DEC-03/04/08/16 aplicadas; ADR-14 (cuenta propia protegida, correo de admin no editable, búsqueda exacta por correo) pendiente de confirmar. Sin probar con Firebase Auth real: invitación, cambio de correo con verificación, baja, cambio de nombre y de contraseña (el recorrido no registró escrituras) | [[05-Desarrollo/Testing]] «Corridas F4», [[02-Arquitectura/Contrato API v0 - F0]] §9 |
| F5 — observabilidad de negocio | **verificada con recorrido integrado** (BE `a4f5014`, FE `7d8e3ce` en `main`) (BE 182 pruebas + 138/138 Firestore real; FE 102 pruebas; smoke FE 27/27). DEC-09 aplicada; ADR-15 confirmada. Datos de F2/F3 incorporados al libro con `reportes:conciliar -- --reparar` (autorizado por Usuario) | [[05-Desarrollo/Testing]] «Corridas F5», [[02-Arquitectura/Contrato API v0 - F0]] §10 |
| F6 — contenido y calidad visual | **verificada** (BE `713e39e`, FE `bb93380` en `main`) (BE 190 pruebas + 148/148 Firestore real; FE 108 pruebas; smoke FE 29/29). DEC-10 aplicada; DEC-11 parcial (línea visual provisional, sin logos ni fotos). Contenido por marca en el panel y Novedades/carrusel para el cliente, probados con las sesiones reales de Usuario y 3 publicaciones de ejemplo. Revisión visual de 25 UI-ID en tres tamaños con correcciones; diferencias con los mockups pendientes de aprobación de Usuario | [[05-Desarrollo/Testing]] «Corridas F6», [[06-Estado/Evidencias/F6-revision-visual]], [[02-Arquitectura/Contrato API v0 - F0]] §11 |
| F7 — entrega y operación | **en curso** (BE `1a46ea6`, FE `e83b92f` en `main`). DEC-13 aplicada. Hecho y verificado en local: observabilidad, límites, reglas de Firestore, respaldo con simulacro real (60 documentos, sin diferencias), configuración de Render/Vercel y cron, documentación de la API con colección Postman comprobada, manuales de despliegue y de uso, guion de demo y optimización medida (Inicio −23 %). BE 261 pruebas + 149/149 Firestore real; FE 112; smoke 29/29. Pendiente: despliegue por Usuario, T-DEMO, medición en producción y DEC-12 | [[05-Desarrollo/Testing]] «Corridas F7», [[08-Produccion/Manual de despliegue y operacion]], [[07-Manuales/Manual de usuario]] |
| F8 — correcciones SRC-06 | **implementada y verificada en local** (2026-10-04; BE `4e886e8`, FE `647012c` en `main`). DEC-17/18/19 resueltas por Usuario. 11/15 lotes implementados (D-01, BE-01…04 y FE-05 verificados; FE-01…04 verificados en componentes). BE 278 pruebas + 163/163 Firestore real; FE 118; smoke 29/29; 7 mutaciones detectadas. Pendientes: recorridos F8-I-01…I-03 y revisión visual de las pantallas de administración | [[05-Desarrollo/Lotes F8 - correcciones SRC-06]], [[05-Desarrollo/Testing]] «Corridas F8», [[02-Arquitectura/Contrato API v0 - F0]] §13 |
| F9 — simplificación UI e identidad Zontes | **Planificada en el Core el 2026-10-05; sin implementación ni pruebas F9.** SRC-07/08/09, DEC-20/22 y propuesta DEC-21; 8 lotes con puerta responsive y ambos roles | [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]], [[02-Arquitectura/Paleta Zontes propuesta F9]] |
| F1–F7 — producto | F1 verificada con salvedades; F2, F3 y F4 verificadas con recorrido parcial; F5 y F6 verificadas (F6 con identidad final pendiente de DEC-11); F7 en curso | [[05-Desarrollo/Testing]] |
| UI | F8: UI-23 Importar clientes construida; UI-10 Tendencias y UI-19 Vencimiento retiradas; UI-12 renombrada «Publicaciones por marca»; UI-13 Inicio rehecho según SRC-06 y revisado en tres tamaños; UI-24 con formulario único. Pantallas de administración de F8 sin revisión visual en navegador | [[03-Modulos/Mapa de vistas frontend]], [[06-Estado/Evidencias/F6-revision-visual]] |
| Testing | Corridas F0–F8 registradas con límites; F8-I-01…I-03 y revisión admin pendientes; F9-T01…T06 sólo previstas; T-DEMO y despliegue pendientes | [[05-Desarrollo/Testing]] |
| Skills/servicios | 0 instalaciones de skills/MCP; dependencias de producto F0 instaladas por encargo; 0 servicios Firebase conectados | [[05-Desarrollo/Skills y herramientas]] |

## Puerta F0 frente a [[05-Desarrollo/Criterio de terminado]]

| Criterio | Estado | Evidencia |
| --- | --- | --- |
| Rutas confirmadas por Usuario al iniciar la fase | cumplido | [[05-Desarrollo/Entorno local]] (DEC-01) |
| Dos instalaciones separadas, cada una con manifiesto y lockfile | cumplido | dos repos Git independientes, `package.json` + `package-lock.json` propios |
| Reproducibles | cumplido en este host | F0-T01/T02 `npm ci` exit 0 sobre el lockfile |
| Lint/build/smoke por repositorio | cumplido | F0-T03…T06 |
| Llamada local FE→BE | cumplido | F0-T07 (Node), F0-T08 (navegador), F0-T09 (negativo) |
| Contrato inicial I-01/I-02, errores y fechas | cumplido en v0: implementado transversal + salud; I-01/I-02 como **propuesta no aprobada** dependiente de DEC-02/03/04 | [[02-Arquitectura/Contrato API v0 - F0]] |
| Documentación actualizada | cumplido | esta nota, Entorno, Testing, Bitácora, Decisiones |

Límite: la reproducibilidad se probó en un host Windows; no hay CI. La puerta no prueba reglas de negocio. El código está versionado y `main` de cada repo contiene la revisión F0.

No convertir “documentado” en “funcional”. Actualizar con fecha, commit/revisión de cada repositorio, prueba ejecutada y aprobación de Usuario cuando aplique. Si cambia una fuente, actualizar primero entrada y decisión afectadas.
