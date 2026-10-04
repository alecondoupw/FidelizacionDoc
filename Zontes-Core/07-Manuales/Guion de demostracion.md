---
title: "Guion de demostración"
tags: [zontes, manual, demo, f7]
status: preparado
updated: 2026-10-04
---

# Guion de demostración (T-DEMO)

Recorrido de unos 15 minutos que muestra el núcleo pedido en SRC-01 p. 2 (usuarios + puntos) y el resto de módulos, sólo con **datos sintéticos** (dominio `ejemplo.test`, catálogo de `datos/catalogo.ejemplo.json`). Sirve en local y en el despliegue de [[08-Produccion/Manual de despliegue y operacion]]. Lote: [[05-Desarrollo/Lotes/F7-FE-01 - Recorrido demo y optimizacion medida|F7-FE-01]].

## Preparación (una vez por proyecto)

Comandos en `FidelizacionBackend` con el `.env` del proyecto que se va a mostrar:

1. Administrador: `npm run admin:bootstrap -- --email <correo del presentador>` (sólo si aún no hay ninguno) y definir la contraseña con el enlace.
2. Cliente de prueba (su vínculo llega por importación, paso 2 del recorrido; con `LEGACY_SOURCE=sintetica` ya figura en las tres marcas): `npm run dev:usuario-prueba -- --email cliente.multimarca@ejemplo.test` y definir su contraseña con el enlace. (El comando se niega con `NODE_ENV=production`; en el despliegue se ejecuta desde el equipo local apuntando al mismo proyecto.) Después, entrar una vez como cliente para completar el registro.
3. Catálogo: `npm run catalogo:cargar -- --archivo datos/catalogo.ejemplo.json` (no pisa beneficios existentes).
4. Dos ventanas: una normal para el administrador y otra privada para el cliente.

## Recorrido

Sustituir `AAAAMMDD` por la fecha del día.

| # | Rol | Acción | Resultado esperado |
| --- | --- | --- | --- |
| 1 | Admin | Ingresar en `/admin/ingresar` | Dashboard con KPI de 30 días y gráficos |
| 2 | Admin | Clientes → **Importar clientes**: Zontes y un CSV con `nombre;correo` y la fila `Cliente Demo;cliente.multimarca@ejemplo.test` → vista previa → confirmar | La fila sale «Ya vinculado» o «Se vinculará a su cuenta»; resumen y reporte descargable |
| 3 | Admin | Registrar puntos → correo `cliente.multimarca@ejemplo.test` → Buscar → Zontes, 100, «Compra en tienda», vence en un año → Revisar y registrar → Registrar puntos | «Se sumaron 100 puntos a … en Zontes; vencen el …» |
| 4 | Admin (opcional, Postman) | `POST /admin/asignaciones` dos veces con el mismo `idSolicitud` (colección de `FidelizacionBackend/docs/postman`) | La segunda responde 200 con `repetido: true` y no suma otra vez (idempotencia) |
| 5 | Cliente | Ingresar en `/ingresar` | Inicio: saludo, banner, total y saldo por marca, puntos por vencer con su fecha, marcas vinculadas y «¿Cómo ganar puntos?» |
| 6 | Cliente | Historial | El movimiento de +100 en Zontes |
| 7 | Cliente | Catálogo → Zontes → **Revisión de mantenimiento (ejemplo)** (80 pts) → confirmar | Código `ML-…` con QR; el saldo baja 80 |
| 8 | Cliente | Catálogo → **Casco integral (ejemplo)**, talla S | Opción agotada y no seleccionable; NIU «Casco urbano» aparece agotado |
| 9 | Admin | Canjes en mostrador → escribir el código del paso 7 → Marcar entregado | Estado «Entregado» |
| 10 | Cliente | Mis canjes → el canje | Estado «Entregado» |
| 11 | Admin | Publicaciones por marca → Zontes → Nuevo contenido: Promoción, «Demo AAAAMMDD», destacada, activa | Estado «Publicada»; vista previa |
| 12 | Cliente | Volver a Inicio | La promoción rota en el banner y aparece en la campana |
| 13 | Admin | Dashboard → Actualizar; Movimientos del día; Exportar → Movimientos → CSV | Las cifras incluyen el otorgamiento y el canje; el CSV abre en Excel con tildes y columnas correctas |
| 14 | Admin | Clientes → `cliente.multimarca@ejemplo.test` → Gestionar | Puntos por marca e historial de cambios |
| 15 | Admin | Administradores → intentar desactivar la propia cuenta | Rechazado: no se puede actuar sobre la cuenta propia |

**Cierre opcional:** desactivar la promoción del paso 11 (interruptor) para que la siguiente demostración parta igual. Los puntos y el canje quedan en el historial: es lo esperado en un sistema auditable; para empezar de cero se usa otro cliente de prueba.

## Puntos a mencionar

- Express decide todo lo sensible (saldo, canje, permisos); la pantalla sólo muestra lo que el backend autoriza.
- Cada operación queda auditada sin datos personales; los reportes salen del mismo libro que los saldos.
- Si el backend gratuito estaba dormido, la primera carga tarda hasta un minuto y la pantalla lo explica: abrir la aplicación unos minutos antes.

## Evidencia

Cada ejecución completa se registra en [[05-Desarrollo/Testing]] como T-DEMO, con fecha, entorno (local o desplegado) y revisiones FE/BE.
