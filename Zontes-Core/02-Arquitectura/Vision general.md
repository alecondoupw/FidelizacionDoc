---
title: "Visión general de arquitectura"
tags: [zontes]
status: planificado
updated: 2026-10-02
---

# Visión general de arquitectura

**Frentes lógicos:** `FE_REPO` (Next.js/TypeScript) y `BE_REPO` (Express/TypeScript). La forma física del repositorio compartido pedido en SRC-01 p. 2 sigue en DEC-01: podrían ser dos repositorios Git o paquetes de uno, sin inventar rutas. Ambos frentes aún no existen en la raíz inspeccionada. Los contratos de API y revisión conjunta se guardan aquí; código, dependencias y configuración operativa van a las rutas que confirme Paulo.

```text
Cliente/Admin → Next.js UI → ID token Firebase Auth
                        ↓ HTTP/JSON
                   Express API
             verifica token + rol + marca
              valida reglas / idempotencia
                        ↓ Admin SDK
           Firestore (movimientos, reglas,
              canjes, contenido, auditoría)
                        ↓
                 Storage (si aplica)
```

Next.js presenta y valida formularios para UX; **Express vuelve a validar** identidad, rol, marca, estado y entradas. No duplicar motores de puntos ni endpoints sensibles en Next.js. Admin SDK omite las reglas de seguridad de Firestore; cada consulta/escritura con Admin SDK necesita control explícito en el backend. No enviar credenciales de servicio al navegador.

**Frentes lógicos:** auth/perfiles y vinculación por correo; eventos y movimientos; reglas/vencimiento; beneficios/canjes; administración; reportes/exportes; contenido por marca. Modelo y contratos en [[02-Arquitectura/Modelo de datos y contratos]]. Pruebas cruzadas por versión FE+BE y datos sintéticos aislados.

Esta es la [[02-Arquitectura/Base tecnica documentada]] de SRC-02 pp. 11–15 y SRC-03 pp. 11–13, no runtime comprobado. DEC-01 fija organización/rutas; DEC-02 fija recursos, cuentas y entornos de Firebase. Una excepción al stack documentado requiere decisión explícita de Paulo.
