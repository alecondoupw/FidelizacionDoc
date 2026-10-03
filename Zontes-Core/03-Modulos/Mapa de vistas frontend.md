---
title: "Mapa de vistas frontend"
tags: [zontes]
status: planificado
updated: 2026-10-02
---

# Mapa de vistas frontend

Las pantallas siguientes son **superficies de tarea**, no UI implementada. SRC-03 describe la vista cliente y SRC-04/05 aportan 23 mockups. La correspondencia imagen original → archivo preservado → UI-ID → lote FE está en [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]]. C = cliente con escritorio y móvil; A = administrador sólo escritorio. Las referencias guían el diseño, pero las acciones dependen de contrato BE y decisión de Paulo cuando corresponda. No aceptar fixtures como módulo completo.

| UI-ID | Vista / usuario | Datos y acción principales | Contrato BE dependiente | Fase / tarea FE | Ref. |
| --- | --- | --- | --- | --- | --- |
| UI-01 | Login/sesión admin | identidad, error genérico, logout | token validado, rol/estado | F1-FE-01 | SRC-02 p. 1; sin imagen |
| UI-02 | Login, registro y verificación cliente | correo normalizado, recuperación, vínculo/no vínculo | auth y enlace legacy | F1-FE-01 | C09, C10; login sin imagen |
| UI-03 | Mis puntos cliente | saldo por marca, vigencia, movimientos recientes | ledger autorizado | F2-FE-01 | C07 |
| UI-04 | Reglas de puntos admin | lista/filtro, crear/editar, vista previa singular/plural, estado | reglas por marca/evento | F2-FE-02 | A05 |
| UI-05 | Catálogo, detalle y canje cliente | stock, saldo, variantes, confirmar, resultado | catálogo y canje atómico | F3-FE-01 | C05, C06 |
| UI-06 | Administradores | listado, alta, edición, desactivar, confirmar eliminación | rol admin, último activo | F4-FE-01 | A03 |
| UI-07 | Clientes admin | filtros, detalle, vínculo, edición/cambio email, estado | autorización y re-vinculación | F4-FE-02 | A01 |
| UI-08 | Actividad admin | KPI→movimientos, marca/periodo | agregados auditables | F5-FE-01 | A10 |
| UI-09 | Canjes admin | tabla, filtros, detalle/comprobante | canjes autorizados | F5-FE-01 | A08 |
| UI-10 | Tendencias admin | líneas/barras, periodos/marcas | series temporales | F5-FE-02 | A11 |
| UI-11 | Exportaciones admin | filtro, formato, descarga/estado | export autorizado | F5-FE-03 | A12 |
| UI-12 | Contenido por marca admin | lista/editor/estado/vista previa si se decide | contenido aislado por marca | F6-FE-01 | A09 |
| UI-13 | Inicio cliente | resumen, saldo, vencimiento, marcas y accesos | saldos, vínculos y reglas activas | F2-FE-01 | C08 |
| UI-14 | Historial cliente | filtros, resumen y movimientos | ledger del propietario | F2-FE-01 | C01 |
| UI-15 | Mis canjes cliente | lista, filtros, detalle y estado | canjes del propietario | F3-FE-01 | C04 |
| UI-16 | Comprobante/cupón cliente | código, vigencia, descarga, QR si aplica | comprobante autorizado | F3-FE-01 | C04; sin imagen aislada |
| UI-17 | Mis marcas cliente | vinculadas, marca activa, acceso a catálogo | marcas autorizadas por correo | F1-FE-02 | C02 |
| UI-18 | Mi perfil cliente | consulta y edición permitida, contraseña/preferencias según contrato | identidad y campos autorizados | F1-FE-03, F4-FE-03 | C03 |
| UI-19 | Vencimiento admin | periodo/activación por marca e historial | política prospectiva y auditoría | F2-FE-02 | A06 |
| UI-20 | Movimientos admin | filtros, detalle y exportación autorizada | ledger y permisos | F5-FE-01 | A07 |
| UI-21 | Dashboard admin | KPI, actividad y canjes resumidos | mismos agregados de reportes | F5-FE-01 | A13 |
| UI-22 | Mi perfil admin | sesión y cambios permitidos | identidad, sesión y recuperación segura | F1-FE-03 | A04; detalle por decidir |
| UI-23 | Importar clientes admin **propuesto** | carga CSV y resultado, si se aprueba | origen legacy e importación segura por definir | F0-FE-01 evaluación; F4-FE-04 condicionado | A02; DEC-16 |
| UI-24 | Registrar puntos admin **propuesto en F2** | registro manual de eventos y ajustes con motivo | `/admin/eventos`, `/admin/ajustes` (DEC-05/14) | F2-FE-02 | sin mockup; línea visual de A05/A06 |
| UI-25 | Beneficios admin **propuesto en F3** | lista por marca, crear/editar con opciones y stock (sin límite), vigencia del cupón, disponible desde, activo | `/admin/beneficios` (DEC-07) | F3-FE-01 | sin mockup; línea visual de A05 |
| UI-26 | Canjes por código admin **propuesto en F3** | buscar por código, marcar entregado, anular con motivo | `/admin/canjes/{codigo}` (DEC-07) | F3-FE-01 | sin mockup; el reporte de canjes (A08) sigue en F5 |

UI-23 no es requisito aprobado ni tarea de implementación autorizada. Los mockups de C04/C05 reúnen etapas distintas; la FE debe separarlas en estados o rutas coherentes. Las imágenes admin no demuestran el diseño móvil. No hay imagen de login de ningún rol.

Cada UI-ID necesita estado vacío, carga, error, falta de permiso, éxito, confirmación de acción irreversible cuando aplique, escritorio/tablet/móvil, teclado/foco y texto accesible. Para cliente aplicar SRC-03 pp. 2, 9–10 y las dos proporciones dibujadas; para admin aplicar SRC-02 pp. 8–9 y diseñar/verificar sus variantes tablet/móvil. Aplicar [[02-Arquitectura/Guia visual y criterios anti slop]] y los criterios de [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]]. Una nueva referencia se registra por versión; nunca sobrescribir una decisión silenciosamente.
