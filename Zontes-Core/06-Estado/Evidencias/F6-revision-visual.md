---
title: "Revisión visual F6 — capturas por UI-ID"
tags: [zontes, evidencia, f6, ui]
status: verificado
updated: 2026-10-03
---

# Revisión visual F6 — capturas por UI-ID

Cotejo de F6-FE-02 y pulido de F6-FE-03 hechos por el agente el 2026-10-03 en el navegador integrado, contra FE (:3000) y BE (:4000) con el proyecto de desarrollo y sesiones reales iniciadas por Paulo (admin y cliente de prueba). Identidad: línea provisional (DEC-11 parcial). Tamaños: escritorio 1280×800, tablet 768×1024 y móvil 375×812. Capturas en `06-Estado/Evidencias/F6-revision-visual/` con el nombre `UI-xx-pantalla-{escritorio|tablet|movil}.jpg` (recortadas al área de la página; el panel del navegador mide ~736 px, por eso el escritorio se ve reducido).

## Método

1. **Barrido automático** de 26 pantallas (25 UI-ID) en los tres tamaños: desbordamiento horizontal, elementos fuera del ancho visible, controles sin nombre accesible y alertas de error.
2. **Revisión visual** de cada captura contra su referencia (A01–A13, C01–C10) y la [[02-Arquitectura/Guia visual y criterios anti slop]].
3. **Contraste** medido en el navegador (WCAG 1.4.11, 3:1 para controles) y **foco por teclado** con pulsaciones reales de Tab.

## Hallazgos corregidos

| Hallazgo | Dónde | Corrección |
|---|---|---|
| Interruptor apagado con contraste 1,29:1 (pista) y 1,2:1 (círculo) | Todos los `Switch` | Pista con `--muted-foreground`: 6,0:1 y 5,6:1 |
| Desborde horizontal de la página | Tendencias, escritorio y móvil | La tabla accesible de los gráficos llevaba `sr-only` en el `<table>`, que ignora `width: 1px`; ahora va en un contenedor |
| Columna ensanchada por un nombre largo con `truncate` | Reporte de canjes, móvil | `min-w-0` en tarjetas y KPI; nombre completo en `title` |
| Historial con columnas fijas que no cabían | Vencimiento, tablet | Columnas fijas sólo en `xl` |
| Filas comprimidas: fecha partida por palabra y etiqueta encima del texto | Reglas, Beneficios, Mis canjes, carrusel, zona de baja | Fila horizontal desde `lg` (la barra lateral ocupa 256 px desde `md`) |
| Tres tarjetas demasiado estrechas | Tendencias, tablet | Dos columnas hasta `xl` |
| Tabla de movimientos apretada | Mis puntos e Historial, tablet | Tabla desde `lg`; tarjetas antes |
| Tarjetas en dos columnas estrechas y «Ver detalle» partido | Catálogo y Mis marcas, tablet | Una columna en `md`, dos en `lg`; enlace sin salto |
| Marca partida en dos líneas y correo largo | Encabezado, móvil | Marca sin salto; nombre/correo recortado |
| Textos largos en la barra inferior | Panel, móvil | «Admins» y «Reglas» con nombre completo accesible (`corta`) |
| Menú «Más» de 590 px sin desplazamiento | Panel, móvil | Alto máximo y desplazamiento propio |
| Incoherencias de texto | Canjes en mostrador; Movimientos | Título «Canjes en mostrador»; filtro «Acumulaciones» como la etiqueta |
| Nombres accesibles pegados («Gestionara…») | Clientes, Mis marcas (F4) | `aria-label` explícito |

Resultado final: barrido limpio en las 26 pantallas y los tres tamaños; foco visible con teclado; sin errores en pantalla.

## Diferencias con los mockups que se mantienen

| Diferencia | Motivo |
|---|---|
| Sin fotos ni logotipos; ilustraciones con icono y color de marca | DEC-11 abierta: no hay activos con licencia |
| Encabezado sin buscador global, campana de notificaciones ni avatar (A01–A13, C08) | No hay requisito de notificaciones ni de búsqueda global en SRC-01/02/03; la búsqueda de clientes vive en Clientes |
| Sin «Importar clientes» (A02) | DEC-16: fuera de alcance |
| Sin pantalla «Auditoría» en el menú | La auditoría se consulta por persona en el detalle del cliente y por API (F4-BE-03); una vista global no tiene requisito propio |
| Sin «Contraer menú» en la barra lateral | No aporta a los requisitos; se puede agregar en F7 si Paulo lo pide |
| Inicio del cliente sin «¿Cómo ganar puntos?» ni tarjetas de marcas con foto (C08) | El contenido de reglas por marca no está modelado para el cliente; Mis marcas cubre las marcas |
| Listas en lugar de tablas en el panel | Legibles en tablet y móvil sin desplazamiento horizontal (SRC-02 p. 8) |
| Nombres «Sin nombre» y correo en el encabezado | Datos: las cuentas de prueba no tienen nombre en Firebase Auth |

## Observación de rendimiento (para F7)

Cada pantalla protegida tarda ~2–2,5 s en mostrar contenido; `/me` tarda ~1,7 s porque cada petición verifica la revocación del token en Firebase Auth y lee el perfil en Firestore (decisión de seguridad de F1). Varias capturas tomadas a los 4 s salieron aún cargando.

## Capturas por UI-ID

| UI-ID | Pantalla | Capturas |
|---|---|---|
| UI-02 | Acceso cliente | `UI-02-ingresar-cliente-*` |
| UI-03 | Mis puntos | `UI-03-mis-puntos-*` |
| UI-04 | Reglas de puntos | `UI-04-reglas-*` |
| UI-05 | Catálogo y detalle | `UI-05-catalogo-*`, `UI-05-detalle-beneficio-*` |
| UI-06 | Administradores | `UI-06-administradores-*` |
| UI-07 | Clientes | `UI-07-clientes-*` |
| UI-08 | Actividad | `UI-08-actividad-*` |
| UI-09 | Reporte de canjes | `UI-09-reporte-canjes-*` |
| UI-10 | Tendencias | `UI-10-tendencias-*` |
| UI-11 | Exportar datos | `UI-11-exportar-*` |
| UI-12 | Contenido por marca | `UI-12-contenido-*` |
| UI-13 | Inicio cliente (carrusel) | `UI-13-inicio-*` |
| UI-14 | Historial | `UI-14-historial-*` |
| UI-15 | Mis canjes | `UI-15-mis-canjes-*` |
| UI-16 | Comprobante con QR | `UI-16-comprobante-*` |
| UI-17 | Mis marcas | `UI-17-mis-marcas-*` |
| UI-18 | Mi perfil cliente | `UI-18-mi-perfil-cliente-*` |
| UI-19 | Vencimiento | `UI-19-vencimiento-*` |
| UI-20 | Movimientos | `UI-20-movimientos-*` |
| UI-21 | Dashboard | `UI-21-dashboard-*` |
| UI-22 | Mi perfil admin | `UI-22-mi-perfil-admin-*` |
| UI-24 | Registrar puntos | `UI-24-registrar-puntos-*` |
| UI-25 | Beneficios | `UI-25-beneficios-*` |
| UI-26 | Canjes en mostrador | `UI-26-canjes-mostrador-*` |
| UI-28 | Novedades | `UI-28-novedades-*` |

Sin captura en esta revisión: UI-01 (acceso admin, sólo en escritorio en F1), UI-27 (verificar correo, requiere un cambio de correo pendiente), UI-23 (fuera de alcance) y los estados de diálogo (editores, confirmaciones), cubiertos por pruebas de componentes.
