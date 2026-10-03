---
title: "Modelo de datos y contratos propuestos"
tags: [zontes]
status: planificado
updated: 2026-10-02
---

# Modelo de datos y contratos propuestos

Modelo conceptual para discutir F0, **no esquema Firestore implementado**:

| Colección/entidad candidata | Identidad y función | Invariante |
| --- | --- | --- |
| `customers` + `legacy_links` | perfil cliente y referencia a base previa por correo normalizado | correo único local; estado vinculado/no vinculado |
| `admins` | perfil administrativo separado | precreado o creado por admin; último activo protegido |
| `brands` | Zontes/Kiden/NIU | contenido, reglas y beneficios aislados |
| `point_rules` | evento+marca+puntos+activo+versión | sin campo condición; una activa por combinación |
| `source_events` | evento externo validado y su ID | idempotencia por origen+ID |
| `point_movements` / `point_lots` | otorgar, usar, vencer, corregir | append-only conceptual; saldo reconciliable |
| `benefits` / `redemptions` | catálogo, disponibilidad, canje y cupón | operación atómica saldo+stock+canje |
| `brand_content` | contenido visible de una marca | no filtrar sólo en UI |
| `audit_events` | cambios de administradores/reglas/configuración | actor, marca, momento, antes/después permitido |

**Contratos iniciales por definir:** sesión verificada; consulta de perfil, saldo/historial/beneficios; alta de evento confiable; configuración de reglas; solicitud de canje; reportes/exportes. La matriz de productores, consumidores, garantías, decisiones y pruebas está en [[02-Arquitectura/Contratos de integracion por flujo]]. Ninguna ruta literal constituye todavía una API pública acordada.

Para cada contrato en F0/F1 documentar: método, actor, recurso de marca, esquema de entrada/salida, autorización, errores, paginación, idempotencia y revisión. Zod puede compartir esquemas entre repos si resuelve versionado sin acoplamiento circular. Una respuesta FE no debe contener datos de otra marca o cliente.

**Transacciones críticas:** otorgamiento, canje, vencimiento y corrección deben conservar movimientos, saldo y disponibilidad de forma atómica/reintentable. No asumir que un único documento Firestore basta; probar concurrencia con casos de doble evento y doble canje. Falta conocer API/esquema de clientes preexistentes: DEC-04.
