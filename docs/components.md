---
title: Component reference
nav_order: 14
---

# Component reference

| Component | Where | Purpose |
|---|---|---|
| **MiniMap** | MiniMap object (Canvas → Safe Area → MiniMap) | The minimap and world map: map source, rotation, shape, zoom, compass, floors, world map, touch sizing, art. |
| **MiniMapMarker** | Any world object | Shows the object on the map. See [Markers](markers.md). |
| **MiniMapIconSet** | Asset (**Create → Mini Map → Icon Set**) | Your own named icons; swap sets to restyle every marker. |
| **MiniMapArea** | A collider around an interior or floor | Its own map, zoom and floor label. See [Interiors & floors](interiors.md). |
| **MiniMapGPS** | MiniMap object | Picking targets, routes on the map, the popup and coordinates. See [GPS navigation](gps-navigation.md). |
| **MiniMapPins** | MiniMap object | The Add a pin dialog and saved pins. See [Map pins](pins.md). |
| **MiniMapAutoTravel** | MiniMap object | Walks the player along the route. See [Auto-travel](auto-travel.md). |
| **MiniMapNavTrail** | MiniMap object | The glowing particle trail along the route. |
| **SafeAreaFitter** | Safe Area object | Fits the HUD to `Screen.safeArea`. |

## Editor menus

| Menu | |
|---|---|
| **GameObject → UI → Mini Map** | Create a ready-to-use minimap (also in the Hierarchy's **+** menu). |
| **Tools → Mini Map → Select Mini Map Settings** (`Ctrl/Cmd + Shift + M`) | Jump to the MiniMap component. |
| **Tools → Mini Map → Scan Scene Into Map Texture** | Scan the world (MiniMap selected) or an interior or floor (MiniMapArea selected). |
| **Tools → Mini Map → Build Demo Scene** | Rebuild the demo, with your render pipeline's materials. |

While playing, objects the minimap creates in the world (pins, the particle trail, the map camera) are grouped under **MiniMap (runtime)** in the Hierarchy.
