# cabify-data-it-marketplace

Marketplace interno de plugins de Cowork para el equipo de Data IT de Cabify.

## Estructura

```
cabify-data-marketplace/
├── .claude-plugin/
│   └── marketplace.json        # catálogo: qué plugins expone este marketplace
└── plugins/
    └── data-toolkit/
        ├── .claude-plugin/
        │   └── plugin.json     # identidad del plugin (nombre, versión, autor)
        ├── skills/
        │   ├── sql-style-guide/
        │   │   └── SKILL.md
        │   └── metric-definitions/
        │       └── SKILL.md
        └── README.md
```

## Notas

- Los plugins viven **dentro de este mismo repo** (`source` relativo en `marketplace.json`), así la Claude GitHub App solo necesita acceso a este repositorio, no a varios.
- Añadir una skill nueva a `data-toolkit` = añadir una carpeta bajo `plugins/data-toolkit/skills/` con su `SKILL.md`. No requiere tocar `marketplace.json`.
- Añadir un plugin nuevo = crear `plugins/<nombre-plugin>/` con su propio `.claude-plugin/plugin.json` y `skills/`, y añadir una entrada en `.claude-plugin/marketplace.json` -> `plugins`.
- Sube la versión (`version`) en `plugin.json` y/o `marketplace.json` cuando quieras que Cowork trate el cambio como una actualización explícita.
