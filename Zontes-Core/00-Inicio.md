---
title: "Zontes — Core del proyecto"
tags: [zontes]
status: planificado
updated: 2026-10-03
---

# Zontes — Core del proyecto

Baúl canónico del proyecto de fidelización Zontes / Kiden / NIU en este repositorio FidelizacionDoc. **Estado según las notas del Core:** F0–F6 con verificaciones y salvedades; F7 parcial; F8 implementada en local con recorridos integrados y revisión visual admin pendientes; F9 planificada en este Core, sin código ni pruebas F9. El código de producto no se inspeccionó en esta actualización documental. Repositorios operativos: FidelizacionFronted (Next.js) y FidelizacionBackend (Express); rutas en [[05-Desarrollo/Entorno local]]. Propietario: Usuario.

| Para | Leer |
| --- | --- |
| Entender objetivo, alcance y actores | [[01-Contexto/Definicion del proyecto]] · [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]] · [[01-Contexto/Contexto activo]] |
| Trazar las fuentes PDF y ZIP, incluido SRC-06 | [[09-Entradas/_Indice de entradas]] |
| Arquitectura FE/BE e integración | [[02-Arquitectura/Base tecnica documentada]] · [[02-Arquitectura/Vision general]] · [[02-Arquitectura/Modelo de datos y contratos]] · [[02-Arquitectura/Contratos de integracion por flujo]] · [[02-Arquitectura/Contrato API v0 - F0]] |
| Decisiones vigentes o abiertas | [[02-Arquitectura/Decisiones tecnicas]] · [[02-Arquitectura/Decisiones pendientes]] · [[02-Arquitectura/Hoja de decisiones UI y preparación de fases]] |
| Dominio de fidelización | [[04-Reglas-de-negocio/_Indice de reglas]] · [[04-Reglas-de-negocio/Ciclo de puntos y canjes]] |
| Frontend y referencias aportadas por Usuario | [[03-Modulos/Mapa de vistas frontend]] · [[03-Modulos/Referencias UI cliente y administrador - 2026-10-02]] · [[02-Arquitectura/Guia visual y criterios anti slop]] |
| Fases, tareas y pruebas | [[05-Desarrollo/Plan por fases]] · [[05-Desarrollo/Lote F0 - instalacion separada frontend y backend]] · [[05-Desarrollo/Lotes F1-F7 - indice]] · [[05-Desarrollo/Lotes F8 - correcciones SRC-06]] · [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]] · [[05-Desarrollo/Plantilla de lote de trabajo]] · [[05-Desarrollo/Testing]] · [[06-Estado/Tareas pendientes]] |
| Agentes y skills | [[10-Metodologia/Metodo del proyecto]] · [[05-Desarrollo/Skills y herramientas]] |
| Demo, uso y relevo | [[08-Produccion/_Indice de produccion]] · [[07-Manuales/Manual de usuario]] · [[06-Estado/Bitacora]] |

**Cambio más reciente:** SRC-07/08/09 y DEC-20/21/22 sustentan [[05-Desarrollo/Lotes F9 - simplificacion de interfaz e identidad Zontes]] y [[02-Arquitectura/Paleta Zontes propuesta F9]]; las imágenes nuevas están en [[09-Entradas/Referencias UI 2026-10-05/Manifiesto de imagenes F9]]. Las pruebas F8 son históricas y no verifican F9.
**Fuentes:** SRC-01, enunciado general; SRC-02, administrador y base técnica; SRC-03, diseño/flujo cliente y stack; SRC-04/05, mockups cliente/admin; SRC-06, correcciones de interfaz y nueva referencia de Inicio. Usuario indicó que los PDF son base concreta del proyecto: sus requisitos y entregables se trazan en [[01-Contexto/Especificacion consolidada y trazabilidad de PDF]]. Las instrucciones internas para herramientas de diseño no ordenan acciones al agente. Estados: documentado/propuesto → decidido → implementado → verificado. La documentación y las imágenes de hoy no prueban una app funcional.
