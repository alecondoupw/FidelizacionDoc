# FidelizacionDoc — Zontes / Kiden / NIU

Documentación y referencias del proyecto de fidelización multimarca. El baúl de Obsidian es [`Zontes-Core/`](Zontes-Core/00-Inicio.md); empieza por [`00-Inicio.md`](Zontes-Core/00-Inicio.md) y [`Contexto activo.md`](Zontes-Core/01-Contexto/Contexto%20activo.md).

## Decisiones

- [Hoja de decisiones UI y preparación de fases](Zontes-Core/02-Arquitectura/Hoja%20de%20decisiones%20UI%20y%20preparación%20de%20fases.md): preguntas concretas para Usuario y estado de las fases.
- [Decisiones pendientes](Zontes-Core/02-Arquitectura/Decisiones%20pendientes.md): índice DEC-01–DEC-16.
- [Decisiones técnicas y procedencia](Zontes-Core/02-Arquitectura/Decisiones%20tecnicas.md): base documentada y decisiones registradas.

## Avance

La [fase F0](Zontes-Core/05-Desarrollo/Lote%20F0%20-%20instalacion%20separada%20frontend%20y%20backend.md) está **verificada (2026-10-03)** y fusionada en `main` de cada repo: frontend Next.js en [FidelizacionFronted](https://github.com/alecondoupw/FidelizacionFronted) y backend Express en [FidelizacionBackend](https://github.com/alecondoupw/FidelizacionBackend), dos repositorios independientes, con instalación limpia, lint, build, pruebas y llamada FE→BE comprobadas ([evidencia](Zontes-Core/05-Desarrollo/Testing.md)). Los lotes F1–F7 están en el [índice de lotes](Zontes-Core/05-Desarrollo/Lotes%20F1-F7%20-%20indice.md); ninguno se ha iniciado.

El Core conserva requisitos, PDF y mockups aportados, asignación de vistas, contratos, pruebas y evidencia. No contiene código de producto ni credenciales; el código vive en los dos repositorios operativos. Consulta [`AGENTS.md`](AGENTS.md) antes de trabajar en el proyecto.
