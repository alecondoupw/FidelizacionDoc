---
title: "Criterio de terminado"
tags: [zontes, calidad]
status: propuesto
updated: 2026-10-02
---

# Criterio de terminado

Un lote sólo está terminado si cumple su objetivo observable, respeta reglas y decisiones, tiene FE/BE integrados cuando corresponde, pruebas positivas y negativas ejecutadas, evidencia reproducible y documentación actualizada. Falla cualquiera de estos puntos → parcial. **F0 exige ambas instalaciones separadas y reproducibles, lint/build/smoke por repositorio y llamada local FE→BE, con rutas confirmadas por Usuario al iniciar la fase; un plan escrito no cierra F0.** Los mocks son válidos para exploración de UI, no para marcar un flujo de negocio completo. Nadie infiere datos de producción, disponibilidad o rendimiento desde una demo local.

Para frontend: cotejo con fuente visual aprobada y guía anti-slop, estados completos, responsive, teclado/foco/lectura, copy y errores útiles. Para backend: permisos en servidor, idempotencia/transacción donde aplica, historial, aislamiento por marca, validación de entrada y manejo de fallos. Para F7 se suman manuales, demo, backup/restauración y despliegue real **sólo tras autorización y verificación**. Ver [[05-Desarrollo/Testing]].
