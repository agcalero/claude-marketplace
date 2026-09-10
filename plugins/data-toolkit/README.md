# data-toolkit

Plugin interno de Cabify Data IT para Claude Cowork.

## Skills incluidas

- **sql-style-guide**: convenciones de estilo SQL del equipo.
- **metric-definitions**: diccionario de métricas de negocio (bookings, GMV, trips...).

## Cómo probarlo en local (Claude Code)

```bash
claude --plugin-dir ./plugins/data-toolkit
```

## Cómo añadir una skill nueva

1. Crea una carpeta en `skills/<nombre-skill>/` con un `SKILL.md` (frontmatter con `description`).
2. No hace falta tocar `plugin.json` ni `marketplace.json` — se descubre automáticamente.
3. Abre una merge request; una vez mergeada a `main`, el pipeline de CI sincroniza el repo espejo y Cowork la recoge sola en la siguiente sesión de cada usuario.
