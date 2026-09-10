---
description: Guía de estilo SQL de Cabify — usar al escribir o revisar queries SQL para mantener convenciones de nombrado, CTEs y formato consistentes en todo el equipo de datos.
---

# Guía de estilo SQL de Cabify

## Instrucciones

Al escribir o revisar SQL para Cabify, sigue estas convenciones:

1. **Nombrado**: tablas y columnas en `snake_case`, en inglés. Prefijar las tablas de staging con `stg_`, las de marts con `dim_`/`fct_` según corresponda.
2. **CTEs**: usar CTEs (`WITH`) en lugar de subqueries anidadas para mejorar la legibilidad. Nombrar cada CTE describiendo qué hace, no `cte1`, `cte2`.
3. **Formato**: una columna por línea en el `SELECT` cuando haya más de 3 columnas; palabras clave (`SELECT`, `FROM`, `WHERE`, `JOIN`) en mayúsculas.
4. **Joins**: siempre usar `JOIN` explícito con el tipo (`LEFT JOIN`, `INNER JOIN`), nunca joins implícitos en el `WHERE`.
5. **Fechas**: comparar siempre en UTC salvo que se indique lo contrario, y documentar la zona horaria si el resultado se presenta en hora local.

## Ejemplo

```sql
WITH active_drivers AS (
    SELECT
        driver_id,
        city_id
    FROM stg_drivers
    WHERE status = 'active'
),

trips_last_30d AS (
    SELECT
        driver_id,
        COUNT(*) AS trip_count
    FROM fct_trips
    WHERE trip_date >= CURRENT_DATE - INTERVAL '30 days'
    GROUP BY driver_id
)

SELECT
    d.driver_id,
    d.city_id,
    COALESCE(t.trip_count, 0) AS trip_count
FROM active_drivers d
LEFT JOIN trips_last_30d t ON d.driver_id = t.driver_id
```

<!-- TODO: sustituir este contenido de ejemplo por las convenciones SQL reales del equipo. -->
