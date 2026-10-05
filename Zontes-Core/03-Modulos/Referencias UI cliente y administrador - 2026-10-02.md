---
title: "Referencias UI cliente y administrador — lote 2026-10-02"
tags: [zontes, ui, referencias]
status: inventariado
updated: 2026-10-02
---

# Referencias UI cliente y administrador — lote 2026-10-02

**Procedencia:** SRC-03 (PDF cliente), SRC-04 (ZIP cliente) y SRC-05 (ZIP administrador), conservados en [[09-Entradas/_Indice de entradas]]. Los JPEG extraídos son copias binarias de las entradas ZIP, con nombres estables C01–C10 y A01–A13; nombre original y SHA-256 individual en [[09-Entradas/Referencias UI 2026-10-02/Manifiesto de imagenes]]. Son **mockups de referencia aportados por Usuario**, no pantallas implementadas ni pruebas de comportamiento. Los textos, cifras, nombres, productos, fechas, logotipos y fotografías dentro de las imágenes son ilustrativos; su uso final como activos de producto y sus permisos siguen abiertos en DEC-11.

## Cliente: diez imágenes, escritorio y móvil en cada una

| Ref. | Imagen preservada y contenido observado | UI-ID / tarea FE | Fuente funcional y estado |
| --- | --- | --- | --- |
| C01 | [[09-Entradas/Referencias UI 2026-10-02/Cliente/C01-historial-cliente.jpeg]] · Historial de actividad, KPI, filtros, tabla/lista móvil | UI-14 · F2-FE-01 | SRC-03 pp. 5–6; referencia directa |
| C02 | [[09-Entradas/Referencias UI 2026-10-02/Cliente/C02-mis-marcas-cliente.jpeg]] · Marcas vinculadas, activa, acción de nueva vinculación | UI-17 · F1-FE-02 | SRC-03 p. 8; la acción de vincular requiere DEC-04; no implica vínculo manual |
| C03 | [[09-Entradas/Referencias UI 2026-10-02/Cliente/C03-mi-perfil-cliente.jpeg]] · Datos y configuración de cuenta | UI-18 · F1-FE-03, F4-FE-03 para edición | SRC-03 pp. 8–9; campos editables sujetos a DEC-08 |
| C04 | [[09-Entradas/Referencias UI 2026-10-02/Cliente/C04-mis-canjes-comprobante-cliente.jpeg]] · Mis canjes, detalle y cupón | UI-15/16 · F3-FE-01 | SRC-03 pp. 7–8; una imagen cubre dos estados/vistas |
| C05 | [[09-Entradas/Referencias UI 2026-10-02/Cliente/C05-detalle-confirmacion-canje-cliente.jpeg]] · Detalle de beneficio, resumen y estado de éxito | UI-05 · F3-FE-01 | SRC-03 pp. 6–7; el éxito dibujado no verifica una transacción |
| C06 | [[09-Entradas/Referencias UI 2026-10-02/Cliente/C06-catalogo-cliente.jpeg]] · Catálogo, filtros y tarjetas | UI-05 · F3-FE-01 | SRC-03 p. 6; disponibilidad debe venir del BE |
| C07 | [[09-Entradas/Referencias UI 2026-10-02/Cliente/C07-mis-puntos-cliente.jpeg]] · Saldo, marcas, vencimiento y movimientos | UI-03 · F2-FE-01 | SRC-03 p. 5; saldo compartido con otras vistas |
| C08 | [[09-Entradas/Referencias UI 2026-10-02/Cliente/C08-inicio-cliente.jpeg]] · Inicio y accesos rápidos | UI-13 · F2-FE-01 | SRC-03 pp. 4–5; depende de saldo y vínculo reales |
| C09 | [[09-Entradas/Referencias UI 2026-10-02/Cliente/C09-verificacion-vinculacion-cliente.jpeg]] · Progreso, marcas detectadas y cuenta creada | UI-02 · F1-FE-01 | SRC-03 p. 4; diseñar también el caso sin coincidencia |
| C10 | [[09-Entradas/Referencias UI 2026-10-02/Cliente/C10-registro-cliente.jpeg]] · Alta por pasos | UI-02 · F1-FE-01 | SRC-03 pp. 3–4; datos opcionales no son criterios de vínculo |

**Sin imagen cliente individual:** login y recuperación (UI-02, SRC-03 p. 3); comprobante aislado (UI-16, SRC-03 pp. 7–8); estados vacíos, error, permiso y sesiones expiradas. C04 y C05 muestran varias etapas en una composición: en producto se diseñan como estados o rutas distintas según el flujo, no como una sola página obligatoria. El PDF pide una imagen independiente por pantalla para herramientas de diseño; esa instrucción de generación no sustituye el pedido actual de inventariar referencias.

## Administrador: trece imágenes de escritorio

| Ref. | Imagen preservada y contenido observado | UI-ID / tarea FE | Fuente funcional y estado |
| --- | --- | --- | --- |
| A01 | [[09-Entradas/Referencias UI 2026-10-02/Administrador/A01-clientes-admin.jpeg]] · Clientes, filtros y acciones | UI-07 · F4-FE-02 | SRC-02 p. 3; referencia directa |
| A02 | [[09-Entradas/Referencias UI 2026-10-02/Administrador/A02-importacion-clientes-admin.jpeg]] · Carga CSV de clientes existentes | UI-23 · F0-FE-01 para evaluar; F4-FE-04 sólo si se aprueba | **Propuesta visual sin requisito aprobado** en SRC-01/02/03; DEC-16 |
| A03 | [[09-Entradas/Referencias UI 2026-10-02/Administrador/A03-administradores-admin.jpeg]] · Gestión de administradores | UI-06 · F4-FE-01 | SRC-02 pp. 2–3; referencia directa |
| A04 | [[09-Entradas/Referencias UI 2026-10-02/Administrador/A04-mi-perfil-admin.jpeg]] · Sesión y cambio de contraseña | UI-22 · F1-FE-03; edición sólo con contrato | Vista sugerida por mockup; flujo seguro por definir en DEC-03/08 |
| A05 | [[09-Entradas/Referencias UI 2026-10-02/Administrador/A05-reglas-puntos-admin.jpeg]] · Reglas por evento y marca | UI-04 · F2-FE-02 | SRC-02 pp. 3–5; sin campo de condición |
| A06 | [[09-Entradas/Referencias UI 2026-10-02/Administrador/A06-vencimiento-admin.jpeg]] · Vigencia por marca e historial de configuración | UI-19 · F2-FE-02 | SRC-02 p. 5; cambios sólo para puntos futuros |
| A07 | [[09-Entradas/Referencias UI 2026-10-02/Administrador/A07-movimientos-admin.jpeg]] · Ledger y filtros | UI-20 · F5-FE-01 | SRC-02 pp. 5–7; desglose de actividad, sin edición manual de saldo |
| A08 | [[09-Entradas/Referencias UI 2026-10-02/Administrador/A08-canjes-admin.jpeg]] · Reporte de canjes | UI-09 · F5-FE-01 | SRC-02 p. 6; estados sujetos a DEC-07 |
| A09 | [[09-Entradas/Referencias UI 2026-10-02/Administrador/A09-contenido-marca-admin.jpeg]] · Contenido por marca | UI-12 · F6-FE-01 | SRC-02 p. 7; tipo, programación y activos sujetos a DEC-10/11 |
| A10 | [[09-Entradas/Referencias UI 2026-10-02/Administrador/A10-actividad-admin.jpeg]] · Reporte de actividad | UI-08 · F5-FE-01 | SRC-02 p. 5; KPI deben abrir su desglose |
| A11 | [[09-Entradas/Referencias UI 2026-10-02/Administrador/A11-tendencias-admin.jpeg]] · Series y comparación | UI-10 · F5-FE-02 | SRC-02 p. 6; cifras sujetas a DEC-09 |
| A12 | [[09-Entradas/Referencias UI 2026-10-02/Administrador/A12-exportacion-admin.jpeg]] · Filtros y formatos | UI-11 · F5-FE-03 | SRC-02 pp. 6–7; formatos finales sujetos a DEC-09 |
| A13 | [[09-Entradas/Referencias UI 2026-10-02/Administrador/A13-dashboard-admin.jpeg]] · Resumen inicial con KPI y gráficos | UI-21 · F5-FE-01 | Desglose visual de reportes SRC-02 pp. 5–6; no duplicar fuente de cifras |

**Sin imagen admin móvil/tablet:** todas las A01–A13 son escritorio. SRC-02 p. 8 exige panel usable y probado en escritorio, tablet y móvil; la implementación deberá diseñar navegación compacta, tarjetas/listas o desplazamiento de tabla justificado, formularios de una columna y gráficos legibles. Tampoco se aportó imagen de login admin (UI-01).

## Reglas para usar estas referencias en tareas FE

1. Abrir la imagen asignada y las páginas de PDF indicadas antes de diseñar cada UI-ID. Mantener jerarquía, navegación, componentes, tono visual y relación escritorio/móvil del cliente; adaptar el admin móvil con los criterios de SRC-02 p. 8.
2. Separar **hecho de la fuente**, **mockup ilustrativo** y **decisión pendiente**. No copiar valores de ejemplo ni usar las fotos/logos JPEG como activos finales sin permisos y fuente autorizados. La denominación `MOTO LOYALTY` pertenecía a la referencia original; DEC-20 pide «Zontes» en ambos sidebars para F9.
3. Confirmar el contrato de BE, rol, propiedad y estados de carga/vacío/error/éxito para cada acción. El total agregado de puntos es informativo: saldo, vencimiento y canje se validan por marca según contrato. Todas las vistas que muestran saldo usan la misma fuente autorizada.
4. En cliente comprobar al menos escritorio, tablet y móvil; la barra inferior móvil da accesos principales y el menú da acceso a todas las secciones. Las tablas de historial y canjes pasan a tarjetas legibles; filtros pueden desplazarse dentro de su fila sin provocar scroll horizontal de página.
5. En admin comprobar los mismos tres tamaños aunque no haya capturas móviles. Ningún control funcional desaparece en el cambio de tamaño. Probar foco/teclado, contraste, controles táctiles, desbordes y estados reales con capturas de implementación por UI-ID.

## Adenda visual SRC-06 (2026-10-03)

[[09-Entradas/Referencias UI 2026-10-03/Manifiesto|SRC-06 p. 4]] aporta una nueva imagen de Inicio cliente para **UI-13/F8-FE-05**, complementaria de C08. Guía jerarquía, tarjetas claras, fondo suave y acento violeta; cifras, fotos y logotipos son ilustrativos y su uso como activos depende de DEC-11/19. No hay variante móvil de esta imagen: F8-I-04 prueba escritorio/tablet/móvil. El nuevo PDF convierte A02/UI-23 en requisito de importación propuesto para F8, sujeto a sustituir expresamente DEC-16; la tabla histórica A02 conserva su procedencia original. A06/UI-19 y A11/UI-10 quedan como referencias históricas de vistas que SRC-06 pide retirar del menú; A09/UI-12 se mantiene con nuevo nombre de menú y título. Ver [[02-Arquitectura/Impacto SRC-06 y decisiones F8]].

## Adenda F9 — asignación de referencias (2026-10-05)

SRC-07 cambia el objetivo de diseño sin modificar los JPEG preservados. **C02 → UI-17/F9-FE-01:** conservar estructura de marcas y su adaptación móvil, retirar el botón «Marca activa». **C03 → UI-18/F9-FE-02:** conservar cuenta y edición permitida, retirar vínculo con clientes existentes e información de marca. **C08 + SRC-06 p. 4 → UI-13/F9-FE-03:** conservar jerarquía y datos reales, retirar «Cómo ganar puntos»/«Explorar catálogo», dejar CTA «Ver novedades». **UI-28/F9-FE-05:** destino Novedades en sidebar/menú cliente; sin mockup aislado. **A01–A13 + C01–C10 → shell compartido/F9-FE-04/05:** las imágenes orientan estructura y responsividad, mientras la paleta propuesta [[02-Arquitectura/Paleta Zontes propuesta F9]] y el texto «Zontes» sustituyen el tema/copy provisional cuando se ejecute F9. Admin móvil no tiene mockup; se diseña y prueba en tres anchos. Ver [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]].

## Adenda SRC-09 — imágenes de Inicio y acceso cliente (2026-10-05)

[[09-Entradas/Referencias UI 2026-10-05/Manifiesto de imagenes F9]] preserva cuatro referencias nuevas y su SHA-256. **F9-R01 → UI-13/F9-FE-03:** composición desktop/móvil del card hero, no asset de producto; sus textos y botones antiguos ceden a DEC-20. **F9-R02 → UI-13/F9-FE-03:** imagen panorámica destinada al card hero. **F9-R03 → UI-02/F9-FE-06:** panel visual del formulario de ingreso cliente. **F9-R04 → UI-02/F9-FE-06:** panel visual del formulario de crear cuenta cliente. C09/C10 siguen describiendo el flujo de verificación/registro; R03/R04 asignan imágenes nuevas a sus formularios. El login admin UI-01 no recibe estas imágenes. En móvil revisar encuadre/orden de lectura, no asumir que los JPEG verticales son mockups completos de formularios.

## Puntos que requieren decisión antes de implementar

- **DEC-04:** si la fuente legacy asocia varias marcas por correo y qué hace exactamente “Vincular nueva marca”; la regla aprobada de coincidencia por correo sigue vigente. No implementar asociación manual por ver un botón en C02.
- **DEC-07/08:** comprobante, variantes y estados de canje; campos de perfil editables, contraseña y preferencias; no inventar mutaciones o permisos.
- **DEC-09/10/11:** semántica de KPI/exportación, tipo de contenido, identidad final, licencias de imágenes/logos/fuentes.
- **DEC-16:** A02 propone una fuente/carga CSV de clientes existentes que no figura en los requisitos aprobados y puede alterar la integración legacy. Queda inventariada, fuera del alcance comprometido hasta decisión de Usuario.

[[03-Modulos/Mapa de vistas frontend]] contiene el inventario de UI-ID y [[05-Desarrollo/Plan por fases]] asigna los lotes FE. Ninguna imagen prueba que la app exista o que la responsividad ya esté verificada.
