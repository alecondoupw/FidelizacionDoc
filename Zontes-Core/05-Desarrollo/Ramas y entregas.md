---
title: "Ramas, contratos y entregas"
tags: [zontes, entregas]
status: propuesto
updated: 2026-10-03
---

# Ramas, contratos y entregas

DEC-01 resuelta el 2026-10-03: dos repositorios Git independientes, [FidelizacionFronted](https://github.com/alecondoupw/FidelizacionFronted) y [FidelizacionBackend](https://github.com/alecondoupw/FidelizacionBackend), rama `main`; el Core vive en [FidelizacionDoc](https://github.com/alecondoupw/FidelizacionDoc). Rutas locales en [[05-Desarrollo/Entorno local]]. Estrategia de ramas por lote (propuesta, no aprobada): rama `f<n>/<id-lote>` por repo, PR con evidencia y enlace al lote; sin CI todavía. Por defecto, cada lote define su frontera de archivos; cambios FE/BE coordinados mediante contrato versionado y una prueba conjunta. No renombrar endpoints, payloads o reglas de fecha sólo desde uno de los lados. Entrega = revisión de código propia de cada repositorio + evidencia de integración + actualización de este Core. Nada de push, despliegue ni merge externo sin solicitud/autorización correspondiente.

Checklist de entrega por lote: decisión vigente; contrato actualizado; pruebas unitarias/integración pertinentes; revisión de seguridad y datos; UI states/accesibilidad si hay vista; cambios documentados; regresión del flujo afectado; riesgos residuales visibles. Ver [[05-Desarrollo/Plan por fases]] y [[05-Desarrollo/Criterio de terminado]].
