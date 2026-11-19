---
title: Performance
nav_order: 17
---

# Performance

- **One draw for the map:** the map is drawn with a single UI shader. Pan, zoom, rotation and the soft edge are all done in the shader, with no masks.
- **Cheapest setup:** texture and scanned maps cost nothing extra per frame. The live camera source renders one extra orthographic camera.
- **Icons and route dots** reuse pooled UI Images instead of creating new ones every frame.
- **GPS** recalculates routes every **Repath Interval** (0.25 s), not every frame.
- **Scans** are made in the editor, so big worlds don't cost anything at runtime.
