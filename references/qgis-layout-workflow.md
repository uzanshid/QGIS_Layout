# QGIS layout workflow

Read this reference when a task uses QGIS projects (`.qgz`), layout templates (`.qpt`), PyQGIS, or QGIS exports. Adapt to the installed QGIS version and the user's specified design.

## Inspect before editing

- Open the saved QGZ and report invalid layers. Record each relevant layout item's type, ID, position and size in page units, z-order, visibility, text, image path, map extent, CRS, and map layer set. Item IDs are useful but may be absent or duplicated in old templates; combine ID, type, geometry, and content when identifying an item.
- Parse the QPT with `QDomDocument` and load it through `QgsPrintLayout.loadFromTemplate(...)`. Verify page count and dimensions after loading. Inspect and remove obsolete or off-page content only after checking whether it serves a purpose.
- Compare the latest user-edited QGZ with prior QPT/PNG output when both exist. Use the user-edited project as the current design reference; preserve the original file and write a revision.

## Implement

- Use `QgsLayoutItemMap` with an explicit CRS, intended layer set, and `setKeepLayerSet(True)` where needed. Fit extent to the frame aspect ratio with suitable geographic padding; inspect the rendered result because a mathematically fitted extent can still have poor visual balance.
- Use native `QgsLayoutItemLabel` for text, `QgsLayoutItemPicture` for images, `QgsLayoutItemScaleBar` linked to the main map, and editable QGIS styles when feasible. Set alignment and margins explicitly for centered titles. Check picture paths after relocation.
- Treat panel geometry as a group even if QGIS stores it as separate shapes, maps, labels, swatches, and pictures. After moving an inset or changing a scale panel's height, recalculate the legend's top, row spacing, bottom, and source panel clearance. Check borders and z-order in the exported image.
- Drive legend rows from the rendered layer categories or a checked class manifest. Confirm a swatch's color, hatch, line width, and label agree with the QML and visible features. Do not confuse a missing-source status with a land-cover class.
- Keep source agency/dataset text distinct from CRS and internal processing notes. Verify the map item's CRS before printing an EPSG code. The chosen format may have separate lines for datum/coordinate system, projection, and CRS code.

## Export and inspect

- Save QGZ and QPT, then reopen both in a fresh QGIS process. Check layer and image validity in each. A QPT alone may depend on a project to resolve its layers, so test it with the intended project context.
- Export at the requested page size and DPI. Compare actual pixel dimensions with page dimensions and DPI; allow ordinary rounding. Check the return code from `QgsLayoutExporter` and that the output image can be decoded.
- Inspect the full rendered map and crowded regions at native resolution: legend, title, source, scale and orientation panel, and inset. Programmatic checks cannot establish readability or visual balance.
- On some environments, offscreen QGIS export can omit or distort editable text. If this is observed, use a GUI-enabled QGIS session/process and rerender; do not silently substitute rasterized labels when editability matters.
