---
title: "Datos y accesos de demo - 2026-10-07"
tags: [zontes, demo, manual]
status: verificado
updated: 2026-10-07
---

# Datos y accesos de demo

## Entorno y limites

- Firebase: fidelizacion-dev0, colecciones sin prefijo. Datos nuevos completamente ficticios, dominio ejemplo.test.
- Se conservaron las cuentas y los registros anteriores. Se simplificaron las contrasenas de las dos cuentas creadas para Paulo y se agregaron nueve cuentas nuevas.
- Las contrasenas simples son para esta demo de desarrollo. Se guardan solo en E:/Repositorios/Hackathon/MainRepo/Fidelazacion/CREDENCIALES-PRUEBA.local.md, excluido de Git.
- Las cuentas sinteticas se marcaron con correo verificado para poder usar el sistema sin recibir mensajes reales.
- El historial de demo simula operaciones de los ultimos 30 dias, en orden cronologico. No representa operaciones comerciales reales.

## Acceso

| Uso | Correo | Ruta local |
| --- | --- | --- |
| Administrador principal | carlos.mendoza.demo@ejemplo.test | http://localhost:3000/admin/ingresar |
| Administradora adicional | valeria.rivas.admin.demo@ejemplo.test | http://localhost:3000/admin/ingresar |
| Cliente recomendado, las tres marcas | sofia.rojas.demo@ejemplo.test | http://localhost:3000/ingresar |
| Cliente Zontes creado antes | cliente.zontes@ejemplo.test | http://localhost:3000/ingresar |
| Caso sin vinculo | elena.morales.demo@ejemplo.test | http://localhost:3000/ingresar |
| Caso desactivado, ingreso rechazado | bruno.castillo.demo@ejemplo.test | http://localhost:3000/ingresar |

## Datos por modulo

| Modulo | Datos y escenarios |
| --- | --- |
| Administradores y clientes | 11 cuentas de demo documentadas: 2 administradores y 9 clientes; clientes de una o varias marcas, un cliente sin vincular y uno desactivado. |
| Importacion | 3 lotes nuevos, uno por marca; 6 contactos ficticios pendientes de registro; filas duplicadas y con correo invalido para mostrar los reportes de validacion. |
| Reglas | 12 combinaciones marca/evento disponibles. Se agregaron 10 y se respetaron las 2 previas. |
| Beneficios | 15 beneficios nuevos, 5 por marca; accesorios, ropa, servicios, descuentos y experiencias. Tallas, opciones agotadas, ultimas unidades y disponibilidad futura. |
| Puntos e historial | 96 otorgamientos nuevos, asignaciones manuales y eventos de integracion simulados; fechas de vencimiento distintas, vencimientos procesados y devoluciones por anulacion. |
| Canjes | 12 canjes nuevos: 4 emitidos, 3 entregados, 3 vencidos y 2 anulados. |
| Publicaciones | 15 contenidos nuevos: noticias, promociones y eventos; publicados, programados, finalizados e inactivos. |
| Dashboard y reportes | Datos de las tres marcas durante los ultimos 30 dias; actividad mensual, clientes, puntos y canjes. |
| Exportaciones | CSV y XLSX de clientes, movimientos, canjes y actividad; reportes CSV de las tres importaciones. |
| Imagenes y comprobantes | La UI actual representa los beneficios con ilustraciones por categoria y el Inicio con un banner ilustrado. No tiene campos de fotografia en los contratos. Se generaron y verificaron QR SVG y comprobantes PDF de los cuatro canjes de Sofia. |

## Recorrido sugerido

1. Ingresar como administrador y revisar Dashboard, Clientes, Reglas, Beneficios y Publicaciones por marca.
2. En otra ventana privada, ingresar como Sofia y abrir Inicio, Mis puntos, Historial, Catalogo, Mis canjes, Novedades y Mis marcas.
3. Sofia tiene 2320 puntos disponibles despues de la carga: zontes: 770, kiden: 750, niu: 800. Los saldos cambian al realizar nuevos canjes o vencer puntos.
4. En Canjes en mostrador, copiar un codigo de la tabla siguiente y pulsar Buscar. Si se marca entregado o se anula, el estado cambiara de verdad.
5. Revisar Reporte de actividad, Reporte de canjes y Exportar datos. Los archivos salen del mismo libro de movimientos.

### Codigos de Sofia

| Codigo | Estado inicial | Marca | Beneficio |
| --- | --- | --- | --- |
| ML-BCAV-2TKV-T6 | vencido | niu | Cupon para repuestos NIU (demo) |
| ML-841B-ZXFW-AD | entregado | kiden | Kit de seguridad para ruta KIDEN (demo) |
| ML-GAGC-7D32-H2 | anulado | zontes | Camiseta del club ZONTES (demo) |
| ML-62ZB-G70A-0Z | emitido | zontes | Revision preventiva ZONTES (demo) |

## Verificacion ejecutada

- 29 verificaciones de login, roles y endpoints, incluidos acceso admin rechazado al cliente y perfil rechazado al cliente desactivado.
- 22 pantallas recorridas en Chrome con Playwright, con inicio de sesion real contra el backend en localhost:4000. Errores de consola/API observados: 0.
- 12 saldos de marca comprobados: saldo materializado = remanentes de lotes = suma de movimientos; stock sin negativos.
- Conciliacion del conjunto completo: 129 movimientos, 129 asientos y 17 canjes. Cero faltantes, diferencias, asientos sobrantes o indices desactualizados.
- Comprobantes PDF y QR SVG validos; XLSX con cabecera ZIP y CSV no vacios.

## Archivos locales

- Credenciales: E:/Repositorios/Hackathon/MainRepo/Fidelazacion/CREDENCIALES-PRUEBA.local.md.
- Copia previa de Firestore, metadatos de Auth, CSV de importacion, exportaciones, QR, PDF, capturas y evidencia: E:/Repositorios/Hackathon/MainRepo/Fidelazacion/.demo-local/.
- Script local con pasos reanudables e identificadores de idempotencia: E:/Repositorios/Hackathon/MainRepo/Fidelazacion/DEMO-SISTEMA.local.mjs.
- El JSON de la cuenta de servicio, las credenciales, el script y los archivos privados de demo quedan excluidos de Git mediante .git/info/exclude en MainRepo.
- No se hizo commit, push ni despliegue en esta carga.

## Actualizacion del frontend con imagenes

El 2026-10-07 se actualizo esta copia de `main` desde `ca67b26` hasta `eea0a762a288419236a4369fc1ad3c512dce7ecb` mediante `git pull --ff-only origin main`. La nueva version incluye las tres imagenes de F9 en `public/imagenes`: ingreso cliente, registro cliente y hero de Inicio. Se verificaron las tres rutas en Chrome: imagen visible y cargada, login real de Sofia correcto y cero errores de consola/API. Evidencia local: `.demo-local/verificacion-imagenes-f9.json` y capturas `f9-*.png`.

Las 22 pantallas descritas arriba se verificaron durante la carga de datos con la version anterior `ca67b26`. La descripcion de ilustraciones sin fotografias corresponde a esa version. En `eea0a76` el catalogo conserva ilustraciones por categoria y las fotografias nuevas estan en `/ingresar`, `/registro` y `/inicio`. La base de datos y las credenciales de demo siguen vigentes.
## Nombre oficial de la aplicacion

Por solicitud de Paulo el 2026-10-07, el nombre de la aplicacion es **Zontes** en todos los accesos y en los titulos de pagina. Los comprobantes PDF tambien usan Zontes como autor y encabezado. Se actualizaron 16 archivos del frontend y el generador de comprobantes del backend. Las cuatro pruebas existentes de navegacion pasaron; los cuatro PDF de ejemplo de Sofia se volvieron a descargar y su autor/encabezado se verificaron. Las referencias documentales y los PDF originales del enunciado conservan sus nombres historicos. Evidencias locales: `.demo-local/verificacion-nombre-zontes.json`, `.demo-local/verificacion-pdf-zontes.json` y `.demo-local/zontes-admin-ingresar.png`.
## Cuentas genéricas añadidas

Se crearon y verificaron adminzontes@test.com (administrador) y clientezontes@test.com (cliente), a petición de Paulo. Las contraseñas están sólo en CREDENCIALES-PRUEBA.local.md. El cliente genérico comienza sin puntos. Para recorrer el escenario de tres marcas y puntos utiliza Sofia. test.com no es un dominio reservado para ejemplos; no se enviaron correos durante la creación de estas cuentas.
