---
title: "Impacto de SRC-06 y decisiones de F8"
tags: [zontes, decisiones, f8]
status: pendiente-de-decision
updated: 2026-10-03
---

# Impacto de SRC-06 y decisiones de F8

**Procedencia:** [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]], 5 páginas, aportado por Usuario el 2026-10-03 con encargo de crear cadenas de tareas. El PDF contiene requisitos de producto y una imagen ilustrativa; no autoriza por sí solo modificar repositorios operativos, datos existentes ni servicios. Los requisitos nuevos se trazan en [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] como REQ-25–28 y se planifican en [[05-Desarrollo/Lotes F8 - correcciones SRC-06]]. **Estado: tareas documentadas, implementación y pruebas pendientes.**

| Punto de SRC-06 | Estado anterior registrado | Resolución documental para planear | Puerta antes de implementar |
| --- | --- | --- | --- |
| pp. 1–2: importar CSV/XLSX por marca, sin crear cuentas; preview, vínculo y reporte | DEC-16, UI-23 y F4-FE-04: importación fuera de alcance; DEC-04 usa adaptador legacy con doble sintético | F8 añade cadena completa FE/BE/I; F4-FE-04 conserva la decisión histórica, sin reabrirse de manera implícita | **DEC-17:** Usuario confirma sustitución de DEC-16, fuente de verdad, acceso/autorización, coexistencia con legacy, política de conflictos y conservación de archivos/reportes |
| p. 1: recortar espacios del correo sin alterar su identidad | F1-BE-03 probó coincidencia de mayúsculas/espacios tras normalización; índice de correo ya existe | Auditar algoritmo e índices antes de importar o vincular; no cambiar claves existentes en silencio | **DEC-17:** tratamiento de mayúsculas, correos ya indexados y migración/reconciliación sin duplicar identidades |
| p. 3: vencimiento elegido en cada asignación, sólo suma manual, sin «Registrar evento», sin «Procesar ahora» | DEC-05/06/14 y F2: regla de vigencia por marca, panel de evento/ajuste positivo o negativo y vencimiento manual/automático | F8 separa cambio BE de formulario FE; conserva ledger, canjes y vencimientos históricos | **DEC-18:** confirmar reemplazo de vigencia por marca, origen de fecha para grants de integración y puntos previos, retirada de ajuste negativo administrativo y modo autorizado de corregir errores |
| p. 2: quitar Tendencias; renombrar Contenido por marca a Publicaciones por marca | UI-10/F5-FE-02 y UI-12/F6-FE-01 ya figuran implementadas; DEC-09 conserva series en BE | F8 modifica navegación y pantalla, sin borrar historial, reportes ni evidencia previa | **DEC-19:** confirmar si la retirada de Tendencias es sólo de UI o también de API/exportaciones; el PDF sólo exige quitar apartado y menú |
| pp. 4–5: nueva referencia de Inicio cliente | UI-13/C08 y FE F2 existentes; DEC-11 deja identidad/fotos/logos abiertos | La imagen de SRC-06 complementa C08 y guía UI-13 en F8-FE-05 | **DEC-19:** comportamiento/origen de notificaciones, alcance de búsqueda y activos visuales autorizados; no usar cifras ni fotos del mockup como datos |

**Regla de transición:** una decisión anterior de Usuario no se borra ni se marca errónea. Cuando Usuario confirme DEC-17/18/19, registrar su respuesta, fecha, alcance y efecto sobre DEC-04/05/06/09/11/14/16 en [[02-Arquitectura/Decisiones tecnicas]]. Hasta entonces los lotes F8 están planificados y bloqueados en los puntos indicados. La revisión de F1–F7 anterior sigue siendo evidencia de la versión previa, no prueba de SRC-06.

**Evaluación de orquestación F8 (2026-10-03):** presentes dependencias FE↔BE, trabajo entre sesiones, puertas humanas y una importación con efecto no idempotente; el plan necesita control persistente. **Componente declarado v1:** índice [[05-Desarrollo/Lotes F8 - correcciones SRC-06]] + estado en [[06-Estado/Tareas pendientes]]/[[06-Estado/Bitacora]], gestionados por un integrador único. Alcance: sólo F8; persistencia: archivos Git de este Core; puertas: DEC-17/18/19 y aceptación por cadena; alternativa si el flujo manual falla: pausar la tarea afectada y decidir con Usuario un runtime de orquestación antes de ejecutar escrituras. No se instala un runtime por inferencia. Cada operación BE de importación y grant tendrá clave de idempotencia; ninguna tarea con efecto se asigna simultáneamente a dos ejecutores. Una cadena puede abrirse cuando su DEC propia esté resuelta, aunque otras sigan pendientes.
