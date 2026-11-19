---
title: Troubleshooting
nav_order: 18
---

# Troubleshooting

| Problem | Fix |
|---|---|
| The map is blank | Check **World Bounds** covers your level, then scan again. For an interior, check the area's box covers it. |
| The house or level isn't on the map | The map is an image: scan again after changing the level. |
| The scan is washed out or one flat colour | Use the built-in scan menu (it turns off fog and renderer features and looks straight down). Check **Camera Layers**. |
| Trees or props are missing from the scan | Check their layer is ticked in **Camera Layers**. Some asset packs put vegetation on unusual layers (even the UI layer). |
| My character is baked into the map | Put the player on its own layer and untick it in **Camera Layers**, then scan again. |
| Nothing happens when clicking the map | The scene needs an EventSystem, and the canvas a GraphicRaycaster (the Mini Map menu adds both). |
| The route is a straight line | No NavMesh found. Bake one, and check **Agent Type ID** and **Area Mask**. |
| The character brushes walls when auto-travelling | Raise **Navigation Radius**, or bake the NavMesh agent at least as wide as the character's collider (radius + skin width). |
| My character controller fights auto-travel | Pause your controller while `MiniMapAutoTravel.IsTraveling` is true (see [Auto-travel](auto-travel.md)). |
| The map doesn't turn in Rotating mode | It follows **Heading Source**. Turn that camera, or clear the field to follow the player. |
| The floor badge flickers on stairs | Raise **Floor Check Height** on the MiniMap. |
| I can't find the settings | **Tools → Mini Map → Select Mini Map Settings** (`Ctrl/Cmd + Shift + M`). |
| The minimap looks blurry | Set the Game view to its real resolution at 1× scale, and untick *Low Resolution Aspect Ratios*. |
| The demo is pink or white in URP / HDRP | Run **Tools → Mini Map → Build Demo Scene** once to rebuild it with your pipeline's materials. |
| The Asset Store validator warns about the demo | Validate outside Play mode. |

Still stuck? [Open an issue](https://github.com/jcafranca/open-world-minimap-docs/issues) on this repository with your Unity version, render pipeline and a screenshot.
