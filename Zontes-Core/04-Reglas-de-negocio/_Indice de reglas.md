---
title: "Reglas de negocio consolidadas"
tags: [zontes]
status: planificado
updated: 2026-10-02
---

# Reglas de negocio consolidadas

| ID | Regla decidida/documentada | Fuente y prueba prevista |
| --- | --- | --- |
| RN-01 | Admin inicial precreado; sólo admin crea otro; sin registro público ni conversión cliente→admin | SRC-02 pp.1–3; T-ROLE |
| RN-02 | Impedir eliminación del último admin activo y auditar cambios admin | SRC-02 p.3; T-ROLE |
| RN-03 | Vincular clientes existentes sólo por correo normalizado; un correo por cuenta; sin coincidencia = no vinculado | SRC-02 p.2; T-LINK |
| RN-04 | Regla de puntos = evento+marca+puntos+estado; sin campo “condición”; única combinación | SRC-02 pp.4,9; T-RULE |
| RN-05 | Cambios de regla/vigencia afectan eventos/puntos futuros; histórico no se reescribe | SRC-02 pp.4–5; T-HISTORY |
| RN-06 | Compra, referido, mantenimiento, asistencia: evento válido otorga puntos configurados de su marca | SRC-01 p.1, SRC-02 p.4; T-POINTS |
| RN-07 | Vencimiento configurable por marca, desde otorgamiento por defecto; deja movimiento de historial | SRC-02 p.5; T-EXP |
| RN-08 | Canje valida saldo/beneficio/disponibilidad y deja traza/comprobante | SRC-01 p.1; T-REDEEM |
| RN-09 | Datos, contenido y beneficios se separan por marca; FE y API respetan permiso | SRC-01/02; T-BRAND |
| RN-10 | Admin SDK requiere autorización backend propia porque omite reglas Firestore | SRC-02 pp.11,14; T-AUTHZ |
| RN-11 | Exportaciones sólo de datos filtrados/autorizados, sin exponer sensibles ajenos | SRC-02 p.7; T-EXPORT |

Las reglas RN-01,03–07 son decisiones explícitas del documento consolidado, no preguntas para volver a plantear. Los vacíos de origen de evento, API legacy, canje y vencimiento parcial se registran en [[02-Arquitectura/Decisiones pendientes]]. Modelar estados/ledger en [[04-Reglas-de-negocio/Ciclo de puntos y canjes]]. Plantilla para nuevas reglas: [[04-Reglas-de-negocio/_Plantilla de regla]].
