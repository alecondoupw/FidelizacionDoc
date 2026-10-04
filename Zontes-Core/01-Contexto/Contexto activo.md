---
title: "Contexto activo y lectura mínima"
tags: [zontes]
status: activo
updated: 2026-10-03
---

# Contexto activo y lectura mínima

**Proyecto:** Zontes; **Core:** `Zontes-Core`; **estado:** semilla documental creada 2026-10-02. **Fuente estructural:** `CORES/nextjs+nestjs/Plantilla-Core-Proyecto`, usada como formato; el anexo técnico del proyecto usa Express, no NestJS. **Cerebro de dominio:** sin asociación verificada en catálogo, no inferir `BRAIN:nextjs-nestjs` por copiar la estructura.

**Raíz de esta copia local (host Windows de Usuario):** `E:/Repositorios/Hackathon/Zontes`, checkout de `FidelizacionDoc` con este Core. Las rutas FE_REPO/BE_REPO descritas en [[05-Desarrollo/Entorno local]] pertenecen a otro host o ubicación documentada y deben confirmarse antes de tocar código; no se inspeccionaron en esta sesión. **Según este Core, F0–F6 tienen pruebas registradas con sus límites y F7 está en curso.** Ver [[05-Desarrollo/Progreso]] y [[05-Desarrollo/Testing]]. El siguiente cambio documental es F8; no iniciar su implementación sin la orden de Usuario y DEC-17/18/19.

**Nueva fuente SRC-06 (2026-10-03):** [[09-Entradas/Requerimientos_Administrador_y_Cliente.pdf]] añade correcciones de importación, vencimiento por asignación, menú admin e Inicio cliente. Cadenas F8 en [[05-Desarrollo/Lotes F8 - correcciones SRC-06]]; conflictos/DEC-17/18/19 en [[02-Arquitectura/Impacto SRC-06 y decisiones F8]]. F8 no se inició ni se probó. Las pruebas F1–F7 del Core pertenecen al alcance anterior.
Para una tarea FE: contrato raíz → requisito/módulo → [[03-Modulos/Mapa de vistas frontend]] → [[02-Arquitectura/Guia visual y criterios anti slop]] → contrato API afectado. Para BE: contrato → [[04-Reglas-de-negocio/_Indice de reglas]] → [[02-Arquitectura/Modelo de datos y contratos]] → pruebas. Para fases: [[05-Desarrollo/Plan por fases]] → P-ID → decisión abierta → evidencia.

SRC-01 enunciado (2 páginas), SRC-02 administrador (15 páginas), SRC-03 cliente (13 páginas) y los ZIP SRC-04/05 viven en [[09-Entradas/_Indice de entradas]]. [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] resume lo definido por página; consultar el pasaje original y el mockup asignado por [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]] al trabajar una tarea. Hay diez referencias cliente escritorio/móvil, trece admin sólo escritorio y una nueva imagen de Inicio en SRC-06 p. 4. UI-23/importación tiene nueva fuente funcional pero requiere DEC-17 para sustituir DEC-16. No rellenar huecos con patrones genéricos por intuición.

Los estados implementados y sus límites se consultan en [[05-Desarrollo/Progreso]]; esta actualización no inspeccionó los repos FE/BE ni servicios. SRC-06/F8 sigue sin código ni pruebas. Al relevar: P-ID, objetivo, fuentes/decisiones, superficies tocadas, resultado de prueba, bloqueos y siguiente acción en [[06-Estado/Bitacora]].
