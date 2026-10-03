---
title: "Plantilla de lote de trabajo"
tags: [zontes, plantilla, desarrollo]
status: plantilla
updated: 2026-10-02
---

# Plantilla de lote de trabajo

Crear una copia en `05-Desarrollo/` **después de verificar F0**, con ID del plan (por ejemplo `F1-FE-01`). Una nota por resultado comprobable; conservar los enlaces internos de Obsidian.

| Campo | Contenido a completar |
| --- | --- |
| ID / fase / frente | FE, BE o integración; relación con [[05-Desarrollo/Plan por fases]] |
| Objetivo observable | Qué podrá hacer cliente/admin o qué contrato quedará operativo |
| Fuente y página | SRC-01/02/03 + REQ-ID de [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] |
| Referencia visual | C/A-ID y UI-ID de [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]], si aplica |
| Reglas y decisiones | RN-ID, DEC-ID, estado de cada decisión; no confundir propuesta con aprobación |
| Responsable y rutas | Dueño, ruta FE y/o BE confirmada en [[05-Desarrollo/Entorno local]] |
| Contrato FE↔BE | Actor, request/response, errores, permisos, marca, fechas, versión e idempotencia según [[02-Arquitectura/Contratos de integracion por flujo]] |
| Dependencias | Lotes previos y datos/servicios autorizados |
| Aceptación | Casos positivos, negativos, responsive y accesibilidad cuando hay UI |
| Prueba y evidencia | T-ID, comandos/resultados, revisión/commit y enlace a [[05-Desarrollo/Testing]] o evidencia en Core |
| Estado | Pendiente, bloqueado por decisión, en curso, verificado; fecha de actualización |

No copiar esta plantilla como tarea vacía que aparente avance. Cada lote se crea con fuente, dueño y aceptación concretos; se cierra según [[05-Desarrollo/Criterio de terminado]].
