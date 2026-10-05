---
title: "Manifiesto de imágenes F9 — Inicio y acceso cliente"
tags: [zontes, fuentes, ui, f9]
status: inventariado
updated: 2026-10-05
---

# Manifiesto de imágenes F9 — Inicio y acceso cliente

**SRC-09:** cuatro imágenes aportadas directamente por Usuario el 2026-10-05 para ampliar la fase F9. Los archivos de esta carpeta son copias de los originales, sin edición, con nombres estables. Las frases, cifras y botones dibujados en una captura de interfaz son referencia visual; el pedido escrito de Usuario y DEC-20/22 definen el comportamiento vigente.

| ID | Archivo preservado | Original aportado | Tamaño | SHA-256 | Asignación |
| --- | --- | --- | --- | --- | --- |
| F9-R01 | [[09-Entradas/Referencias UI 2026-10-05/F9-R01-inicio-composicion-cliente.png]] | `codex-clipboard-b038d8fa-ed64-4984-8bd8-531e8b367b08.png` | 1600×900 PNG | `1502ACD70405540A9AF6F33056DF71EB3D2DB2222AC930BE16EAC817DE1E7706` | **Referencia de composición** UI-13/F9-FE-03: card hero de escritorio y móvil. No usar la captura como fondo ni como pantalla final. |
| F9-R02 | [[09-Entradas/Referencias UI 2026-10-05/F9-R02-inicio-banner-zontes-kiden-niu.jpeg]] | `WhatsApp Image 2026-10-05 at 12.34.41 AM.jpeg` | 1600×533 JPEG | `5E4756C42E771E15526B64BDB7A572D1D8062B061AF9A2607DB8808F6EFE1EFD` | **Imagen destinada al card hero** UI-13/F9-FE-03: panorama de tres vehículos y logotipos sobre paisaje. |
| F9-R03 | [[09-Entradas/Referencias UI 2026-10-05/F9-R03-ingresar-panel-cliente.jpg]] | `codex-clipboard-fc65c421-6b79-4eb5-b543-039b3248ba81.jpg` | 1086×1448 JPEG | `A4D0935E2CE5BA7CA90FD962D862795F822584D056916BCA5FADA343C72D1AA9` | **Imagen del panel/card visual de `/ingresar` cliente** UI-02/F9-FE-06. Frase de acceso integrada en la imagen. |
| F9-R04 | [[09-Entradas/Referencias UI 2026-10-05/F9-R04-registro-panel-cliente.jpg]] | `codex-clipboard-d31ec7e2-2342-467f-b96f-fbf61cb363b9.jpg` | 1086×1448 JPEG | `2030E6061E12AA47C396848C4472ED0F9D3B7FDABE0234C36D45233CE504B2BB` | **Imagen del panel/card visual de `/registro` cliente** UI-02/F9-FE-06. Frase de cuenta única integrada en la imagen. |

## Lectura de las referencias

- F9-R01 muestra la **ubicación y proporción** del hero: card ancho inmediatamente bajo el encabezado en escritorio; card compacto bajo el header en móvil. Sus textos «MOTO LOYALTY», «Explorar catálogo» y «¿Cómo ganar puntos?» son históricos y **no** se reintroducen: F9 mantiene sidebar «Zontes», CTA «Ver novedades» y retira «Cómo ganar puntos» (DEC-20).
- F9-R02 es el contenido visual para ese hero, no una captura de UI. El texto/CTA de Inicio se monta como HTML sobre el área clara de la izquierda en escritorio; vehículos y logotipos quedan a la derecha. No duplicar los logotipos que ya forman parte de la imagen. En móvil, ajustar encuadre o separar el texto de la imagen dentro del card para conservar los tres vehículos y las tres marcas legibles; nunca recortar un vehículo o logotipo sin revisión visual.
- F9-R03 corresponde **sólo a iniciar sesión del cliente**; F9-R04 corresponde **sólo a crear cuenta del cliente**. Ambos van en el panel visual asociado al formulario, no dentro de los campos de entrada. En escritorio, panel visual y formulario se ven simultáneamente; en móvil, el panel pasa antes del formulario en el flujo de lectura o se adapta a un encabezado visual legible, sin ocultar inputs, errores ni pasos de registro. El acceso admin (`/admin/ingresar`, UI-01) conserva su diseño actual salvo otra indicación de Usuario.
- Las imágenes verticales incluyen texto y logotipos integrados. Mantener la copia proporcionada sin aplicar filtros cromáticos ni superponer la misma frase/logos. El formulario debe tener título e instrucciones accesibles por HTML aunque la imagen no cargue. Si el texto de la imagen se comunica también en HTML, usar `alt=""` para evitar repetición; si no, redactar un `alt` breve que lo transmita. No usar la imagen como único modo de comunicar errores, pasos o requisitos.

**Aplicación y prueba:** [[05-Desarrollo/Lotes/F9-FE-03 - Simplificar Inicio y CTA de Novedades]], [[05-Desarrollo/Lotes/F9-FE-06 - Imagenes de ingreso y registro cliente]] y [[05-Desarrollo/Lotes/F9-I-01 - Regresion visual y funcional de ambas vistas]]. Capturas reales en 1280/768/375 px y verificación de carga, recorte, contraste, navegación por teclado y peso/LCP. El material se incorporó al Core como referencia y activo solicitado; aún no se añadió al repositorio frontend.
