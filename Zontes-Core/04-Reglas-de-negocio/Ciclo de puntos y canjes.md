---
title: "Ciclo de puntos y canjes"
tags: [zontes]
status: planificado
updated: 2026-10-02
---

# Ciclo de puntos y canjes

```text
evento autorizado (origen + ID)
   → validar actor, marca y evento
   → buscar regla activa exacta
   → transacción: registrar evento + movimiento + vencimiento
   → saldo consultable e historial
   → solicitud de canje
   → transacción: reservar/disminuir saldo + disponibilidad + canje
   → comprobante/cupón y traza
   → vencimiento posterior: sólo puntos no consumidos
```

Una regla inactiva no otorga; cambios de cantidad/vigencia afectan sólo nuevos otorgamientos. Sin campo “condición”. **No mantener sólo un saldo mutable**: los movimientos y sus IDs permiten conciliar resultados; definir lotes o método equivalente antes de codificar vencimiento parcial.

Caso de doble evento: mismo origen+ID no da puntos dos veces. Doble canje concurrente: uno falla o ambos tienen saldo/stock suficiente; nunca saldo negativo. Proceso de expiración reejecutable no descuenta dos veces. Una corrección deja nuevo movimiento/auditoría, no borra historia.

Decisiones aún abiertas: DEC-05 origen y validez, DEC-06 consumo/vencimiento, DEC-07 disponibilidad/cupón/reversa, DEC-14 corrección. Estas preguntas no alteran los tipos de eventos ni la forma simple de reglas definida por SRC-02.
