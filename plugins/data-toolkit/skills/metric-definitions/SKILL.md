---
description: Definiciones oficiales de métricas de negocio de Cabify (bookings, GMV, trips, etc.) — usar cuando se pregunte por una métrica o se necesite calcularla, para asegurar consistencia con las definiciones acordadas por el equipo.
---

# Diccionario de métricas de negocio

## Instrucciones

Cuando se pida calcular, explicar o interpretar una métrica de negocio, usa exactamente estas definiciones en lugar de inferirlas del nombre de la columna:

| Métrica            | Definición                                                                 | Tabla fuente        |
| ------------------- | --------------------------------------------------------------------------- | -------------------- |
| `bookings`           | Solicitudes de viaje confirmadas por el pasajero, independientemente de si se completan | `fct_bookings`        |
| `trips` / `completed_trips` | Viajes que llegaron a estado `completed`                              | `fct_trips`            |
| `gmv`                 | Importe bruto facturado al pasajero antes de comisiones, en la moneda local convertida a EUR | `fct_trips` (`gross_amount_eur`) |
| `active_driver`       | Conductor con al menos 1 viaje completado en los últimos 30 días            | `fct_trips` + `dim_drivers` |

Si una pregunta usa un término ambiguo (p.ej. "ventas", "actividad"), pregunta a qué métrica de esta tabla se refiere antes de calcular nada, salvo que el contexto lo deje claro.

<!-- TODO: sustituir por las definiciones reales y mantenerlas actualizadas — esta es la fuente de verdad para el equipo. -->
