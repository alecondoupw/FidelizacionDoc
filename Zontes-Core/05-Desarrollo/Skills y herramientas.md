---
title: "Skills y herramientas — evaluación, no instalación"
tags: [zontes, skills]
status: propuesto
updated: 2026-10-02
---

# Skills y herramientas — evaluación, no instalación

Las siguientes son **capacidades a considerar**, no dependencias instaladas. Antes de habilitar una skill, MCP, CLI, extensión o servicio, pedir permiso explícito a Paulo: origen y mantenedor, código/permisos/red, datos que verá, coste, riesgo, alternativa sin instalación y forma de reversión. Recomendarla o citarla no la activa. Impeccable puede evaluarse para UI si Paulo lo pide, pero **nunca instalarse sin preguntar primero**.

| Momento | Capacidad útil | Resultado esperado sin acoplarse a proveedor |
| --- | --- | --- |
| F0 | lectura de PDF/contexto y planificación por tareas | fuentes trazadas, decisiones y plan FE/BE |
| F0–F7 | diseño de API/contratos y revisión de seguridad | permisos del backend, esquemas, versiones y pruebas de contrato |
| F1–F3 | pruebas automatizadas + emulador Firebase si se aprueba | identidad, transacciones e idempotencia verificadas sin datos reales |
| F1–F6 | diseño frontend/accesibilidad y navegador de pruebas | UI-ID alineados con referencias aprobadas, estados completos, menos UI genérica |
| F5–F7 | exportación/reportes, carga focalizada y revisión de operación | conciliación, límites, logs, backup/restauración y manual |

## Economía de contexto para Codex, Claude y otros agentes

Un agente recibe sólo objetivo del lote, criterios, archivos involucrados, decisiones y contratos pertinentes; usa este índice para pedir el resto por necesidad. Hacer búsquedas dirigidas y resúmenes con referencias en vez de leer todo el baúl. Separar trabajo FE, BE y QA cuando puedan avanzar sin conflicto; no gastar tokens de varios agentes para duplicar la misma exploración. Medir utilidad como **criterios verificados por tiempo/tokens**, no como respuesta más corta. Las observaciones de consumo pueden registrar modelo/agente, fase, tokens o coste si la plataforma los ofrece, resultado y retrabajo; no inventar métricas ni prometer ahorro universal. Nunca ejecutar algo sólo para ahorrar tokens si aumenta riesgo, permisos o pérdida de evidencia.

Consultar [[10-Metodologia/Metodo del proyecto]] para contrato de agentes. SRC-02 pp. 11–13 incorpora Postman, ESLint/Prettier, Tailwind, shadcn/ui, Recharts, TanStack, Zod y otras librerías en la [[02-Arquitectura/Base tecnica documentada]]; **no están instaladas en repositorios operativos**. Las skills/MCP del agente son herramientas de trabajo distintas de las dependencias del producto.
