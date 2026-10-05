---
title: "Lotes F8 — correcciones de administrador y cliente (SRC-06)"
tags: [zontes, lotes, f8]
status: parcialmente_verificado
updated: 2026-10-05
---

# Lotes F8 — correcciones de administrador y cliente (SRC-06)

**Fuente:** [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf|SRC-06]] pp. 1–5; REQ-25–28. **Propósito:** ajustar el producto ya documentado en F1–F7. Los estados de esas fases describen la versión anterior y no verifican F8. Los lotes se planificaron originalmente antes de implementar F8. Según [[05-Desarrollo/Progreso]] y [[05-Desarrollo/Testing]], al 2026-10-04 hay código FE/BE y pruebas F8 registradas, con recorridos integrados F8-I-01…I-03 y revisión visual admin pendientes. FE_REPO y BE_REPO siguen separados; rutas en [[05-Desarrollo/Entorno local]]. La nueva petición SRC-07 se planifica aparte en [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]]; no reescribe las pruebas F8.

## Cadena A — importación y vínculo de clientes

| Orden | Tarea y frente | Resultado verificable | Depende de |
| --- | --- | --- | --- |
| 1 | [[05-Desarrollo/Lotes/F8-D-01 - Conciliar decisiones y contratos SRC-06\|F8-D-01]] · Core | DEC-17/18/19 resueltas; contratos y transición aprobados | SRC-06, DEC vigentes |
| 2 | [[05-Desarrollo/Lotes/F8-BE-01 - Validar archivos y previsualizar importacion\|F8-BE-01]] · BE | CSV/XLSX por una marca; errores y duplicados por fila; preview sin escritura | F8-D-01/DEC-17 |
| 3 | [[05-Desarrollo/Lotes/F8-BE-02 - Confirmar importacion y vincular por correo\|F8-BE-02]] · BE | commit idempotente, cuenta única, marcas acumulativas, reporte auditable | F8-BE-01, F1-BE-03, F4-BE-02 |
| 4a | [[05-Desarrollo/Lotes/F8-FE-01 - Flujo de importacion administrador\|F8-FE-01]] · FE | UI-23/A02: carga, preview, confirmación, resumen y reporte | F8-BE-01/02 |
| 4b | [[05-Desarrollo/Lotes/F8-FE-02 - Clientes y marcas asociadas administrador\|F8-FE-02]] · FE | UI-07/A01: búsqueda por correo, filtro marca, detalle y estado; sin alta manual | F8-BE-02 |
| 5 | [[05-Desarrollo/Lotes/F8-I-01 - Recorrido de importacion y vinculo\|F8-I-01]] · integración | Archivo → vista previa → commit → registro/verificación → marcas visibles; reimportación segura | F8-FE-01/02, F8-BE-02 |

## Cadena B — puntos y vencimiento por asignación

| Orden | Tarea y frente | Resultado verificable | Depende de |
| --- | --- | --- | --- |
| 2 | [[05-Desarrollo/Lotes/F8-BE-03 - Registrar suma manual con fecha propia\|F8-BE-03]] · BE | Sólo suma positiva, fecha obligatoria y única por lote, auditoría e idempotencia | F8-D-01/DEC-18, F2-BE-02 |
| 3 | [[05-Desarrollo/Lotes/F8-BE-04 - Vencer remanente automaticamente\|F8-BE-04]] · BE | Vencimiento al fin del día Bolivia, remanente e historial sin doble descuento | F8-BE-03, F2-BE-03, F3-BE-02 |
| 4 | [[05-Desarrollo/Lotes/F8-FE-03 - Formulario unico Registrar puntos\|F8-FE-03]] · FE | UI-24: búsqueda, marca vinculada, suma, motivo, fecha y confirmación; sin bloque evento/resta | F8-BE-03/04 |
| 5 | [[05-Desarrollo/Lotes/F8-I-02 - Conciliar suma canje y vencimiento\|F8-I-02]] · integración | FE↔BE, reintento, canje y caducidad reflejados en UI-03/13/14/20 | F8-FE-03, F8-BE-04 |

## Cadena C — navegación y nombres del administrador

| Orden | Tarea y frente | Resultado verificable | Depende de |
| --- | --- | --- | --- |
| 2 | [[05-Desarrollo/Lotes/F8-FE-04 - Limpiar menu y renombrar publicaciones\|F8-FE-04]] · FE | Retirar UI-10/19 del menú y rutas visibles; UI-12 muestra «Publicaciones por marca» sin alterar acciones | F8-D-01/DEC-18/19 |
| 3 | [[05-Desarrollo/Lotes/F8-I-03 - Regresion de navegacion administrador\|F8-I-03]] · integración | Navegación escritorio/tablet/móvil y enlaces sin destinos eliminados | F8-FE-03/04 |

## Cadena D — Inicio cliente con referencia nueva

| Orden | Tarea y frente | Resultado verificable | Depende de |
| --- | --- | --- | --- |
| 2 | [[05-Desarrollo/Lotes/F8-FE-05 - Inicio cliente segun nueva referencia\|F8-FE-05]] · FE | UI-13 con jerarquía de SRC-06 p. 4, datos del cliente y estados reales | F8-D-01/DEC-19; APIs existentes F1–F6 |
| 3 | [[05-Desarrollo/Lotes/F8-I-04 - Datos y responsive de Inicio cliente\|F8-I-04]] · integración | 1–3 marcas, saldo separado, vencimiento real, accesos y móvil sin pérdida | F8-FE-05; F8-I-01/02 para datos nuevos |

**Puertas independientes:** F8-D-01 documenta las tres decisiones; cada cadena puede comenzar cuando la decisión que la gobierna esté resuelta, sin esperar las otras. Ver evaluación de orquestación en [[02-Arquitectura/Impacto SRC-06 y decisiones F8]].

**Camino crítico:** F8-D-01 → (F8-BE-01→02→FE-01/02→I-01) y (F8-BE-03→04→FE-03→I-02) → F8-FE-05 → F8-I-04. F8-FE-04→I-03 puede avanzar cuando DEC-18/19 queden resueltas. Contratos FE↔BE (roles, request/response, errores e idempotencia) se versionan antes de implementar cada par. Si una API existente no entrega datos para Inicio, registrar el hueco y añadir un lote BE acotado antes de F8-FE-05; no calcular saldo ni vínculos en el navegador.

**Puerta de aceptación F8:** decisiones registradas, pruebas T-IMPORT/T-GRANT-DATE/T-EXP/T-NAV/T-HOME y regresión de F1–F7 ejecutadas contra revisiones FE/BE identificadas, con evidencia en [[05-Desarrollo/Testing]]. Revisar y actualizar manual, mapa UI y estado; no llamar «verificado» a capturas ni a pruebas no ejecutadas.
