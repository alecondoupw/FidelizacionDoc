---
title: "Método de trabajo multiagente — Zontes"
tags: [zontes, metodologia]
status: propuesto
updated: 2026-10-02
---

# Método de trabajo multiagente — Zontes

Este Core es la memoria canónica del proyecto; FE/BE son artefactos operativos. Cualquier agente (Codex, Claude, Gemini, Kimi u otro) entra por [[00-Inicio]], lee [[01-Contexto/Contexto activo]], el lote de [[05-Desarrollo/Plan por fases]] y sólo módulos, reglas y fuentes pertinentes. El nombre del agente no altera permisos ni criterios de calidad.

## Ciclo por tarea

1. **Enfocar:** describir necesidad, usuario, fase, UI-ID/RN-ID y criterio observable. Consultar [[02-Arquitectura/Decisiones pendientes]]; si falta decisión material, presentar opciones e impacto a Paulo antes de implementar.
2. **Diseñar mínimo:** contrato FE↔BE, datos/roles, cambios de interfaz, pruebas y riesgos. El anexo de stack es [[02-Arquitectura/Base tecnica documentada]], no instalación ni evidencia de servicios disponibles.
3. **Delegar con frontera:** FE, BE y QA en paralelo sólo si archivos y contratos no compiten. El coordinador integra; ningún subagente decide arquitectura o permisos por sí mismo.
4. **Construir y probar:** cambios pequeños, revisión de fuentes, escenarios negativos, compatibilidad. Separar prototipo de producto verificado.
5. **Aprender:** guardar en Core decisión, evidencia, error generalizable y próximo gate. No copiar prompts, secretos, toda una conversación ni conocimiento técnico de otro proyecto por analogía indiscriminada.

## Contexto y tokens

Primero índice y pregunta concreta; después nota puntual; fuente PDF sólo en páginas necesarias. Entregar a otro agente un paquete pequeño: objetivo, aceptación, rutas, contrato, decisiones y evidencia. Observaciones de rendimiento pueden registrar consumo si está disponible, pero la optimización se juzga por resultados verificados/retrabajo. No sacrificar pruebas para ahorrar tokens. La experiencia de otro Core puede sugerir una hipótesis; validar su ajuste a Zontes antes de adoptarla, manteniendo el conocimiento de dominio aquí. Ver [[05-Desarrollo/Skills y herramientas]].

## Autoridad y cambios

Paulo decide alcance, stack final, proveedores, rutas, uso de datos reales, instalaciones, credenciales y despliegue. Un agente puede proponer, documentar y ejecutar sólo lo pedido y autorizado. Las skills son optativas y pasan por revisión de seguridad y utilidad. Cuando llegue nueva información, conservar procedencia en [[09-Entradas/_Indice de entradas]], actualizar decisión y plan afectados; evitar sobreajustar la metodología a un incidente puntual. Ver [[10-Metodologia/Procedencia de semilla]].
