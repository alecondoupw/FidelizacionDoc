---
title: "Lotes F1–F7 — índice"
tags: [zontes, lotes, plan]
status: activo
updated: 2026-10-03
---

# Lotes F1–F7 — índice

Creados el 2026-10-03 tras verificar F0 ([[05-Desarrollo/Lote F0 - instalacion separada frontend y backend]]), uno por resultado comprobable del [[05-Desarrollo/Plan por fases]], con [[05-Desarrollo/Plantilla de lote de trabajo]]. Fuentes: SRC-01/02/03 vía [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]], [[03-Modulos/Mapa de vistas frontend]], [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]], [[04-Reglas-de-negocio/_Indice de reglas]] y decisiones vigentes. **Ningún lote está iniciado.** Los nombres de rutas HTTP y de campos fuera del contrato v0 son propuestas que se fijan dentro de cada lote.

**Resumen (2026-10-03):** 41 lotes · F1: 6 implementados y probados con dobles, F1-I-01 bloqueado por entorno · F2–F7: 34 lotes no iniciados (27 bloqueados por decisión, 6 a la espera de otros lotes, 1 condicionado). DEC-02/03 resueltas y DEC-04 parcial el 2026-10-03.

## F1 — Identidad y vínculo

| Lote | Frente | Objetivo | Estado | Depende de |
| --- | --- | --- | --- | --- |
| [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]] | BE | Express verifica el ID token de Firebase (firma, expiración y revocación) con Admin SDK, carga el perfil (rol y estado) y expone `GET /ap… | Implementado y probado con dobles; integración real pendiente | F0 verificada. DEC-02 y autorización para usar Firebase Auth Emulator (requiere `firebase-tools`, no instalado) o un proyecto de prueba sin datos reales. |
| [[05-Desarrollo/Lotes/F1-BE-02 - Bootstrap del administrador inicial\|F1-BE-02]] | BE | Existe un procedimiento seguro e idempotente para precrear el administrador inicial, sin ningún endpoint público de registro admin; los a… | Implementado y probado con dobles; integración real pendiente | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]]; DEC-02; DEC-03. |
| [[05-Desarrollo/Lotes/F1-BE-03 - Normalizacion de correo y vinculo legacy\|F1-BE-03]] | BE | Al registrarse un cliente, Express normaliza el correo, busca coincidencia exacta en la fuente existente autorizada y deja la cuenta vinc… | Implementado y probado con dobles; integración real pendiente | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]]; DEC-04 (contrato de la fuente); acceso autorizado a la fuente o a un doble acordado. |
| [[05-Desarrollo/Lotes/F1-FE-01 - Login registro y verificacion cliente y login admin\|F1-FE-01]] | FE | El cliente inicia sesión o se registra por pasos con Firebase Auth y ve la verificación con resultado vinculado/no vinculado; el admin en… | Implementado y probado con dobles; integración real pendiente | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]], [[05-Desarrollo/Lotes/F1-BE-03 - Normalizacion de correo y vinculo legacy\|F1-BE-03]] para integrar; DEC-02; React Testing Library/jsdom a instalar en el lote. |
| [[05-Desarrollo/Lotes/F1-FE-02 - Mis marcas cliente\|F1-FE-02]] | FE | El cliente ve sólo las marcas vinculadas que confirma el BE, elige la marca activa y accede a su catálogo; el saldo por marca se integra… | Implementado y probado con dobles; integración real pendiente | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]], [[05-Desarrollo/Lotes/F1-FE-01 - Login registro y verificacion cliente y login admin\|F1-FE-01]]. |
| [[05-Desarrollo/Lotes/F1-FE-03 - Mi perfil cliente y admin en consulta\|F1-FE-03]] | FE | Cliente y admin consultan sus datos de identidad y cierran sesión; la edición queda para F4-FE-03 tras contrato. | Implementado y probado con dobles; integración real pendiente | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]], [[05-Desarrollo/Lotes/F1-FE-01 - Login registro y verificacion cliente y login admin\|F1-FE-01]]. |
| [[05-Desarrollo/Lotes/F1-I-01 - Integracion de identidad y vinculo\|F1-I-01]] | Integración | Demostrar FE↔BE el recorrido registro → vínculo → `/me` → logout con datos sintéticos, y que permisos, duplicados, marcas y cambio de cor… | Bloqueado: falta el proyecto Firebase de desarrollo y usuarios de prueba | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]]/02/03, [[05-Desarrollo/Lotes/F1-FE-01 - Login registro y verificacion cliente y login admin\|F1-FE-01]]/02/03. |

## F2 — Motor de puntos

| Lote | Frente | Objetivo | Estado | Depende de |
| --- | --- | --- | --- | --- |
| [[05-Desarrollo/Lotes/F2-BE-01 - Reglas de puntos por marca y evento\|F2-BE-01]] | BE | El admin crea, consulta, filtra, edita, activa/desactiva y elimina reglas evento+marca+puntos+estado; la combinación es única, no existe… | Pendiente: depende de F1-BE-01 y DEC-02 | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]] (rol admin); DEC-02. |
| [[05-Desarrollo/Lotes/F2-BE-02 - Ledger idempotente y transacciones de otorgamiento\|F2-BE-02]] | BE | Un evento autorizado (origen + ID) busca la regla activa exacta y, en una transacción, registra evento, movimiento y fecha de vencimiento… | Bloqueado por decisión: DEC-05, DEC-06, DEC-14, DEC-02 | [[05-Desarrollo/Lotes/F2-BE-01 - Reglas de puntos por marca y evento\|F2-BE-01]]; DEC-05/06/14; emulador Firestore autorizado para concurrencia. |
| [[05-Desarrollo/Lotes/F2-BE-03 - Vencimiento por marca y auditoria\|F2-BE-03]] | BE | La vigencia se configura por marca (días/meses/años, activación); el BE calcula el vencimiento al otorgar y un proceso reejecutable vence… | Bloqueado por decisión: DEC-06, DEC-13 | [[05-Desarrollo/Lotes/F2-BE-02 - Ledger idempotente y transacciones de otorgamiento\|F2-BE-02]]; DEC-06; DEC-13 para la ejecución programada. |
| [[05-Desarrollo/Lotes/F2-FE-01 - Inicio saldo e historial cliente\|F2-FE-01]] | FE | Inicio, Mis puntos e Historial muestran el mismo saldo por marca, los vencimientos con la fecha del BE y los movimientos filtrables del p… | Bloqueado: depende de F2-BE-02 (DEC-05/06/14) | [[05-Desarrollo/Lotes/F2-BE-02 - Ledger idempotente y transacciones de otorgamiento\|F2-BE-02]], [[05-Desarrollo/Lotes/F1-FE-02 - Mis marcas cliente\|F1-FE-02]]. |
| [[05-Desarrollo/Lotes/F2-FE-02 - Reglas y vencimiento admin\|F2-FE-02]] | FE | El admin gestiona reglas (lista, filtros, crear/editar con vista previa singular/plural, activar/desactivar, eliminar con confirmación) y… | Pendiente (reglas) tras F2-BE-01 · Bloqueado (vigencia) por DEC-06 | [[05-Desarrollo/Lotes/F2-BE-01 - Reglas de puntos por marca y evento\|F2-BE-01]]; [[05-Desarrollo/Lotes/F2-BE-03 - Vencimiento por marca y auditoria\|F2-BE-03]] para vigencia. |
| [[05-Desarrollo/Lotes/F2-I-01 - Integracion evento a saldo e historial\|F2-I-01]] | Integración | Un evento realista llega desde su origen autorizado hasta saldo e historial del cliente y del admin, incluyendo el borde de vencimiento. | Bloqueado por decisión: DEC-05, DEC-06, DEC-14 | [[05-Desarrollo/Lotes/F2-BE-01 - Reglas de puntos por marca y evento\|F2-BE-01]]/02/03, [[05-Desarrollo/Lotes/F2-FE-01 - Inicio saldo e historial cliente\|F2-FE-01]]/02. |

## F3 — Beneficios y canje

| Lote | Frente | Objetivo | Estado | Depende de |
| --- | --- | --- | --- | --- |
| [[05-Desarrollo/Lotes/F3-BE-01 - Catalogo de beneficios por marca\|F3-BE-01]] | BE | El BE entrega catálogo y detalle de beneficios sólo de marcas vinculadas del cliente, con costo, disponibilidad, búsqueda y filtros. | Bloqueado por decisión: DEC-07 | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]]; DEC-07; DEC-02. |
| [[05-Desarrollo/Lotes/F3-BE-02 - Canje atomico con saldo stock e idempotencia\|F3-BE-02]] | BE | Un canje valida saldo y disponibilidad y, en una transacción, descuenta puntos, ajusta stock y registra canje y movimiento; un reintento… | Bloqueado por decisión: DEC-07, DEC-06 | [[05-Desarrollo/Lotes/F2-BE-02 - Ledger idempotente y transacciones de otorgamiento\|F2-BE-02]], [[05-Desarrollo/Lotes/F3-BE-01 - Catalogo de beneficios por marca\|F3-BE-01]]; DEC-06/07. |
| [[05-Desarrollo/Lotes/F3-BE-03 - Estados comprobante y reversa de canje\|F3-BE-03]] | BE | Cada canje tiene estados definidos y un comprobante o cupón con código trazable (QR si corresponde), visible sólo para su propietario; la… | Bloqueado por decisión: DEC-07 | [[05-Desarrollo/Lotes/F3-BE-02 - Canje atomico con saldo stock e idempotencia\|F3-BE-02]]; DEC-07. |
| [[05-Desarrollo/Lotes/F3-FE-01 - Catalogo canje mis canjes y comprobante cliente\|F3-FE-01]] | FE | El cliente explora el catálogo de su marca, ve el detalle, confirma un canje, ve el resultado real y consulta Mis canjes y su comprobante. | Bloqueado por decisión: DEC-07 | [[05-Desarrollo/Lotes/F3-BE-01 - Catalogo de beneficios por marca\|F3-BE-01]]/02/03, [[05-Desarrollo/Lotes/F2-FE-01 - Inicio saldo e historial cliente\|F2-FE-01]]. |
| [[05-Desarrollo/Lotes/F3-I-01 - Integracion de canje concurrente y aislamiento\|F3-I-01]] | Integración | Demostrar FE↔BE canje feliz, rechazos seguros, concurrencia y aislamiento entre marcas. | Bloqueado por decisión: DEC-07 | [[05-Desarrollo/Lotes/F3-BE-01 - Catalogo de beneficios por marca\|F3-BE-01]]/02/03, [[05-Desarrollo/Lotes/F3-FE-01 - Catalogo canje mis canjes y comprobante cliente\|F3-FE-01]]. |

## F4 — Administración de identidades

| Lote | Frente | Objetivo | Estado | Depende de |
| --- | --- | --- | --- | --- |
| [[05-Desarrollo/Lotes/F4-BE-01 - Gestion de administradores y ultimo activo\|F4-BE-01]] | BE | Un admin lista, crea, edita lo permitido, activa/desactiva y elimina otros admins; el último admin activo no puede eliminarse ni desactiv… | Bloqueado por decisión: DEC-03 | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]], [[05-Desarrollo/Lotes/F1-BE-02 - Bootstrap del administrador inicial\|F1-BE-02]]; DEC-03. |
| [[05-Desarrollo/Lotes/F4-BE-02 - Gestion de clientes y revinculacion\|F4-BE-02]] | BE | Un admin busca y filtra clientes, ve su detalle, edita campos permitidos, reevalúa el vínculo al cambiar el correo, activa/desactiva y el… | Bloqueado por decisión: DEC-08, DEC-04 | [[05-Desarrollo/Lotes/F1-BE-03 - Normalizacion de correo y vinculo legacy\|F1-BE-03]]; DEC-04/08. |
| [[05-Desarrollo/Lotes/F4-BE-03 - Auditoria y politica de conservacion\|F4-BE-03]] | BE | Los cambios de administradores, clientes, reglas y configuración dejan eventos de auditoría consultables con actor, marca, momento y ante… | Bloqueado por decisión: DEC-08 | [[05-Desarrollo/Lotes/F4-BE-01 - Gestion de administradores y ultimo activo\|F4-BE-01]]/02; DEC-08. |
| [[05-Desarrollo/Lotes/F4-FE-01 - Administradores admin\|F4-FE-01]] | FE | Vista de gestión de administradores con alta, edición, estado y eliminación confirmada. | Bloqueado por decisión: DEC-03 | [[05-Desarrollo/Lotes/F4-BE-01 - Gestion de administradores y ultimo activo\|F4-BE-01]]. |
| [[05-Desarrollo/Lotes/F4-FE-02 - Clientes admin\|F4-FE-02]] | FE | Vista de clientes con filtros, detalle, vínculo, edición permitida y estado. | Bloqueado por decisión: DEC-08, DEC-04 | [[05-Desarrollo/Lotes/F4-BE-02 - Gestion de clientes y revinculacion\|F4-BE-02]]. |
| [[05-Desarrollo/Lotes/F4-FE-03 - Edicion de perfil permitida\|F4-FE-03]] | FE | Cliente y admin editan sólo los campos que DEC-08 permita, con contraseña y preferencias según contrato. | Bloqueado por decisión: DEC-08 | [[05-Desarrollo/Lotes/F1-FE-03 - Mi perfil cliente y admin en consulta\|F1-FE-03]]; [[05-Desarrollo/Lotes/F4-BE-02 - Gestion de clientes y revinculacion\|F4-BE-02]]; DEC-08. |
| [[05-Desarrollo/Lotes/F4-FE-04 - Importacion CSV de clientes condicionada\|F4-FE-04]] | FE | Sólo si Paulo aprueba DEC-16: carga CSV de clientes existentes con validación, deduplicación, errores por fila y auditoría. | Condicionado: fuera de alcance hasta DEC-16 | DEC-16; [[05-Desarrollo/Lotes/F4-BE-02 - Gestion de clientes y revinculacion\|F4-BE-02]]. |
| [[05-Desarrollo/Lotes/F4-I-01 - Integracion de administracion de identidades\|F4-I-01]] | Integración | Probar FE↔BE que un cliente nunca se promueve, que el último admin activo está protegido y que las acciones prohibidas se rechazan en el… | Bloqueado por decisión: DEC-03, DEC-08 | [[05-Desarrollo/Lotes/F4-BE-01 - Gestion de administradores y ultimo activo\|F4-BE-01]]/02/03, [[05-Desarrollo/Lotes/F4-FE-01 - Administradores admin\|F4-FE-01]]/02/03. |

## F5 — Observabilidad de negocio

| Lote | Frente | Objetivo | Estado | Depende de |
| --- | --- | --- | --- | --- |
| [[05-Desarrollo/Lotes/F5-BE-01 - Agregados y consultas de reportes\|F5-BE-01]] | BE | El BE entrega actividad, canjes, tendencias y KPI filtrados por marca y periodo, derivados de movimientos y canjes, con índices Firestore… | Bloqueado por decisión: DEC-09 | [[05-Desarrollo/Lotes/F2-BE-02 - Ledger idempotente y transacciones de otorgamiento\|F2-BE-02]], [[05-Desarrollo/Lotes/F3-BE-02 - Canje atomico con saldo stock e idempotencia\|F3-BE-02]]; DEC-09. |
| [[05-Desarrollo/Lotes/F5-BE-02 - Exportacion autorizada\|F5-BE-02]] | BE | La API exporta clientes, movimientos, canjes y reportes con los filtros efectivos, autorización, encabezados claros y volumen controlado. | Bloqueado por decisión: DEC-09 | [[05-Desarrollo/Lotes/F5-BE-01 - Agregados y consultas de reportes\|F5-BE-01]]; DEC-09. |
| [[05-Desarrollo/Lotes/F5-FE-01 - Dashboard actividad movimientos y canjes admin\|F5-FE-01]] | FE | Dashboard con KPI que abren su desglose, y vistas de actividad, movimientos y canjes con filtros. | Bloqueado por decisión: DEC-09 | [[05-Desarrollo/Lotes/F5-BE-01 - Agregados y consultas de reportes\|F5-BE-01]]. |
| [[05-Desarrollo/Lotes/F5-FE-02 - Tendencias admin\|F5-FE-02]] | FE | Series temporales y comparación por marca con periodos seleccionables. | Bloqueado por decisión: DEC-09 | [[05-Desarrollo/Lotes/F5-BE-01 - Agregados y consultas de reportes\|F5-BE-01]]. |
| [[05-Desarrollo/Lotes/F5-FE-03 - Exportacion admin\|F5-FE-03]] | FE | El admin elige filtros y formato, lanza la exportación y ve su estado, error o descarga. | Bloqueado por decisión: DEC-09 | [[05-Desarrollo/Lotes/F5-BE-02 - Exportacion autorizada\|F5-BE-02]]. |
| [[05-Desarrollo/Lotes/F5-I-01 - Integracion y conciliacion de reportes\|F5-I-01]] | Integración | Conciliar cifras de pantalla y archivo con ledger y canjes, y comprobar comportamiento con volumen. | Bloqueado por decisión: DEC-09 | [[05-Desarrollo/Lotes/F5-BE-01 - Agregados y consultas de reportes\|F5-BE-01]]/02, [[05-Desarrollo/Lotes/F5-FE-01 - Dashboard actividad movimientos y canjes admin\|F5-FE-01]]/02/03. |

## F6 — Contenido y calidad visual

| Lote | Frente | Objetivo | Estado | Depende de |
| --- | --- | --- | --- | --- |
| [[05-Desarrollo/Lotes/F6-BE-01 - Contenido por marca\|F6-BE-01]] | BE | El admin crea, edita, activa/desactiva y elimina contenido de una marca; el cliente sólo recibe contenido activo de sus marcas. | Bloqueado por decisión: DEC-10, DEC-11 | [[05-Desarrollo/Lotes/F1-BE-01 - Verificacion de token y frontera de autorizacion\|F1-BE-01]]; DEC-10/11. |
| [[05-Desarrollo/Lotes/F6-FE-01 - Contenido por marca admin\|F6-FE-01]] | FE | Lista y editor de contenido por marca con estado y vista previa si se decide. | Bloqueado por decisión: DEC-10, DEC-11 | [[05-Desarrollo/Lotes/F6-BE-01 - Contenido por marca\|F6-BE-01]]. |
| [[05-Desarrollo/Lotes/F6-FE-02 - Cotejo visual de cada UI-ID\|F6-FE-02]] | FE | Cada UI-ID construida se compara con su referencia y con la guía visual durante su fase; aquí se consolida la revisión. | Pendiente: transversal, se ejecuta al cerrar cada UI-ID | UI-ID implementadas en F1–F5. |
| [[05-Desarrollo/Lotes/F6-FE-03 - Pulido responsive accesibilidad y marcas\|F6-FE-03]] | FE | Pulir responsive, foco, copy y diferenciación entre Zontes, Kiden y NIU con la identidad aprobada. | Bloqueado por decisión: DEC-11 | [[05-Desarrollo/Lotes/F6-FE-02 - Cotejo visual de cada UI-ID\|F6-FE-02]]; DEC-11. |
| [[05-Desarrollo/Lotes/F6-I-01 - Integracion de contenido y revision visual\|F6-I-01]] | Integración | Comparar con referencias y tareas reales, no sólo con capturas estéticas, y probar aislamiento de contenido por marca. | Bloqueado por decisión: DEC-10, DEC-11 | [[05-Desarrollo/Lotes/F6-BE-01 - Contenido por marca\|F6-BE-01]], [[05-Desarrollo/Lotes/F6-FE-01 - Contenido por marca admin\|F6-FE-01]]/02/03. |

## F7 — Entrega y operación

| Lote | Frente | Objetivo | Estado | Depende de |
| --- | --- | --- | --- | --- |
| [[05-Desarrollo/Lotes/F7-FE-01 - Recorrido demo y optimizacion medida\|F7-FE-01]] | FE | Recorrido demo cliente y admin sin errores, con mejoras de rendimiento medidas, no supuestas. | Bloqueado: depende de F1–F6 y DEC-12/13 | F1–F6 verificadas. |
| [[05-Desarrollo/Lotes/F7-BE-01 - Seguridad observabilidad respaldo y despliegue\|F7-BE-01]] | BE | Observabilidad, revisión de seguridad, backup y restauración probados y despliegue en un entorno autorizado. | Bloqueado por decisión: DEC-13 | F1–F6; DEC-13. |
| [[05-Desarrollo/Lotes/F7-BE-02 - Documentacion API y operacion\|F7-BE-02]] | BE | Documentación de la API, colección de pruebas manuales y manual de despliegue y operación. | Pendiente: crece con cada fase; cierre bloqueado por DEC-13 | Endpoints implementados; [[05-Desarrollo/Lotes/F7-BE-01 - Seguridad observabilidad respaldo y despliegue\|F7-BE-01]]. |
| [[05-Desarrollo/Lotes/F7-I-01 - Entregables y demostracion integrada\|F7-I-01]] | Integración | Entregar arquitectura, prototipo usuarios+puntos, código en repositorio compartido y manuales de despliegue y uso; ejecutar pruebas, back… | Bloqueado por decisión: DEC-12, DEC-13 | [[05-Desarrollo/Lotes/F7-FE-01 - Recorrido demo y optimizacion medida\|F7-FE-01]], [[05-Desarrollo/Lotes/F7-BE-01 - Seguridad observabilidad respaldo y despliegue\|F7-BE-01]]/02. |

## Evaluación de orquestación (2026-10-03)

**No se requiere un componente de orquestación instalado.** El grafo es acíclico y lineal por fases (F1 → F2 → F3/F5; F4 tras F1 en paralelo con F3; F6 transversal; F7 al final). Basta un **integrador único** que despacha cada lote a un solo agente, con FE y BE en paralelo sólo cuando el contrato del lote está escrito y sus superficies de archivos no se solapan (repos distintos). Persistencia del estado: estas notas y [[05-Desarrollo/Progreso]]. Puertas: las decisiones DEC listadas en cada lote, que son humanas y no se resuelven iterando. Alternativa si el volumen crece: revisar esta evaluación antes de introducir herramientas, con autorización de Paulo.

## Camino crítico propuesto (no aprobado)

Coincide con la propuesta de prioridad de la [[02-Arquitectura/Hoja de decisiones UI y preparación de fases]] (DEC-12): F1-BE-01 → F1-BE-03 → F1-FE-01 → F1-I-01 → F2-BE-01 → F2-BE-02 → F2-FE-01/F2-FE-02 → F2-I-01. Para abrirlo hacen falta, en este orden: **DEC-02** (proyecto Firebase o emulador autorizado), **DEC-03**, **DEC-04**, y después **DEC-05/06/14**.
