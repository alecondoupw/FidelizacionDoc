---
title: "Hoja de decisiones UI y preparación de fases"
tags: [zontes, decisiones, ui]
status: pendiente-de-paulo
updated: 2026-10-03
---

# Hoja de decisiones UI y preparación de fases

Esta hoja permite revisar las diferencias entre las referencias C01–C10 (cliente, escritorio y móvil), A01–A13 (administrador, sólo escritorio), SRC-03 (flujo cliente) y SRC-02 (requisitos admin). **Ninguna opción de esta hoja está aprobada.** Los PDF describen requisitos/propuestas y los mockups ilustran pantallas; no son órdenes para implementar todo lo que aparece. Una respuesta de Paulo se registra en [[02-Arquitectura/Decisiones tecnicas]] antes de cambiar alcance, contrato o UI ejecutable.

## Decisiones para acordar antes de seguir

| Prioridad | ID vigente | Decisión concreta para Paulo | Evidencia y diferencia observada | Propuesta para revisar | Afecta |
| --- | --- | --- | --- | --- | --- |
| 1 | DEC-12 | ¿Qué recorrido tiene prioridad para el prototipo y cuál es el hito de entrega: cliente, admin o ambos? | Hay 10 mockups cliente y 13 admin; SRC-01 p. 2 exige un núcleo funcional usuarios/puntos, sin fecha definida. | Priorizar un recorrido integrado mínimo: registro/vínculo cliente → puntos/historial → regla admin, y ampliar canje/reportes por fases. | Orden de F1–F5 y criterios de demo |
| 2 | DEC-11 | ¿Se aprueba un sistema visual compartido con composición y densidad propias para cada rol? ¿Cuál es la identidad final y qué logos/fotos/fuentes se pueden usar? | SRC-03 p. 2 pide línea visual compatible con admin; C01–C10 muestran interfaz cliente más gráfica, A01–A13 tablas y datos densos. `MOTO LOYALTY` figura en ambos, pero el Core aún se llama Zontes. | Compartir colores, tipografía, iconos, componentes y estados; conservar navegación y densidad según la tarea de cada rol. Usar los JPEG sólo como referencia hasta aclarar permisos. | F0-FE-02 y toda UI; no cambia marca por inferencia |
| 3 | DEC-04 | ¿Un correo puede vincular una, dos o tres marcas? ¿Qué hace “Vincular nueva marca” cuando ya existe una cuenta? | C02/C09 muestran múltiples marcas y un botón de vínculo; SRC-02 p. 2 fija la coincidencia **sólo por correo**. | Mostrar sólo marcas confirmadas por la fuente autorizada; el botón no crea asociaciones manuales mientras no haya contrato. | F1-FE-01/02, UI-02/17, BE legacy |
| 4 | DEC-01/02 | ¿Cómo se organizará el repositorio compartido y cuáles son las rutas/responsables FE_REPO/BE_REPO? ¿Qué proyecto Firebase, cuenta y entornos se usarán? | SRC-02/03 fijan Next.js + Express + Firebase como base técnica; el Core no tiene repositorios operativos ni servicios confirmados. | Mantener esa base documental y F0 como especificación hasta que Paulo confirme rutas, recursos y acceso. | Gate F0 y arranque de F1 |
| 5 | DEC-16 | ¿Se incluye la carga CSV de clientes existentes de A02 o se descarta? | A02 la dibuja; SRC-01/02 sólo piden sincronizar con la base existente y vincular por correo, sin definir importación CSV. | Mantener UI-23/F4-FE-04 como opción fuera del alcance comprometido. Si se incluye, definir origen de verdad, permisos, deduplicación y auditoría antes de implementarla. | F4 y posible cambio de integración |
| 6 | DEC-07/08 | ¿Qué estados y comprobante tendrá el canje, y qué cambios de perfil permite cada rol? | C04/C05 reúnen detalle, éxito y cupón en composiciones; C03/A04 sugieren ajustes de cuenta. Los permisos y estados finales siguen abiertos. | Separar etapas en vistas/estados reales; permitir sólo acciones respaldadas por BE. | F1 perfil de consulta, F3 canje, F4 edición |
| 7 | DEC-09/10 | ¿Qué métricas/formatos de exportación y qué tipos de contenido por marca entran en el prototipo? | A08–A13 muestran reportes, formatos y contenido con datos de ejemplo; SRC-02 pp. 5–7 deja granularidad, formatos y contenido concreto por definir. | Mantener estructura visual de referencia y fijar datos/acciones contra contrato antes de programar. | F5–F6 |

**No requieren una decisión nueva para documentarlos:** el panel admin debe funcionar en móvil aunque A01–A13 no tengan versión móvil (SRC-02 p. 8); los mockups de cliente ya muestran un patrón móvil que se debe verificar al construirlo. También faltan imágenes de login para ambos roles: SRC-02 p. 1 y SRC-03 p. 3 permiten especificar el flujo, pero el diseño concreto se revisa dentro de F0-FE-02/F1-FE-01. Ninguna de estas ausencias autoriza a marcar una vista como probada.

## Estado real de las fases al 2026-10-03

| Fase o lote | Estado | Qué falta para empezar o cerrar |
| --- | --- | --- |
| F0-FE-01 · inventario de referencias | **Documentado y verificado** para este lote | Las 23 imágenes tienen fuente, hash, UI-ID y tarea en [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]]; A02 sigue condicionada. |
| F0 · instalación y fundaciones | **Verificada 2026-10-03; publicado en la rama `f0/base-tecnica` (FE `f29da45`, BE `747e191`)** | Rutas confirmadas (DEC-01), Next.js y Express instalados y verificados por separado, contrato v0 y evidencia en [[05-Desarrollo/Lote F0 - instalacion separada frontend y backend]] y [[05-Desarrollo/Testing]]. DEC-02 precede a conexiones reales; DEC-11/12 a diseño final/prioridades. |
| F1 · identidad y vínculo | **Lotes creados; sin código ni pruebas** | Gate F0 cumplido; faltan DEC-02/03/04 y aprobación del contrato I-01/I-02. |
| F2 · puntos | **Planificada; sin código ni pruebas** | F1 y DEC-05/06/14; ledger y reglas verificables. |
| F3–F6 · canje, administración, reportes y contenido | **Planificadas; sin código ni pruebas** | Gates de sus fases y decisiones específicas DEC-07/08/09/10. |
| F7 · entrega | **Planificada; sin despliegue** | Producto integrado y probado; DEC-13. |

**Conclusión operativa (2026-10-03):** F0 está verificada y publicado en la rama `f0/base-tecnica` (FE `f29da45`, BE `747e191`) y los lotes ejecutables F1–F7 están creados en [[05-Desarrollo/Lotes F1-F7 - indice]]; ninguno iniciado. Para abrir F1 hacen falta DEC-02, DEC-03 y DEC-04. No se debe presentar F1 ni otra fase como lista o completada por disponer de mockups.

Ver [[05-Desarrollo/Plan por fases]], [[02-Arquitectura/Decisiones pendientes]], [[03-Modulos/Mapa de vistas frontend]] y [[05-Desarrollo/Progreso]].
