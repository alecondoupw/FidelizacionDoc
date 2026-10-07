---
title: "Cambios backend - comprobantes Zontes y demo"
tags: [zontes, backend, cambios]
status: implementado-verificado-local
updated: 2026-10-07
---

# Cambios del backend

## Código

src/canjes/comprobante.ts utiliza Zontes como autor del PDF y “Zontes · FIDELIZACIÓN” en su encabezado visible. El QR, código, puntos, marcas, estado y vencimiento conservan sus contratos.

El README enlaza esta documentación y la guía de despliegue. La PWA se implementa en frontend y utiliza la API Express existente; no se modifican permisos ni reglas de puntos, saldos y stock.

## Datos de demo

Las cuentas y datos ficticios creados por encargo de Paulo existen en Firebase Authentication/Firestore. No son archivos que se carguen al ejecutar git pull o desplegar.

Se conservaron registros previos y se agregaron ejemplos para usuarios, importación, reglas, beneficios, puntos, canjes, publicaciones, reportes y exportaciones. Se verificaron conciliación, saldos y comprobantes. Detalle en [[07-Manuales/Datos y accesos de demo - 2026-10-07]].

Cuentas genéricas: adminzontes@test.com (administrador) y clientezontes@test.com (cliente). Sus contraseñas se entregan a Paulo fuera de Git. El cliente genérico comienza sin puntos; Sofia ofrece el escenario de varias marcas. El dominio test.com no es un dominio reservado para ejemplos; no se enviaron mensajes durante la creación.

Render debe utilizar el mismo proyecto Firebase y prefijo vacío para acceder a los registros existentes. Un proyecto Firebase diferente requiere preparar sus propios usuarios y datos.

## Operación

El backend ya admite HOST=0.0.0.0, PORT asignado por Render y TRUST_PROXY=1. El build instala TypeScript con npm ci --include=dev && npm run build y arranca con npm start. El JSON de Admin SDK se carga como Secret File del backend.

LEGACY_SOURCE=importacion utiliza los clientes importados. sintetica añade el doble de desarrollo para ejemplo.test. Para esta publicación se utiliza el origen importacion con las colecciones existentes.

## Evidencia

Los PDF de demo se analizaron y muestran el autor y encabezado Zontes. Se aprobaron 20 pruebas HTTP de canjes y configuración, lint focalizado, typecheck y build antes de publicar esta entrega.

El JSON privado, .env, contraseñas, respaldos y script local de carga quedan fuera de Git. No se vuelve a sembrar Firebase durante esta publicación.

Ver [[08-Produccion/Guia rapida - Render Vercel y demo 2026-10-07]] y [[06-Estado/Entrega demo Zontes - 2026-10-07]].
