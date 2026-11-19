---
title: Getting started
nav_order: 2
---

# Getting started
{: .no_toc }

1. TOC
{:toc}

---

## Requirements

| | |
|---|---|
| **Unity** | Unity 6 (developed and tested on 6000.6). |
| **Packages** | **uGUI** (`com.unity.ugui`), required. It's in Unity's standard templates; otherwise install it from the Package Manager. GPS uses the built-in **AI** module (`com.unity.modules.ai`). |
| **Render pipeline** | Tested on **Built-in**, **URP** and **HDRP**. The minimap and world map are uGUI with a standard UI shader, so they look the same in every pipeline. In HDRP, map cameras (scanning and the live-camera source) automatically skip the sky, fog and eye adaptation. |
| **Input** | No dependency on the old or new Input System. The minimap's UI uses the EventSystem, so both work. |
| **Platforms** | Desktop, mobile (touch-sized controls on phones and tablets) and console (controller-friendly UI). |
| **Demo scene only** | **AI Navigation** (`com.unity.ai.navigation`) and Unity's free **Starter Assets – Third Person**. See [The demo scene](demo-scene.md). |

## What's in the package

Open-World Minimap is a **tool**, not a prefab. It's a set of components plus editor menus that build everything for you:

| Folder | What it holds |
|---|---|
| `Assets/MiniMap/Runtime` | The components: MiniMap, MiniMapMarker, MiniMapArea, MiniMapGPS, MiniMapAutoTravel, MiniMapNavTrail, MiniMapPins, SafeAreaFitter, MiniMapIconSet. |
| `Assets/MiniMap/Editor` | The **GameObject → UI → Mini Map** menu and the scene scanner. |
| `Assets/MiniMap/Resources/MiniMap` | The built-in art: icons, frames, the map shader. |
| `Assets/MiniMap/Demo` | The playable demo scene and its scripts (safe to delete). |
| `Assets/MiniMap/Sample` | A sample illustrated map. |
| `Assets/MiniMap/Documentation` | The offline copy of this documentation. |

All runtime code is in the `MiniMapUI` namespace, and the demo's code is in `MiniMapUI.Demo`.

## Install

1. Buy and download **Open-World Minimap** from the Unity Asset Store.
2. In Unity, open **Window → Package Manager → My Assets**, find the package and press **Import**.
3. Import everything, or untick `Demo` if you don't want the sample scene.

## Quick start

1. In your scene, choose **GameObject → UI → Mini Map**. This creates:
   - **MiniMap Canvas**, a Screen Space Overlay canvas scaled to a 1920×1080 reference with *Expand* matching, which looks right at 16:9, 16:10, 21:9 and on phones.
   - **Safe Area**, which keeps the HUD clear of notches and rounded corners.
   - **MiniMap**, the minimap itself, anchored to the top-left corner. All its settings are on this object.
   - An **EventSystem**, if the scene doesn't have one.
2. Select the MiniMap. **Tools → Mini Map → Select Mini Map Settings** (`Ctrl/Cmd + Shift + M`) jumps straight to it. Check:
   - **Player**, filled in automatically if your character is tagged `Player`.
   - **Heading Source**, usually your gameplay camera, filled in automatically from `Camera.main`.
3. Set **World Bounds** to the X/Z area your level covers.
4. Give it a map. The quickest way is **Tools → Mini Map → Scan Scene Into Map Texture**. See [Map sources](map-sources.md).
5. Press Play.

To show things on the map, add a **MiniMapMarker** to any GameObject. See [Markers](markers.md).

To add navigation, add **MiniMapGPS** to the MiniMap and bake a NavMesh. See [GPS navigation](gps-navigation.md).

{: .tip }
The [setup tutorial](setup-tutorial.md) walks through all of this in the editor, click by click, in a forest scene with a Starter Assets character.
