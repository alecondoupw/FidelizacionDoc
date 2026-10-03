---
title: "Decisiones pendientes"
tags: [zontes]
status: planificado
updated: 2026-10-03
---

# Decisiones pendientes

Las reglas consolidadas de SRC-02 ya están definidas; esta lista sólo recoge huecos que afectarían el resultado. Paulo decide antes de la fase dependiente. No pedir de nuevo si una respuesta ya aparece en SRC-01/02/03. Para resolver las diferencias de mockups y priorizar el inicio, usar [[02-Arquitectura/Hoja de decisiones UI y preparación de fases]].

| ID | Decisión solicitada a Paulo | Desbloquea |
| --- | --- | --- |
| DEC-01 | **Resuelta 2026-10-03** por Paulo: dos repos Git independientes en rutas confirmadas; ver [[02-Arquitectura/Decisiones tecnicas]] y [[05-Desarrollo/Entorno local]]. Sigue abierto: responsables por repo y CI. | F0 (cerrada); CI pendiente |
| DEC-02 | **Resuelta 2026-10-03:** proyecto Firebase de desarrollo creado y custodiado por Paulo; ver [[02-Arquitectura/Decisiones tecnicas]]. Abierto: ambientes de prueba/producción, cuotas y costes. | F1 (resuelto); F7 ambientes |
| DEC-03 | **Resuelta 2026-10-03:** rol/estado en Firestore + script CLI de bootstrap ejecutado por Paulo (custodio); en F4, alta de admins por invitación por correo de Firebase. | F1/F4 (resuelto) |
| DEC-04 | **Parcial 2026-10-03:** adaptador + doble sintético en F1; 1–3 marcas por correo; «Vincular nueva marca» deshabilitado. Cambio de correo resuelto en F4 (recalcular vínculo sólo con el correo nuevo). **Sigue abierto:** Contrato real de base de clientes: API/esquema, permisos, correos duplicados, fuente de verdad, multiplicidad de marcas y semántica de “Vincular nueva marca” en C02 | F1 sincronización/UI-17 |
| DEC-05 | **Resuelta 2026-10-03:** panel admin + API de integración con clave; idempotencia origen + id externo. Ver [[02-Arquitectura/Decisiones tecnicas]]. | F2 (resuelto) |
| DEC-06 | **Resuelta 2026-10-03:** America/La_Paz, vence a fin de día; lotes consumidos primero por vencimiento más próximo. | F2/F3 (resuelto) |
| DEC-07 | **Resuelta 2026-10-03:** catálogo por script + pantalla admin; stock por variante; Emitido/Entregado/Vencido/Anulado; PDF con QR en backend. Ver [[02-Arquitectura/Decisiones tecnicas]]. | F3 (resuelto) |
| DEC-08 | **Resuelta 2026-10-03:** eliminar = baja + anonimización conservando movimientos, canjes y auditoría; admin edita nombre, correo y estado; cliente sólo su nombre. Ver [[02-Arquitectura/Decisiones tecnicas]]. | F4 (resuelto) |
| DEC-09 | Definición operativa de “tiempo real”, filtros, volúmenes, granularidad de tendencias y formatos de exportación | F5 |
| DEC-10 | Tipo de contenido por marca (banners, noticias, eventos, promociones), visibilidad y assets autorizados | F6 |
| DEC-11 | Identidad final de MOTO LOYALTY/Zontes/Kiden/NIU, logotipos, fotos y fuentes licenciadas; autorizar activos reales distintos de las referencias SRC-04/05 | F0 diseño y F1–F6 UI |
| DEC-12 | Prioridad/detalle de vistas cliente frente a administrador; alcance de prototipo e hitos/fecha de hackathon | F0 plan |
| DEC-13 | Entorno de despliegue, backups/restauración, integraciones CRM/facturación y acceso a datos reales | F7 |
| DEC-14 | **Resuelta 2026-10-03:** movimientos definitivos; corrección por ajuste con motivo y auditoría. | F2/F3 (resuelto) |
| DEC-15 | ¿Se registra/asocia un cerebro de dominio específico o se mantiene sólo este Core con plantilla estructural? | Procedencia futura; no bloquea plan |
| DEC-16 | **Resuelta 2026-10-03:** importación CSV fuera de alcance; UI-23/F4-FE-04 no se construyen. | — |

**Puertas duras:** no crear administradores fuera del flujo seguro, no conectar base existente ni Firebase sin acceso autorizado, no fijar API/saldo/canje ambiguos por inferencia, no aplicar a eventos anteriores una regla editada. La pregunta debe incluir propuesta, alternativas y efecto en tareas; una respuesta se anota en [[02-Arquitectura/Decisiones tecnicas]] antes de implementar.
