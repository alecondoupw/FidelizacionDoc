---
title: "Mapa de vistas frontend"
tags: [zontes]
status: planificado
updated: 2026-10-03
---

# Mapa de vistas frontend

Las filas conservan el inventario original; varias vistas figuran implementadas en F1–F7 según [[05-Desarrollo/Testing]]. SRC-06 agrega correcciones F8 aún sin implementar. Los IDs retirados siguen como historia para trazabilidad. SRC-03 describe la vista cliente y SRC-04/05 aportan 23 mockups. La correspondencia imagen original → archivo preservado → UI-ID → lote FE está en [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]]. C = cliente con escritorio y móvil; A = administrador sólo escritorio. Las referencias guían el diseño, pero las acciones dependen de contrato BE y decisión de Usuario cuando corresponda. No aceptar fixtures como módulo completo.

| UI-ID | Vista / usuario | Datos y acción principales | Contrato BE dependiente | Fase / tarea FE | Ref. |
| --- | --- | --- | --- | --- | --- |
| UI-01 | Login/sesión admin | identidad, error genérico, logout | token validado, rol/estado | F1-FE-01 | SRC-02 p. 1; sin imagen |
| UI-02 | Login, registro y verificación cliente | correo normalizado, recuperación, vínculo/no vínculo | auth y enlace legacy | F1-FE-01 | C09, C10; login sin imagen |
| UI-03 | Mis puntos cliente | saldo por marca, vigencia, movimientos recientes | ledger autorizado | F2-FE-01 | C07 |
| UI-04 | Reglas de puntos admin | lista/filtro, crear/editar, vista previa singular/plural, estado | reglas por marca/evento | F2-FE-02 | A05 |
| UI-05 | Catálogo, detalle y canje cliente | stock, saldo, variantes, confirmar, resultado | catálogo y canje atómico | F3-FE-01 | C05, C06 |
| UI-06 | Administradores | listado, alta, edición, desactivar, confirmar eliminación | rol admin, último activo | F4-FE-01 | A03 |
| UI-07 | Clientes admin; ajuste F8 | búsqueda correo/filtro marca, detalle 0–3 marcas y estado; sin alta manual | importación/vínculo autorizado | F4-FE-02; F8-FE-02 | A01; SRC-06 pp. 1–2 |
| UI-08 | Actividad admin · `/admin/actividad` (F5) | KPI→movimientos, marca/periodo | agregados auditables | F5-FE-01 | A10 |
| UI-09 | Canjes admin · `/admin/reporte-canjes` (F5) | tabla, filtros, detalle/comprobante | canjes autorizados | F5-FE-01 | A08 |
| UI-10 | Tendencias admin; retiro solicitado en F8 | retirar apartado y menú tras DEC-19; conservar evidencia previa | series históricas según contrato | F5-FE-02 histórico; F8-FE-04 | A11 histórico; SRC-06 p. 2 |
| UI-11 | Exportaciones admin · `/admin/exportar` (F5) | filtro, formato, descarga/estado | export autorizado | F5-FE-03 | A12 |
| UI-12 | Publicaciones por marca admin (nombre solicitado en F8) | conservar lista/editor, botones y demás textos; cambiar sólo menú y título | contenidos I-08 | F6-FE-01; F8-FE-04 | A09; SRC-06 p. 2 |
| UI-13 | Inicio cliente; nueva referencia F8 | saludo, búsqueda, banner, total informativo, vencimiento, accesos, marcas y reglas activas | saldos/vínculos/reglas/contenidos autorizados | F2-FE-01; F8-FE-05 | C08 + SRC-06 pp. 4–5 e imagen |
| UI-14 | Historial cliente | filtros, resumen y movimientos | ledger del propietario | F2-FE-01 | C01 |
| UI-15 | Mis canjes cliente | lista, filtros, detalle y estado | canjes del propietario | F3-FE-01 | C04 |
| UI-16 | Comprobante/cupón cliente | código, vigencia, descarga, QR si aplica | comprobante autorizado | F3-FE-01 | C04; sin imagen aislada |
| UI-17 | Mis marcas cliente | vinculadas, marca activa, acceso a catálogo | marcas autorizadas por correo | F1-FE-02 | C02 |
| UI-18 | Mi perfil cliente | consulta y edición permitida, contraseña/preferencias según contrato | identidad y campos autorizados | F1-FE-03, F4-FE-03 | C03 |
| UI-19 | Vencimiento admin; retiro solicitado en F8 | sin apartado independiente ni opción de menú; fecha pasa a UI-24 | vigencia histórica y nuevo contrato DEC-18 | F2-FE-02 histórico; F8-FE-04 | A06 histórico; SRC-06 p. 3 |
| UI-20 | Movimientos admin · `/admin/movimientos` (F5) | filtros, detalle y exportación autorizada | ledger y permisos | F5-FE-01 | A07 |
| UI-21 | Dashboard admin · `/admin/dashboard`, entrada del panel (F5) | KPI, actividad y canjes resumidos | mismos agregados de reportes | F5-FE-01 | A13 |
| UI-22 | Mi perfil admin | sesión y cambios permitidos | identidad, sesión y recuperación segura | F1-FE-03 | A04; detalle por decidir |
| UI-23 | Importar clientes admin; reconsideración F8 | CSV/XLSX por marca, preview, confirmación, reporte; sin alta manual | importación idempotente y vínculo por correo verificado | F4-FE-04 histórico; F8-FE-01 | A02; SRC-06 pp. 1–2; DEC-17 |
| UI-24 | Registrar puntos admin; ajuste F8 | único formulario de suma >0 con motivo, marca vinculada y fecha de vencimiento propia | grant idempotente y caducidad automática | F2-FE-02 histórico; F8-FE-03 | SRC-06 p. 3; sin mockup propio |
| UI-25 | Beneficios admin **propuesto en F3** | lista por marca, crear/editar con opciones y stock (sin límite), vigencia del cupón, disponible desde, activo | `/admin/beneficios` (DEC-07) | F3-FE-01 | sin mockup; línea visual de A05 |
| UI-26 | Canjes por código admin **propuesto en F3** | buscar por código, marcar entregado, anular con motivo | `/admin/canjes/{codigo}` (DEC-07) | F3-FE-01 | sin mockup; el reporte de canjes (A08) sigue en F5 |
| UI-28 | Novedades cliente · `/novedades?marca=` **propuesto en F6** | publicaciones visibles de las marcas vinculadas con filtro por marca; las destacadas también en el carrusel de Inicio (UI-13) | `/contenidos` (I-08, DEC-10) | F6-FE-01 | sin mockup propio; tarjetas del carrusel de C08 |
| UI-27 | Verificar nuevo correo **propuesto en F4** | aviso, enviar enlace, confirmar verificación, cerrar sesión | 403 `EMAIL_NOT_VERIFIED` tras cambio de correo (DEC-04) | F4-FE-02 | sin mockup; composición de C09/C10 |

UI-23 estuvo fuera de alcance por DEC-16 (2026-10-03); SRC-06 solicita reconsiderarla y F8 depende de DEC-17. Los mockups de C04/C05 reúnen etapas distintas; la FE debe separarlas en estados o rutas coherentes. Las imágenes admin no demuestran el diseño móvil. No hay imagen de login de ningún rol.

SRC-06 modifica el estado objetivo de UI-07/10/12/13/19/23/24; [[05-Desarrollo/Lotes F8 - correcciones SRC-06]] conserva cadenas y puertas. UI-23 estaba fuera de alcance por DEC-16 histórica; no programar importación hasta DEC-17. La nueva imagen de UI-13 está en [[09-Entradas/Referencias UI 2026-10-03/Manifiesto]].
Cada UI-ID necesita estado vacío, carga, error, falta de permiso, éxito, confirmación de acción irreversible cuando aplique, escritorio/tablet/móvil, teclado/foco y texto accesible. Para cliente aplicar SRC-03 pp. 2, 9–10 y las dos proporciones dibujadas; para admin aplicar SRC-02 pp. 8–9 y diseñar/verificar sus variantes tablet/móvil. Aplicar [[02-Arquitectura/Guia visual y criterios anti slop]] y los criterios de [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]]. Capturas de las vistas construidas (F6) en [[06-Estado/Evidencias/F6-revision-visual]]. Una nueva referencia se registra por versión; nunca sobrescribir una decisión silenciosamente.
