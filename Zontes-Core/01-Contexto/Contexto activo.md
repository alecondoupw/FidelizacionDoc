---
title: "Contexto activo y lectura mínima"
tags: [zontes]
status: activo
updated: 2026-10-03
---

# Contexto activo y lectura mínima

**Proyecto:** Zontes; **Core:** `Zontes-Core`; **estado:** semilla documental creada 2026-10-02. **Fuente estructural:** `CORES/nextjs+nestjs/Plantilla-Core-Proyecto`, usada como formato; el anexo técnico del proyecto usa Express, no NestJS. **Cerebro de dominio:** sin asociación verificada en catálogo, no inferir `BRAIN:nextjs-nestjs` por copiar la estructura.

**Raíz real (host Windows de Paulo):** `C:\Users\aleco\Documents\Fidelizacion`, con tres repos Git independientes: `FidelizacionDoc` (este Core), `FidelizacionFronted` (FE_REPO, Next.js) y `FidelizacionBackend` (BE_REPO, Express). La raíz `E:/Repositorios/Hackathon/Zontes` de la semilla no aplica a este host. **F0 verificada localmente el 2026-10-03** (instalación limpia, lint, typecheck, test, build, smoke y FE→BE); con autorización de Paulo, el código F0 está publicado en la rama `f0/base-tecnica` de FE (`f29da45`) y BE (`747e191`), pendiente de fusionar en `main`. Ver [[05-Desarrollo/Entorno local]], [[05-Desarrollo/Testing]] y [[02-Arquitectura/Contrato API v0 - F0]]. **Siguiente:** lotes en [[05-Desarrollo/Lotes F1-F7 - indice]]; F1 espera DEC-02/03/04. No iniciar funciones de un lote sin la orden de Paulo y sus decisiones.

Para una tarea FE: contrato raíz → requisito/módulo → [[03-Modulos/Mapa de vistas frontend]] → [[02-Arquitectura/Guia visual y criterios anti slop]] → contrato API afectado. Para BE: contrato → [[04-Reglas-de-negocio/_Indice de reglas]] → [[02-Arquitectura/Modelo de datos y contratos]] → pruebas. Para fases: [[05-Desarrollo/Plan por fases]] → P-ID → decisión abierta → evidencia.

SRC-01 enunciado (2 páginas), SRC-02 administrador (15 páginas), SRC-03 cliente (13 páginas) y los ZIP SRC-04/05 viven en [[09-Entradas/_Indice de entradas]]. [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] resume lo definido por página; consultar el pasaje original y el mockup asignado por [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]] al trabajar una tarea. Hay diez referencias cliente escritorio/móvil y trece admin sólo escritorio; UI-23/importación CSV es propuesta visual pendiente de DEC-16. No rellenar huecos con patrones genéricos por intuición.

Existen FE y BE técnicos con `GET /api/v1/health` y prueba runtime local de F0; no hay conexión a Firebase, base de clientes, CI, despliegue ni funciones de producto. Al relevar: P-ID, objetivo, fuentes/decisiones, superficies tocadas, resultado de prueba, bloqueos y siguiente acción en [[06-Estado/Bitacora]].
