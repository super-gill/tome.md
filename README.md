# tome.personal

Personal books and notes. A **TOME instance**.

This site is the platform from [`tome.platform`](https://github.com/super-gill/tome.platform)
plus this repo's own content. (Formerly `tome.md`, which used to double as the
platform root; that role now lives in `tome.platform`.)

## What lives here (per-instance content)

- `Books/` - personal documents (recipes, Spanish, etc.)
- `tome.json` - branding
- `export-branding/` - PDF brand presets

Platform files (`index.html`, `index.js`, `styles.css`, `libs/`, `tools/`) come
from `tome.platform`. Don't edit them here.

## Updating the platform

```bash
bash update.sh          # macOS/Linux
powershell -File update.ps1   # Windows
```

Platform version: **v2.10.0**
