---
title: "Definición del proyecto"
tags: [zontes]
status: planificado
updated: 2026-10-02
---

# Definición del proyecto

## Objetivo general

Diseñar, implementar y desplegar una plataforma web responsiva de fidelización multimarca para **Zontes, Kiden y NIU** que centralice usuarios, acumulación/vencimiento de puntos, catálogo de beneficios y canjes, con reglas por marca, seguridad y posibilidad de ampliación. **El despliegue es parte del objetivo de SRC-01 p. 1**; su entorno, cuentas, acceso y ejecución concreta requieren DEC-13 y autorización. El reto se dirige a Bolivia y contempla escalabilidad internacional.

## Objetivos específicos

1. Registrar/autenticar clientes y administradores separados; vincular nuevos clientes a la base existente **sólo por correo normalizado** cuando haya coincidencia.
2. Configurar puntos por evento y marca —compra, referido, mantenimiento, asistencia— sin condición adicional, y mantener movimientos auditables y saldo correcto.
3. Permitir catálogo y canjes independientes por marca con control de disponibilidad, saldo, comprobante/cupón y trazabilidad.
4. Ofrecer panel administrativo con gestión de cuentas/reglas, actividad, canjes, tendencias, exportaciones y contenido por marca.
5. Proveer UI de cliente y administrador con identidad de marca, accesibilidad y diseño responsivo verificable en escritorio/tablet/móvil.
6. Entregar arquitectura/diseño técnico, prototipo funcional con núcleo usuarios/puntos, código fuente en repositorio compartido y manual de despliegue/uso administrativo; definir cronograma e hitos en reunión de arranque y hacer revisiones periódicas (SRC-01 p. 2).

## Actores y alcance

| Actor | Necesidad | Alcance documentado |
| --- | --- | --- |
| Cliente | Cuenta, marcas, puntos, historial, beneficios/canje | SRC-01 esencial; SRC-03 detalla flujo y diseño; SRC-04 aporta diez mockups; contratos y decisiones aún abiertos |
| Administrador | Crear otros administradores, gestionar clientes y reglas, reportar/exportar, contenido | SRC-02 pp.1–10 detallado; SRC-05 aporta trece mockups escritorio, incluyendo una importación propuesta no aprobada |
| Empresa/sistema existente | Reconocer clientes previos y separar marcas | Fuente externa aún no inspeccionada; contrato pendiente |
| Integrador del proyecto | Coordinar frentes frontend/backend y evidencias en el repositorio compartido que se acuerde | Organización y rutas aún no presentes |

**Dentro:** web responsiva, panel admin y experiencia cliente conforme al reto, con despliegue como entregable final. SRC-02 pp. 11–15 incorpora Next.js/TypeScript, Express/TypeScript y Firebase como [[02-Arquitectura/Base tecnica documentada]]; DEC-02 precisa recursos/entornos reales, no reabre la lectura del PDF. **Fuera hasta nueva decisión:** app móvil nativa, motor de condiciones adicional en reglas de puntos, promoción cliente→admin, registro público de admins, uso de NestJS por herencia de plantilla e integraciones reales de facturación/CRM sin acceso autorizado. El despliegue no se ejecuta durante esta semilla documental.

**Criterio de éxito inicial:** un cliente vinculado y otro no vinculado; evento válido otorga puntos según marca; historial/saldo concilian; admin autorizado gestiona regla futura; canje respeta saldo/disponibilidad; UI muestra estados reales; API rechaza acceso cruzado; ambos repos pueden demostrar el recorrido. Alcance exacto de demo, tiempos y cuentas pendientes en [[02-Arquitectura/Decisiones pendientes]].

Estado real al inicio: carpeta Zontes vacía. No hay código, proyectos Firebase, credenciales, datos de la empresa ni pruebas ejecutadas.
