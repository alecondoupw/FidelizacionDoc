---
title: "Decisiones pendientes"
tags: [zontes]
status: planificado
updated: 2026-10-03
---

# Decisiones pendientes

Las reglas consolidadas de SRC-02 ya están definidas; esta lista sólo recoge huecos que afectarían el resultado. Usuario decide antes de la fase dependiente. No pedir de nuevo si una respuesta ya aparece en SRC-01/02/03. Para resolver las diferencias de mockups y priorizar el inicio, usar [[02-Arquitectura/Hoja de decisiones UI y preparación de fases]].

| ID | Decisión solicitada a Usuario | Desbloquea |
| --- | --- | --- |
| DEC-01 | **Resuelta 2026-10-03** por Usuario: dos repos Git independientes en rutas confirmadas; ver [[02-Arquitectura/Decisiones tecnicas]] y [[05-Desarrollo/Entorno local]]. Sigue abierto: responsables por repo y CI. | F0 (cerrada); CI pendiente |
| DEC-02 | **Resuelta 2026-10-03:** proyecto Firebase de desarrollo creado y custodiado por Usuario; ver [[02-Arquitectura/Decisiones tecnicas]]. Abierto: ambientes de prueba/producción, cuotas y costes. | F1 (resuelto); F7 ambientes |
| DEC-03 | **Resuelta 2026-10-03:** rol/estado en Firestore + script CLI de bootstrap ejecutado por Usuario (custodio); en F4, alta de admins por invitación por correo de Firebase. | F1/F4 (resuelto) |
| DEC-04 | **Parcial 2026-10-03:** adaptador + doble sintético en F1; 1–3 marcas por correo; «Vincular nueva marca» deshabilitado. Cambio de correo resuelto en F4 (recalcular vínculo sólo con el correo nuevo). **Sigue abierto:** Contrato real de base de clientes: API/esquema, permisos, correos duplicados, fuente de verdad, multiplicidad de marcas y semántica de “Vincular nueva marca” en C02 | F1 sincronización/UI-17 |
| DEC-05 | **Resuelta 2026-10-03:** panel admin + API de integración con clave; idempotencia origen + id externo. Ver [[02-Arquitectura/Decisiones tecnicas]]. | F2 (resuelto) |
| DEC-06 | **Resuelta 2026-10-03:** America/La_Paz, vence a fin de día; lotes consumidos primero por vencimiento más próximo. | F2/F3 (resuelto) |
| DEC-07 | **Resuelta 2026-10-03:** catálogo por script + pantalla admin; stock por variante; Emitido/Entregado/Vencido/Anulado; PDF con QR en backend. Ver [[02-Arquitectura/Decisiones tecnicas]]. | F3 (resuelto) |
| DEC-08 | **Resuelta 2026-10-03:** eliminar = baja + anonimización conservando movimientos, canjes y auditoría; admin edita nombre, correo y estado; cliente sólo su nombre. Ver [[02-Arquitectura/Decisiones tecnicas]]. | F4 (resuelto) |
| DEC-09 | **Resuelta 2026-10-03:** al instante + «Actualizar»; presets y rango de hasta 12 meses en hora de Bolivia; CSV + Excel; hasta 10.000 filas con nombre y correo, auditado. Ver [[02-Arquitectura/Decisiones tecnicas]]. | F5 (resuelto) |
| DEC-10 | **Resuelta 2026-10-03:** «Publicación» con categoría y destacada; visible si activa y dentro de su ventana (hora de Bolivia); ilustración por marca sin subida de archivos. Ver [[02-Arquitectura/Decisiones tecnicas]]. | F6 (resuelto) |
| DEC-11 | **Parcial 2026-10-03:** F6 se pule con la línea visual provisional. **Sigue abierto:** Identidad final de MOTO LOYALTY/Zontes/Kiden/NIU, logotipos, fotos y fuentes licenciadas; autorizar activos reales distintos de las referencias SRC-04/05 | F0 diseño y F1–F6 UI |
| DEC-12 | Prioridad/detalle de vistas cliente frente a administrador; alcance de prototipo e hitos/fecha de hackathon | F0 plan |
| DEC-13 | **Resuelta 2026-10-03:** Vercel (FE) + Render (BE) gratis, cron de GitHub Actions, respaldo JSON propio con restauración probada, Postman + Markdown, integraciones sólo documentadas y datos sintéticos. Ver [[02-Arquitectura/Decisiones tecnicas]]. | F7 (resuelto) |
| DEC-14 | **Resuelta 2026-10-03:** movimientos definitivos; corrección por ajuste con motivo y auditoría. | F2/F3 (resuelto) |
| DEC-15 | ¿Se registra/asocia un cerebro de dominio específico o se mantiene sólo este Core con plantilla estructural? | Procedencia futura; no bloquea plan |
| DEC-16 | **Resuelta 2026-10-03:** importación CSV fuera de alcance; UI-23/F4-FE-04 no se construyen. | — |
| DEC-17 | **Resuelta 2026-10-03:** importación CSV/XLSX por marca leída en el backend, recortar + minúsculas, conflictos conservados y señalados, reporte 90 días, 5.000 filas. Ver [[02-Arquitectura/Decisiones tecnicas]]. | F8 cadena A (resuelto) |
| DEC-18 | **Resuelta 2026-10-03:** sólo sumas con vencimiento propio (hoy a 2 años), la API de integración exige fecha, sin corrección manual, rutas antiguas retiradas. Ver [[02-Arquitectura/Decisiones tecnicas]]. | F8 cadena B (resuelto) |
| DEC-19 | **Resuelta 2026-10-03:** Tendencias fuera (pantalla y API), avisos calculados, banner ilustrado que rota destacadas, búsqueda hacia el catálogo. Ver [[02-Arquitectura/Decisiones tecnicas]]. | F8 cadenas C/D (resuelto) |
| DEC-20 | **Resuelta por petición directa de Usuario, 2026-10-05:** simplificaciones de UI-13/17/18, Novedades y texto de sidebar. Ver [[02-Arquitectura/Decisiones tecnicas]]. | F9 alcance (resuelto) |
| DEC-21 | **Propuesta cromática F9 pendiente de revisión:** colores observados en Zontes Bolivia y tokens complementarios en [[02-Arquitectura/Paleta Zontes propuesta F9]]. No implica licencia de logo/fotos/fuentes (DEC-11). | F9-FE-04 |
| DEC-22 | **Resuelta por petición directa de Usuario, 2026-10-05:** R02 hero, R03 ingreso y R04 registro cliente; R01 composición de referencia. Ver [[09-Entradas/Referencias UI 2026-10-05/Manifiesto de imagenes F9]]. | F9-FE-03/06 (resuelto) |

La matriz de conflictos, efectos sobre decisiones previas y contrato de transición está en [[02-Arquitectura/Impacto SRC-06 y decisiones F8]]. SRC-06 fue aportado por Usuario y DEC-17/18/19 quedaron resueltas el 2026-10-03; SRC-07 abre F9 con DEC-20 resuelta y DEC-21 propuesta.
**Puertas duras:** no crear administradores fuera del flujo seguro, no conectar base existente ni Firebase sin acceso autorizado, no fijar API/saldo/canje ambiguos por inferencia, no aplicar a eventos anteriores una regla editada. La pregunta debe incluir propuesta, alternativas y efecto en tareas; una respuesta se anota en [[02-Arquitectura/Decisiones tecnicas]] antes de implementar.
