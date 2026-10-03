---
title: "Contexto activo y lectura mínima"
tags: [zontes]
status: planificado
updated: 2026-10-02
---

# Contexto activo y lectura mínima

**Proyecto:** Zontes; **Core:** `Zontes-Core`; **estado:** semilla documental creada 2026-10-02. **Fuente estructural:** `CORES/nextjs+nestjs/Plantilla-Core-Proyecto`, usada como formato; el anexo técnico del proyecto usa Express, no NestJS. **Cerebro de dominio:** sin asociación verificada en catálogo, no inferir `BRAIN:nextjs-nestjs` por copiar la estructura.

**Raíz objetivo:** `E:/Repositorios/Hackathon/Zontes`. Al preparar la semilla estaba vacía; `FE_REPO` y `BE_REPO` son dos frentes separados aún sin ubicación. Paulo pidió planificar F0 para instalarlos y verificarlos, pero **no iniciar F0 todavía**; preguntar ambas rutas y la organización Git sólo cuando dé inicio a esa fase. Ver [[05-Desarrollo/Lote F0 - instalacion separada frontend y backend]]. No crear proyectos ni instalar paquetes a partir de esta nota.

Para una tarea FE: contrato raíz → requisito/módulo → [[03-Modulos/Mapa de vistas frontend]] → [[02-Arquitectura/Guia visual y criterios anti slop]] → contrato API afectado. Para BE: contrato → [[04-Reglas-de-negocio/_Indice de reglas]] → [[02-Arquitectura/Modelo de datos y contratos]] → pruebas. Para fases: [[05-Desarrollo/Plan por fases]] → P-ID → decisión abierta → evidencia.

SRC-01 enunciado (2 páginas), SRC-02 administrador (15 páginas), SRC-03 cliente (13 páginas) y los ZIP SRC-04/05 viven en [[09-Entradas/_Indice de entradas]]. [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] resume lo definido por página; consultar el pasaje original y el mockup asignado por [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]] al trabajar una tarea. Hay diez referencias cliente escritorio/móvil y trece admin sólo escritorio; UI-23/importación CSV es propuesta visual pendiente de DEC-16. No rellenar huecos con patrones genéricos por intuición.

No hay conexión a Firebase, base de clientes, API, repositorios, CI, app ni prueba runtime. Al relevar: P-ID, objetivo, fuentes/decisiones, superficies tocadas, resultado de prueba, bloqueos y siguiente acción en [[06-Estado/Bitacora]].
