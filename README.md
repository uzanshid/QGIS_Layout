# GIS Map Layout

Reusable Codex skill for composing, revising, and checking GIS map layouts. It covers map extent, inset, legend, scale bar, CRS text, source attribution, editable QGIS items, and print-ready export. The skill does not fix an institution, region, page size, color palette, CRS, or scale length.

## Files

- [`SKILL.md`](SKILL.md): skill instructions and activation scope.
- [`references/qgis-layout-workflow.md`](references/qgis-layout-workflow.md): QGIS QPT/QGZ and PyQGIS guidance.
- [`docs/evaluasi-rangkaian-layout-gis.md`](docs/evaluasi-rangkaian-layout-gis.md): lessons from the project that prompted the skill.

## Local installation

Place `SKILL.md` and the `references` directory in `$CODEX_HOME/skills/gis-map-layout/` (or `~/.codex/skills/gis-map-layout/` when `CODEX_HOME` is unset). Invoke it with `$gis-map-layout` when preparing a map layout.
