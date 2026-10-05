---
title: "F9-FE-06 — Imágenes de ingreso y registro cliente"
tags: [zontes, lote, f9, frontend]
status: pendiente
fase: F9
frente: FE
updated: 2026-10-05
---

# F9-FE-06 — Imágenes de ingreso y registro cliente

| Campo | Contenido |
| --- | --- |
| Fuente | Petición directa de Usuario y [[09-Entradas/Referencias UI 2026-10-05/Manifiesto de imagenes F9\|SRC-09]]; UI-02; F1-FE-01 existente |
| Objetivo | Mostrar la imagen específica de cada flujo en el panel/card visual del formulario de cliente: F9-R03 en `/ingresar` y F9-R04 en `/registro`. |
| Repositorio | FE_REPO Next.js de [[05-Desarrollo/Entorno local]]; copiar los assets desde este Core al directorio de imágenes de producto al implementar, conservando procedencia. BE_REPO sin cambios. |
| Depende de | F9-D-01; F1-FE-01 existente; F9-FE-04 para coherencia de superficies y controles. |
| Contrato | Autenticación, registro por pasos, verificación y permisos sin cambios; UI-01 `/admin/ingresar` no recibe estas imágenes. |
| Prueba | F9-T07: rutas cliente `/ingresar` y `/registro`, escritorio/tablet/móvil, carga, foco, fallos de imagen y pasos de registro. |

## Posición y responsividad

- [ ] `/ingresar`: [[09-Entradas/Referencias UI 2026-10-05/F9-R03-ingresar-panel-cliente.jpg|F9-R03]] ocupa el **panel visual contiguo** al card del formulario de inicio de sesión. En escritorio se presenta como composición de dos columnas con el formulario íntegro y visible; no es fondo de los campos ni sustituye el encabezado del formulario.
- [ ] `/registro`: [[09-Entradas/Referencias UI 2026-10-05/F9-R04-registro-panel-cliente.jpg|F9-R04]] ocupa la **misma posición visual** junto al card de crear cuenta, durante los pasos de registro; no mezclar imágenes entre rutas.
- [ ] En 768/375 px el panel se apila antes del formulario o se adapta como encabezado visual compacto; el usuario llega al primer campo sin obstáculos, puede completar los pasos y ver errores/confirmaciones. Mantener proporción de 1086×1448 o un encuadre revisado que preserve frase, logos y vehículos; sin estirar ni cortar contenido clave.
- [ ] Formularios y mensajes siguen siendo HTML accesible y funcional si la imagen falla o tarda. Definir `alt` según la regla del manifiesto; reservar dimensiones para evitar saltos y usar optimización de imagen de Next.js con tamaños adecuados. No usar las frases integradas en la foto como etiquetas de campos.
- [ ] Verificar que el tema Zontes F9 convive con las imágenes sin filtros que alteren sus colores ni contraste del formulario; comprobar teclado, foco, targets táctiles y ausencia de scroll horizontal.

**Evidencia futura:** revisión FE identificada, pruebas F9-T07 y capturas en [[05-Desarrollo/Testing]]. Índice: [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]]. No marcar implementado por haber guardado las imágenes en el Core.
