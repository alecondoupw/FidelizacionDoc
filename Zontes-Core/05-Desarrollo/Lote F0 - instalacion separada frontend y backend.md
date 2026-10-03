---
title: "F0 — Instalación separada de frontend y backend"
tags: [zontes, fase-0, instalacion]
status: planificado-no-iniciado
updated: 2026-10-02
---

# F0 — Instalación separada de frontend y backend

Paulo pidió el 2026-10-02 que F0, **cuando se inicie**, instale y verifique **frontend Next.js** y **backend Express.js** en ubicaciones separadas que indicará **al abrir esa fase**. F0 está planificada, **no iniciada**: no se definieron rutas, no se creó código y no se instalaron paquetes. `Zontes-Core/` sigue siendo el **baúl de Obsidian y memoria canónica**: aquí van decisiones, tareas y evidencias; el código y los paquetes van sólo en las ubicaciones operativas que confirme. Los PDF SRC-01/02/03 definen el producto y la [[02-Arquitectura/Base tecnica documentada]], pero no proporcionan rutas ni proyectos Firebase.

## Al iniciar F0, antes de escribir código

- [ ] **Preguntar entonces a Paulo**, no antes: ruta absoluta de frontend y de backend, si ya existen, y si serán dos repositorios Git o dos carpetas de un repositorio compartido (DEC-01). Registrar literalmente su respuesta en [[05-Desarrollo/Entorno local]] y [[02-Arquitectura/Decisiones tecnicas]].
- [ ] Inspeccionar ambas rutas antes de escribir: contenido existente, manifiestos, estado Git y versiones de runtime. Conservar cambios previos y resolver cualquier conflicto antes de inicializar.
- [ ] Elegir una versión de Node.js y un gestor de paquetes compatibles con las versiones actuales de Next.js/Express y documentarlos junto con lockfiles. Verificar requisitos en documentación oficial al ejecutar F0; no fijar números desde los PDF.

## F0-FE-03 · instalación frontend

**Ubicación:** ruta FE que indique Paulo. **Base:** SRC-02 pp. 11–13 y SRC-03 p. 11. **Salida:** aplicación Next.js/TypeScript que compila y arranca localmente, con estructura para cliente/admin y sin pantallas presentadas como producto terminado.

- [ ] Inicializar o adaptar Next.js + TypeScript en la ruta FE, con gestor/lockfile acordados y scripts reproducibles.
- [ ] Configurar Tailwind CSS y base de componentes shadcn/ui según versiones compatibles; instalar Lucide React, React Hook Form, Zod, Recharts, TanStack Table y date-fns donde corresponda. Registrar qué se instaló y por qué.
- [ ] Instalar SDK cliente de Firebase para Auth; dejar variables de entorno **por nombre**, sin valores ni credenciales en el Core. No conectar proyecto real hasta DEC-02 y acceso autorizado.
- [ ] Elegir **fetch o Axios** como estándar de HTTP según SRC-02 p. 13 / SRC-03 p. 12 y registrar la decisión en el contrato. No instalar ambas opciones como estándar por inercia.
- [ ] Configurar ESLint + Prettier de forma compatible con Next.js y comprobar formato/lint/build. Preparar navegación/esqueleto técnico para roles sin inventar datos de negocio.
- [ ] Documentar comandos de instalación, desarrollo, build, lint y pruebas en el repositorio FE y registrar versiones/resultados en [[05-Desarrollo/Entorno local]].

## F0-BE-03 · instalación backend

**Ubicación:** ruta BE que indique Paulo. **Base:** SRC-02 pp. 11–15 y SRC-03 pp. 11–13. **Salida:** API Express/TypeScript que compila y arranca localmente, con validación/errores y frontera de autorización preparados, sin eventos ni saldos ficticios presentados como funcionales.

- [ ] Inicializar o adaptar Express.js + TypeScript con scripts de desarrollo, build y arranque reproducibles.
- [ ] Instalar Firebase Admin SDK, Zod y date-fns; configurar ESLint + Prettier y dependencias de desarrollo estrictamente necesarias. Mantener Admin SDK sólo en backend.
- [ ] Preparar configuración por variables de entorno **sin secretos en Git ni en el Core**. No crear administradores, conectar base legacy ni usar credenciales reales en F0 sin autorización específica.
- [ ] Crear una prueba de arranque/salud local sin datos de producto y una respuesta de error consistente. Definir, sin implementar negocio prematuro, el lugar donde Express verificará ID token, rol, estado, propietario y marca.
- [ ] Documentar comandos de instalación, desarrollo, build, lint y pruebas en el repositorio BE y registrar versiones/resultados en [[05-Desarrollo/Entorno local]].

## F0-I-02 · instalación integrada y puerta de salida

- [ ] Confirmar que FE y BE viven en ubicaciones distintas, con manifiesto y lockfile propios; si Paulo elige un Git compartido, mantener paquetes y scripts separados.
- [ ] Correr instalación limpia, lint, build y pruebas/smoke de **cada lado**; registrar comando, versión, salida y revisión. Una compilación no demuestra reglas de negocio.
- [ ] Probar una llamada local FE→BE a un endpoint de salud sin token ni datos personales; documentar URL/configuración por nombre y errores de conectividad. El flujo protegido Firebase requiere DEC-02/03 y se prueba en F1.
- [ ] Fijar contrato inicial I-01/I-02 de [[02-Arquitectura/Contratos de integracion por flujo]] con roles, errores, fechas y respuestas; identificar lo que depende de DEC-04 sin inventar el esquema legacy.
- [ ] Actualizar [[05-Desarrollo/Progreso]], [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]] con evidencia de F0. Marcar F0 completa **sólo** cuando rutas, instalación, smoke FE/BE y documentación estén verificados.

## Dependencias que no se fuerzan en F0

SheetJS y `@react-pdf/renderer` se instalan al concretar formatos/comprobantes en DEC-07/09; Firebase Storage se habilita cuando existan archivos autorizados. Postman es herramienta manual de API, no requisito para que la aplicación arranque. La identidad visual final y los assets de DEC-11 se aplican en las tareas UI, sin bloquear la instalación técnica. Los mockups se mantienen como referencias, no como activos publicables.

## Después de la puerta F0

Crear dentro de este Core los lotes ejecutables **F1–F7**, uno por alcance verificable, usando [[05-Desarrollo/Plantilla de lote de trabajo]]: fuente/página, UI-ID o regla, responsable, rutas FE/BE, contrato, decisión pendiente, aceptación, prueba y evidencia. Basarlos en [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]], [[03-Modulos/Mapa de vistas frontend]] y [[05-Desarrollo/Plan por fases]]. No marcar lote listo para implementar si depende de una decisión material aún abierta. El código de esos lotes permanece en los repositorios operativos, nunca en este baúl.
