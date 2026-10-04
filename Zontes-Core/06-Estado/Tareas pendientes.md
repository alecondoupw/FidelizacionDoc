---
title: "Tareas pendientes — Zontes"
tags: [zontes, tareas]
status: activo
updated: 2026-10-03
---

# Tareas pendientes

## F0 — verificada localmente el 2026-10-03

- [x] Rutas FE/BE y organización Git confirmadas por Usuario el 2026-10-03 (DEC-01): ver [[05-Desarrollo/Entorno local]].
- [x] FE y BE instalados y verificados por separado (npm ci, check, smoke, FE→BE): ver [[05-Desarrollo/Testing]] F0-T01…T11.
- [ ] Resolver recursos Firebase de DEC-02 antes de conectar servicios. DEC-11/12 se resuelven antes de identidad visual final y de abrir los lotes funcionales que dependan de prioridad/hitos.
- [ ] Revisar con Usuario la [[02-Arquitectura/Hoja de decisiones UI y preparación de fases]]; registrar sus respuestas en [[02-Arquitectura/Decisiones tecnicas]] antes de cambiar alcance o implementar.
- [ ] Acordar calendario, hitos y prioridad cliente/admin para los entregables que ya fija SRC-01 p. 2: arquitectura, prototipo usuarios+puntos, código compartido y manuales; no inventar fechas.
- [x] Contrato inicial FE↔BE v0 definido: [[02-Arquitectura/Contrato API v0 - F0]]. Responsables por repo: pendientes de Usuario.
- [x] Inventariar SRC-03/04/05 y asignar C01–C10/A01–A13 a UI-ID y lotes FE en [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]]. Sólo está completo el inventario de este lote, no el diseño ni la implementación.
- [ ] Resolver DEC-16 para A02/importación CSV antes de incluir UI-23 como implementación.
- [ ] Diseñar variantes admin tablet/móvil: SRC-05 sólo aporta escritorio; verificar cada UI-ID en tres tamaños.
- [x] Lotes ejecutables F1–F7 creados: [[05-Desarrollo/Lotes F1-F7 - indice]].

## F8 — correcciones de SRC-06, implementadas en local (2026-10-04)

- [x] DEC-17/18/19 resueltas por Usuario y contratos escritos (§13).
- [ ] Recorridos F8-I-01…I-03 con sesión de administrador y un archivo sintético (requiere autorización para escribir en el proyecto de desarrollo).
- [ ] Revisión visual de Importar clientes, Clientes y Registrar puntos en tres tamaños.
- [x] Commit y push de F8 (BE `4e886e8`, FE `647012c`, Doc `a269749`).
- [ ] Ejecutar cadena A: F8-BE-01→02, F8-FE-01/02, F8-I-01; importar sin crear acceso ni duplicar vínculos.
- [ ] Ejecutar cadena B: F8-BE-03→04, F8-FE-03, F8-I-02; suma manual con vencimiento propio, auto caducidad y sin resta manual.
- [ ] Ejecutar cadena C: F8-FE-04→F8-I-03; retirar Tendencias/Vencimiento del menú y renombrar sólo Publicaciones por marca.
- [ ] Ejecutar cadena D: F8-FE-05→F8-I-04; Inicio cliente según SRC-06 p. 4 con datos reales y móvil completo.
- [ ] Registrar pruebas T-IMPORT/T-GRANT-DATE/T-NAV/T-HOME y regresión en [[05-Desarrollo/Testing]]; no dar F8 por verificada antes.

Índice y 14 tareas individuales: [[05-Desarrollo/Lotes F8 - correcciones SRC-06]].

## Próximos gates de negocio

- [ ] F1: resolver DEC-03/04 antes de bootstrap y legacy.
- [ ] F2: resolver DEC-05/06/14 antes de grants/caducidad/corrección.
- [ ] F3: resolver DEC-07 antes de canje real.
- [ ] F4: resolver DEC-08 antes de borrado o edición sensible.
- [ ] F5: resolver DEC-09 antes de fijar semántica de dashboard/export.
- [x] F6: DEC-10 resuelta y contenido implementado (2026-10-03).
- [ ] F6: Usuario revisa las diferencias con los mockups de [[06-Estado/Evidencias/F6-revision-visual]] y entrega logos, fuentes y fotos autorizados (DEC-11); no publicar fotos/logos de mockup sin permiso.
- [ ] F7: medir y reducir la espera de `GET /me` (~1,7 s por pantalla protegida).
- [x] F7: DEC-13 resuelta e implementada en local (2026-10-03).
- [ ] F7: Usuario crea las cuentas de Render y Vercel y sigue [[08-Produccion/Manual de despliegue y operacion]] §4; luego el agente verifica el despliegue (F7-T10) y repite la medición de rendimiento.
- [ ] F7: ejecutar [[07-Manuales/Guion de demostracion]] completo (T-DEMO).
- [ ] F7: confirmar ADR-16 y publicar `firestore.rules` comprobando el acceso con un usuario autenticado.
- [ ] DEC-12: hitos y fecha de entrega.
- [ ] Definir la retención de respaldos (propuesta: 8 semanales y 6 mensuales).

- [x] Commit y push de F0 autorizados por Usuario el 2026-10-03: rama `f0/base-tecnica` en los tres repos (FE `f29da45`, BE `747e191`).
- [x] `f0/base-tecnica` fusionada en `main` en los tres repos por avance rápido (decisión de Usuario, 2026-10-03).
- [x] Rama `f0/base-tecnica` borrada en local y remoto de los tres repos (decisión de Usuario, 2026-10-03).
- [ ] Decidir si se configura CI (no incluida en F0).

La casilla de inventario visual refleja sólo documentación ya verificada; F0 está verificada y publicada en `f0/base-tecnica`. Al iniciar una tarea, anotar aceptación, evidencia y fuente mínima; al terminar, actualizar [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].
