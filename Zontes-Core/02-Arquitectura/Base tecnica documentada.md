---
title: "Base técnica documentada por los PDF"
tags: [zontes, arquitectura, fuentes]
status: base-documental
updated: 2026-10-02
---

# Base técnica documentada por los PDF

SRC-02 pp. 11–15 incorpora estas tecnologías como **base de desarrollo**; SRC-03 pp. 11–13 las reitera como stack propuesto y precisa observaciones. Paulo indicó que los PDF definen el avance del proyecto. Se toma esta base como referencia del plan y los contratos, sin confundirla con paquetes instalados, cuentas disponibles o despliegue aprobado. Una sustitución de proveedor/arquitectura requiere decisión de Paulo. La estructura heredada `nextjs+nestjs` es sólo plantilla del Core: **el backend documentado es Express, no NestJS**.

| Capa | Tecnología documentada | Responsabilidad y límite |
| --- | --- | --- |
| Interfaz | Next.js + TypeScript | Cliente y administrador; rutas, renderizado, formularios y presentación. No duplica reglas sensibles de Express. |
| API | Express.js + TypeScript | Verifica token, rol, estado, propietario/marca y entradas; centraliza usuarios, puntos, canjes, reportes y exportación. |
| Identidad | Firebase Authentication | Inicio de sesión/registro cliente y autenticación admin precreado. El frontend recibe ID token; Express lo verifica con Firebase Admin SDK. No crear sistema paralelo de contraseñas en Express. |
| Datos | Cloud Firestore | Usuarios, reglas, movimientos, beneficios, canjes, contenido y configuración; modelar colecciones/índices por consultas reales de las pantallas. Operaciones críticas atómicas y trazables. |
| Archivos | Firebase Storage | Imágenes y archivos cuando se utilicen; comprobantes privados con acceso autorizado. No implica que los JPEG de referencia tengan licencia de publicación. |
| Acceso servidor | Firebase Admin SDK | Sólo en Express, nunca en el navegador. Omite reglas de Firestore: la API aplica autorización en cada operación. |
| Estilos/componentes | Tailwind CSS, shadcn/ui, Lucide React | Sistema responsive, componentes personalizados al diseño y iconografía coherente. |
| Formularios/validación | React Hook Form y Zod | Validación UX en FE y validación independiente en Express; compartir esquemas sólo con versionado acordado. |
| Datos visibles | Recharts, TanStack Table, date-fns | Gráficos admin, tablas/filtros y manejo de fechas; la fecha oficial de vencimiento viene del BE. |
| Exportación/documentos | SheetJS (xlsx), React PDF | Excel/CSV si se habilitan; concretar `@react-pdf/renderer` para generación React o resolver comprobante en BE si se exige emisión fiable en servidor. Formatos finales y ubicación de generación siguen abiertos. |
| HTTP y herramientas | **fetch o Axios**, Postman, ESLint + Prettier | Escoger un cliente HTTP como estándar; Postman para pruebas/documentación manual; calidad y formato del código. Ninguna elección alternativa implica ambos clientes principales. |

## Flujo protegido de referencia

`Next.js → Firebase Auth (ID token) → petición HTTP/JSON a Express → Admin SDK verifica token → Express autoriza rol, estado, propietario y marca → Firestore/transacción → respuesta limitada a datos autorizados → Next.js presenta estado` (SRC-02 p. 15). Para cada ruta real, el contrato define actor, request/response, errores, paginación, zona/fechas, idempotencia y prueba. Las rutas literales siguen pendientes: ver [[02-Arquitectura/Modelo de datos y contratos]].

## Distinciones que siguen abiertas

- **DEC-01:** la forma física del repositorio compartido de SRC-01 p. 2 y las rutas/ownership reales de FE_REPO y BE_REPO. Dos líneas de trabajo no prueban dos repos Git.
- **DEC-02:** proyecto(s) Firebase, cuentas, ambientes, cuotas/costes, permisos y custodio. La pregunta ya no es si los PDF contienen el stack, sino cómo habilitarlo y si Paulo ordena alguna excepción.
- **DEC-04/05:** contrato de base legacy y origen de eventos; la documentación no entrega API/esquema ni credenciales.
- **DEC-07/09/13:** generación autorizada de comprobantes, formatos exportables y despliegue/operación.

No se crean repositorios, servicios, credenciales ni instalaciones a partir de esta nota. En los entregables distinguir **base documentada**, **decisión operativa**, **implementación** y **prueba ejecutada**.
