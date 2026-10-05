---
title: "Lotes F9 — simplificación de interfaz e identidad Zontes"
tags: [zontes, lotes, f9]
status: planificado
updated: 2026-10-05
---

# Lotes F9 — simplificación de interfaz e identidad Zontes

**Origen:** petición directa de Usuario (SRC-07), referencia web observada SRC-08 y cuatro imágenes aportadas por Usuario (SRC-09) el 2026-10-05. Ver [[09-Entradas/Referencia web Zontes Bolivia 2026-10-05]] y [[09-Entradas/Referencias UI 2026-10-05/Manifiesto de imagenes F9]]. **Estado:** fase y tareas creadas en el Core; ningún cambio de código F9 ni prueba F9 ejecutada. F8 ya implementó partes de Inicio y conserva sus pruebas históricas; F9 define el objetivo siguiente, sin reescribir F8. FE_REPO Next.js y BE_REPO Express siguen separados, según [[05-Desarrollo/Entorno local]].

## Cadena A — alcance y vistas cliente

| Orden | Lote | Resultado observable | Depende de |
| --- | --- | --- | --- |
| 1 | [[05-Desarrollo/Lotes/F9-D-01 - Conciliar alcance visual y tokens\|F9-D-01]] · Core | DEC-20/21, mapa UI, paleta y criterios listos para implementar | SRC-07/08; DEC-11/19, ADR-12 |
| 2a | [[05-Desarrollo/Lotes/F9-FE-01 - Simplificar Mis marcas\|F9-FE-01]] · FE | UI-17 sin botón «Marca activa» | F9-D-01 |
| 2b | [[05-Desarrollo/Lotes/F9-FE-02 - Depurar Informacion de cuenta\|F9-FE-02]] · FE | UI-18 sin bloque de vínculo con clientes existentes ni información de marca | F9-D-01 |
| 2c | [[05-Desarrollo/Lotes/F9-FE-03 - Simplificar Inicio y CTA de Novedades\|F9-FE-03]] · FE | UI-13: card hero con R02 siguiendo composición R01; sin «Cómo ganar puntos»/«Explorar catálogo»; CTA «Ver novedades» | F9-D-01; F8-FE-05 |

## Cadena B — navegación e identidad compartida

| Orden | Lote | Resultado observable | Depende de |
| --- | --- | --- | --- |
| 2d | [[05-Desarrollo/Lotes/F9-FE-04 - Aplicar paleta en cliente y administrador\|F9-FE-04]] · FE | tokens comunes y estados accesibles en ambas vistas; sin confundir datos por marca | F9-D-01; aprobación del detalle de DEC-21 |
| 2e | [[05-Desarrollo/Lotes/F9-FE-05 - Sidebar Zontes y Novedades\|F9-FE-05]] · FE | «Zontes» junto al icono en ambos roles; Novedades accesible en sidebar/menú cliente | F9-D-01; F9-FE-03 para eliminar accesos duplicados |
| 2f | [[05-Desarrollo/Lotes/F9-FE-06 - Imagenes de ingreso y registro cliente\|F9-FE-06]] · FE | UI-02: R03 en ingreso y R04 en crear cuenta, panel visual junto al formulario y adaptación móvil | F9-D-01; F9-FE-04 |
| 3 | [[05-Desarrollo/Lotes/F9-I-01 - Regresion visual y funcional de ambas vistas\|F9-I-01]] · integración | navegación, imágenes, datos, 3 anchos, accesibilidad, pruebas y manuales registrados | F9-FE-01…06 |

**Interpretación de dos pedidos sobre Novedades:** dejar «Ver novedades» como única acción del banner de Inicio y crear «Novedades» como destino persistente del sidebar cliente. Si existe un acceso rápido separado «Novedades» en el cuerpo de Inicio, se retira para evitar duplicación. UI-28 y `/novedades?marca=` continúan; no cambia el filtro de marca ni la autorización.

**Límite funcional:** retirar información o controles visibles no borra vínculos, marcas, reglas, preferencias locales, puntos ni publicaciones del backend. La marca activa de ADR-12 sólo deja de ofrecerse como botón en UI-17; cualquier uso del contexto de marca en catálogo/contenido debe seguir autorizado por `/me`. No se prevé lote BE salvo que una inspección del código revele un contrato roto; se registraría como tarea y decisión nueva antes de alterar la API.

**Imágenes F9:** R01 orienta el card hero; R02 se incorpora allí sin reintroducir el copy de la captura; R03 y R04 van sólo en los paneles visuales de ingreso y registro cliente. Las copias están en el Core, no en FE_REPO.

**Puerta F9:** revisión del alcance y de la paleta propuesta, implementación FE identificada por revisión, pruebas de componente/ruta y recorrido con cliente/admin en 1280/768/375 px, foco y contraste, regresión de permisos y datos por marca; evidencia en [[05-Desarrollo/Testing]], [[05-Desarrollo/Progreso]] y manuales. El sitio público aporta inspiración cromática, no derechos sobre sus fotos, logotipo o fuente.
