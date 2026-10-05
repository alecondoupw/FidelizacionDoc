---
title: "Guía visual y criterios de interfaz"
tags: [zontes]
status: planificado
updated: 2026-10-02
---

# Guía visual y criterios de interfaz

SRC-02 pp.8–9 define el panel administrativo; SRC-03 pp.2–10 define la experiencia cliente y pide mantener una línea visual compatible. SRC-04/05 aportan mockups concretos, asignados en [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]]. Esta nota traduce las fuentes a criterios revisables. **No es una licencia para copiar pantallas de Stripe/Linear.** La identidad final, los logotipos, las fotos y las fuentes utilizables siguen en DEC-11.

## Tokens del panel admin

- Fondo `#f1f3f7`, superficies blancas, borde frío `#eceef4`/`#e6e9f1`; gap base 8px.
- Acento índigo `#4f46e5`, hover `#4338ca`; textos `#111827`, `#5b6377`, `#8b93a7`.
- Tarjetas radio 10–16px, botones/inputs 9–11px, sombras discretas. Menú lateral y encabezado en superficies flotantes.
- Tipografía documentada: Plus Jakarta Sans; títulos 24px/800, cifras 26px/800, etiquetas 10.5–11px/700. **Comprobar legibilidad y contraste real**; no reducir contenido funcional a un tamaño difícil de leer por obedecer un ejemplo.
- Estados semánticos: verde éxito, ámbar aviso, rojo error, azul información; no depender sólo del color.
- Componentes: botones, chips, KPI, tablas sin bordes verticales, inputs, modales y switches con estados hover/focus/disabled/loading/empty/error. No degradados ni emojis.
- Escritorio: menú lateral y tablas; tablet/móvil: navegación compacta, formularios de una columna, tabla con estrategia de overflow explícita. Probar tamaños reales, no sólo reducir ventana.

## Sistema cliente descrito en SRC-03

- Fondo aproximadamente `#F7F7FB`, tarjetas blancas de radio 12–16px y sombra sutil, acento violeta/azul, positivo verde, descuento/error rojo y vencimiento/alerta naranja (p. 10). Tipografía Inter, Manrope, Aptos o similar; iconos lineales; fotografía realista de motos/accesorios sólo con derechos de uso aclarados.
- Escritorio: sidebar con Inicio, Mis puntos, Catálogo, Mis canjes, Historial, Mis marcas, Mi perfil y Cerrar sesión; topbar con saludo, fecha, buscador contextual, notificaciones y cuenta (p. 2). Móvil: header compacto, barra inferior para accesos principales y menú para las demás funciones; no ocultar secciones (pp. 2 y 9).
- Contexto multimarca: marca activa para catálogo/beneficios/contenido, acceso visible a otras marcas vinculadas, sin mostrar beneficios exclusivos de marcas no vinculadas (p. 3). Saldos y estados de canje siempre desde la misma fuente autorizada (p. 9).
- Formularios de una columna móvil, filtros desplazables dentro de su fila, tablas de historial/canjes como tarjetas, controles táctiles legibles y página sin scroll horizontal innecesario (pp. 2, 5, 7 y 9).
- SRC-03 pide línea visual compatible con admin, pero su tipografía y fondo sugeridos no coinciden exactamente con SRC-02. **DEC-11 debe fijar tokens comunes y diferencias por rol**; hasta entonces los valores anteriores son especificaciones de fuente, no un tema único aprobado.

## Adenda F9 — identidad Zontes solicitada el 2026-10-05

El índigo anterior describe la referencia y la implementación provisional F6; el objetivo cromático posterior está en [[02-Arquitectura/Paleta Zontes propuesta F9]]. SRC-07/DEC-20 también cambia el texto del sidebar a «Zontes» en cliente/admin. Los tokens exactos de DEC-21 siguen propuestos, mientras DEC-11 continúa abierta para activos licenciados. Aplicar la paleta a ambos roles sin perder los colores que distinguen datos por marca ni los estados semánticos. La versión implementada sólo se declarará tras F9-I-01.

## Puerta visual por pantalla

1. **Fuente:** SRC-02 pp.8–9 para admin o SRC-03 pp.2–10 para cliente + imagen C/A asignada y revisión identificada; documentar ausencia de mockup cuando corresponda.
2. **Objetivo:** tarea y dato que el usuario quiere ver/cambiar; mapear a API/permiso.
3. **Diseño:** jerarquía, copy, tokens, estados, navegación, responsive y accesibilidad. Evitar tarjetas KPI o gráficos sin dato útil, textos de relleno, sombras/degradados genéricos.
4. **Implementación:** componente reutilizable sólo cuando hay patrón repetido; personalizar shadcn/ui si se adopta, sin dejar aspecto predeterminado.
5. **Revisión:** captura real en desktop/tablet/móvil comparada con fuente; verificar contraste, teclado, foco, tabla, loading/empty/error y acciones peligrosas. Registrar evidencia.

Las imágenes de cliente muestran pares escritorio/móvil; las 13 imágenes admin sólo muestran escritorio. El admin móvil se diseña y prueba según SRC-02 p.8, sin fingir que existe una referencia visual aprobada. El cliente mantiene sidebar en escritorio y header compacto, barra inferior y menú complementario en móvil; el historial/canjes usan tarjetas legibles y los filtros no provocan desborde de página. Ver [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]]. DEC-11 aún define activos e identidad finales. Skills de UI como Impeccable pueden recomendarse y auditarse, pero nunca instalarse ni activar hooks sin autorización de Usuario.
