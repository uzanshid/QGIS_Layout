---
name: gis-map-layout
description: Create, revise, compare, and export GIS map layouts (tata letak peta), especially QGIS QPT/QGZ projects. Use for map composition, legends, scale bars, insets, sources, CRS labels, logos, and print-ready exports; not for spatial analysis alone.
---

# GIS Map Layout

Produce a legible, editable, source-backed map for the requested theme, area, organization, and output format. Treat each project's template and latest user-edited layout as design evidence, not as a universal design specification. Do not assume an institution, province, map class, page size, color palette, CRS, scale length, or export DPI from a prior project.

## Establish the map specification

Before composing, identify the theme and intended claim, mapped extent, audience, output size, format, and any supplied QGIS project, template, logo, style, or reference image. Inspect the actual layer names, geometry types, CRS, extents, class values, styles, and metadata. Use the latest user-approved or user-edited artifact as the visual baseline. If a required source agency or date is absent from reliable metadata, ask for it rather than inferring it from a filename or a service URL; continue independent layout work while waiting.

Separate three kinds of text:

- **Data sources:** actual agency and dataset names, with edition or year only when established.
- **Map metadata:** CRS, projection, scale, processing date, map identifier, and limitations when relevant.
- **Internal provenance:** local paths, processing scripts, temporary files, and QA results; keep these in project documentation unless the user wants them printed.

Honor source attribution and license requirements, but do not automatically list local filenames or a visual basemap in the data-source box. Verify any cited cartographic regulation applies to the mapped data type; distinguish official colors from approximate project adaptations.

## Compose or revise the layout

1. If the user supplies a QPT or an existing QGZ, load and inspect it. Preserve its useful structure and editable native items. Loading a QPT and reproducing its appearance from scratch are different operations; use the actual template when requested. Inspect hidden or off-page items, stale titles, logos, data paths, and layer references before reuse.
2. Set the main map and inset extents from their purpose and frame aspect ratios. Keep the subject prominent and context subordinate. Lock each layout map to the intended layer set when project visibility may change.
3. Design the page as related sections. When resizing or shifting one section, move its border/background, content, and neighboring sections together. Check stacking order and whitespace. Do not solve a crowded legend by shrinking text until it is unreadable; first rebalance panel height, spacing, or grouping.
4. Build the legend from the symbols and classes actually visible in the map. Include meaningful no-data, uncovered, or unclassified states. Do not create implied classes merely to fill a legend. Keep line, point, and area symbols distinguishable at print size.
5. Link the scale bar to the correct map, choose units and segment lengths from the mapped extent, and check that the bar fills the allocated space without crowding it. State the coordinate system, projection when applicable, and authority code only after checking the map's actual CRS. A north arrow or inset is useful when it improves orientation; it is not obligatory for every map.
6. Fit title, source, logo, and explanatory text in their boxes with deliberate alignment and margins. Preserve source text as editable layout text where practical. Copy or relink supplied images so the saved project and template can reopen them.

For QGIS template loading, item inspection, and export details, read [references/qgis-layout-workflow.md](references/qgis-layout-workflow.md) when using PyQGIS, QPT, or QGZ.

## Verify the delivered artifact

Check both structure and appearance. Reopen the saved project and exported template; confirm valid data layers, images, fonts, map extents, item positions, and scale-bar linkage. Compare rendered output with the user's reference at full page and normal print size. Inspect title alignment, legend completeness, panel boundaries, source spacing, text clipping, source accuracy, inset placement, and any no-data depiction. Confirm page dimensions, pixel dimensions, and DPI for raster export. If a headless render drops native QGIS text, retry with a GUI-enabled QGIS process before replacing text with raster images.

Save revisions separately when preserving earlier work matters. Deliver the requested project, reusable template/style, and exported map with concise notes on what changed and any unresolved source or display limitation. Stop verification once the relevant risks have been checked; do not turn every layout edit into a full spatial-data audit.
