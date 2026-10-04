---
title: "Manual de uso — administración y clientes"
tags: [zontes, manual, f7]
status: verificado-en-desarrollo
updated: 2026-10-03
---

# Manual de uso — administración y clientes

Entregable «manual de uso administrativo» de SRC-01 p. 2 (REQ-22), con un apartado para clientes. Describe la aplicación verificada en F1–F7 (FE `FidelizacionFronted`, BE `FidelizacionBackend`, `main`) contra el proyecto Firebase de desarrollo; las capturas por pantalla están en [[06-Estado/Evidencias/F6-revision-visual]] (datos de prueba, sin datos reales). La identidad visual es provisional (DEC-11). Despliegue y operación: [[08-Produccion/Manual de despliegue y operacion]].

## Conceptos

| Concepto | Qué significa |
| --- | --- |
| Marcas | Zontes, Kiden y NIU. Los puntos, el catálogo y el contenido son **por marca** y nunca se mezclan |
| Vínculo | Un cliente ve las marcas en las que ya era cliente según su **correo** (verificado). Si no hay coincidencia queda «no vinculado» |
| Puntos | Se ganan por eventos (compra, referido, mantenimiento, asistencia) según la regla activa de cada marca; pueden vencer si la marca tiene vencimiento activo |
| Canje | Cambio de puntos por un beneficio; genera un código `ML-XXXX-XXXX-XX` con QR que se presenta en tienda |
| Hora | Fechas y periodos en hora de Bolivia |

## Administración

### Acceso (UI-01)

Entrar por `/admin/ingresar` con la cuenta de administrador. La primera cuenta la crea el responsable técnico con `npm run admin:bootstrap`; las siguientes se invitan desde **Administradores**. Una cuenta de cliente no puede entrar al panel. En el móvil, la barra inferior muestra las secciones principales y «Más» el resto.

### Dashboard (UI-21)

Resumen de los últimos 30 días frente a los 30 anteriores: clientes, puntos otorgados, puntos utilizados y canjes. Cada indicador abre su detalle. Debajo, la evolución de 6 meses, los últimos registros y los últimos canjes. Las cifras se calculan al abrir la pantalla; **Actualizar** las vuelve a pedir.

### Usuarios

| Tarea | Dónde | Pasos y reglas |
| --- | --- | --- |
| Invitar un administrador | Administradores (UI-06) → **Nuevo administrador** | Nombre, apellido y correo. La persona recibe un correo de Firebase para definir su contraseña; hasta entonces figura con invitación pendiente |
| Desactivar o eliminar un administrador | Administradores → acciones de la fila | Pide confirmación. No se puede actuar sobre la propia cuenta ni dejar el sistema sin administradores activos |
| Buscar un cliente | Clientes (UI-07) | Filtros por marca, estado y vinculación; **Buscar por correo completo** (coincidencia exacta) |
| Ver un cliente | Clientes → **Gestionar** | Datos, puntos por marca (incluidas marcas desvinculadas) e historial de cambios con autor y fecha |
| Corregir nombre o correo | Detalle del cliente | Cambiar el correo pide confirmación: el vínculo se recalcula con el correo nuevo, la persona debe verificarlo y se cierran sus sesiones |
| Desactivar o dar de baja | Detalle del cliente → zona de baja | Desactivar impide el acceso y se puede revertir. La baja anonimiza a la persona, conserva sus movimientos y canjes para los reportes y libera el correo; no se puede deshacer |

### Puntos

| Tarea | Dónde | Pasos y reglas |
| --- | --- | --- |
| Definir cuántos puntos da un evento | Reglas de puntos (UI-04) → **Nueva regla** | Marca, evento y puntos (entero positivo). Una regla por marca y evento; se puede pausar con el interruptor. La vista previa muestra cómo lo verá el cliente |
| Configurar el vencimiento | Vencimiento (UI-19) | Por marca: activar y fijar el plazo en días, meses o años (máximo 10 años). Afecta sólo a los puntos que se otorguen después; el historial guarda cada cambio. **Procesar vencimientos** aplica de inmediato los vencidos (también corre cada noche) |
| Registrar una compra u otro evento | Registrar puntos (UI-24) → **Registrar evento** | Marca, evento y correo del cliente, que debe estar vinculado a la marca. Si la red falla y se reintenta, no se otorga dos veces. Los sistemas de facturación o CRM registran sus eventos por la API de integración con su propio número de operación |
| Corregir un saldo | Registrar puntos → **Ajuste de puntos** | Puntos positivos o negativos y un motivo obligatorio. No se puede dejar el saldo en negativo |
| Revisar movimientos | Movimientos (UI-20) | Todos los clientes por periodo, marca, tipo y evento; se exporta con los mismos filtros |

### Beneficios y canjes

| Tarea | Dónde | Pasos y reglas |
| --- | --- | --- |
| Crear o editar un beneficio | Beneficios (UI-25) | Marca, nombre, descripción, categoría, puntos, días de validez del cupón, fecha desde la que estará disponible y opciones (p. ej. tallas) con stock por opción o sin límite. Inactivo = oculto para los clientes |
| Entregar un canje en tienda | Canjes en mostrador (UI-26) | Escribir o leer el código `ML-…` del cliente, comprobar beneficio, opción y vigencia, y marcar como entregado |
| Anular un canje | Canjes en mostrador → anular | Motivo obligatorio y confirmación. Devuelve los puntos y una unidad de stock. Un canje entregado no se anula |
| Ver canjes del periodo | Reporte de canjes (UI-09) | Totales, beneficios más canjeados, por marca, y lista filtrable por estado o correo |

### Análisis y exportación

- **Actividad (UI-08):** usuarios con actividad, registros, puntos generados, utilizados y vencidos, ajustes y canjes por periodo y marca; desglose por evento.
- **Tendencias (UI-10):** evolución diaria, semanal o mensual de una métrica, comparada con el periodo anterior y entre marcas.
- **Exportar datos (UI-11):** elegir clientes, movimientos, canjes o actividad, filtros y formato (CSV para Excel en español o .xlsx). La vista previa indica cuántas filas saldrán; el máximo es 10.000. Cada exportación queda registrada en la auditoría. Los archivos contienen datos personales: guardarlos con cuidado.
- Los periodos admiten como máximo 12 meses.

### Contenido por marca (UI-12)

**Contenido por marca** → elegir la marca → **Nuevo contenido**: categoría (noticia, evento o promoción), título, texto, enlace opcional (sólo `https`), «Destacada en el Inicio» y fechas opcionales de publicación. La vista previa muestra cómo lo verá el cliente. Estados: **Programada** (aún no empieza), **Publicada** y **Finalizada**; sólo lo activo y dentro de sus fechas llega a los clientes de esa marca. Eliminar pide confirmación.

### Mi perfil (UI-22)

Cambiar el propio nombre y pedir el correo para cambiar la contraseña. El correo de un administrador no se edita (ADR-14).

## Clientes

| Tarea | Dónde | Qué ocurre |
| --- | --- | --- |
| Crear la cuenta | `/registro` (UI-02) | Nombre, correo y contraseña; llega un correo de verificación. Al verificarlo, la aplicación muestra las marcas vinculadas o avisa si el correo no coincide con ningún cliente |
| Entrar | `/ingresar` | Si el servidor estuvo inactivo, la primera carga puede tardar hasta un minuto y la pantalla lo explica |
| Ver puntos | Inicio (UI-13), Mis puntos (UI-03), Historial (UI-14) | Saldo total y por marca, próximo vencimiento y movimientos filtrables |
| Canjear | Catálogo (UI-05) → beneficio → opción → confirmar | Sólo beneficios de sus marcas. Si faltan puntos, está agotado o aún no está disponible, la pantalla lo explica. El resultado muestra el código |
| Usar un canje | Mis canjes (UI-15) → canje (UI-16) | Código, QR y vigencia; se puede descargar el comprobante en PDF. Se presenta en tienda antes de que venza |
| Ver novedades | Inicio (destacadas) y Novedades (UI-28) | Publicaciones vigentes de sus marcas |
| Mis marcas y perfil | Mis marcas (UI-17), Mi perfil (UI-18) | Marcas vinculadas; cambiar nombre y contraseña |

## Mensajes frecuentes

| Mensaje | Causa y solución |
| --- | --- |
| «Verifica tu correo…» | El correo no está verificado o el administrador lo cambió: abrir el enlace recibido y pulsar «Ya lo verifiqué» |
| «No tienes esa marca vinculada» | El correo de la cuenta no figura como cliente de esa marca: un administrador puede corregir el correo |
| «Demasiadas solicitudes…» | Límite de seguridad; esperar un minuto |
| «No pudimos conectar con el servidor» | Servidor dormido o sin conexión: **Reintentar** |
| Un error que termina en «(referencia xxxxxxxx)» | Fallo del servidor: indicar esa referencia al soporte técnico, que la busca en los registros |

Mantener según [[07-Manuales/Mantenimiento del manual]].
