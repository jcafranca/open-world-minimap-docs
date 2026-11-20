---
title: Setup tutorial
nav_order: 3
---

# Setup tutorial: from scratch
{: .no_toc }

This walkthrough starts with a level that has a player but no minimap: a forest from *Ultimate Nature – Starter* and Unity's *Starter Assets – Third Person* character. It ends with the player following a GPS route to a quest giver. Every step below is a frame from the video.

<video src="assets/video/setup_tutorial.mp4" poster="assets/images/setup_01.jpg" controls muted playsinline width="100%"></video>

[Download the video (MP4, 75 s)](assets/video/setup_tutorial.mp4)

1. TOC
{:toc}

---

## 1. Start with your level

Any scene with a player works. Tag your character `Player` and make sure the scene has a camera tagged `MainCamera`; the minimap fills both in by itself.

![The forest scene before adding the minimap](assets/images/setup_01.jpg)

## 2. Add the minimap

In the Hierarchy, press **+ → UI → Mini Map** (or use **GameObject → UI → Mini Map** in the menu bar).

![Hierarchy + menu, UI, Mini Map](assets/images/setup_02.jpg)

This creates **MiniMap Canvas → Safe Area → MiniMap** and an **EventSystem**. Select **MiniMap**: **Player** and **Heading Source** are already filled in from the `Player` tag and the main camera.

![Player and Heading Source filled in](assets/images/setup_03.jpg)

{: .note }
The canvas is huge in the Scene view because it's a Screen Space Overlay canvas. That's normal: the minimap appears in the top-left corner of the Game view.

## 3. Set World Bounds, Camera Layers and Scan Style

**World Bounds** is the X/Z rectangle your level covers: **X/Y** is its south-west corner, **W/H** its size. Here, the 100 m terrain runs from −50 to 50, so it's X −50, Y −50, W 100, H 100.

![World Bounds set to the terrain](assets/images/setup_04.jpg)

**Camera Layers** decides what the scan draws. Untick the layer your player is on, so the character isn't baked into the map image.

![Camera Layers: untick the player's layer](assets/images/setup_05.jpg)

**Scan Style** picks the look of the map: **Photo** (the scene as it renders) or **Painted** (a stylized map with flat colours, soft outlines and shadows). This tutorial uses Painted. See [Map sources](map-sources.md#scan-style-photo-or-painted).

![Scan Style set to Painted](assets/images/setup_scanstyle.jpg)

## 4. Scan your scene

Choose **Tools → Mini Map → Scan Scene Into Map Texture** in the menu bar.

![Tools, Mini Map, Scan Scene Into Map Texture](assets/images/setup_06.jpg)

A top-down map of everything inside World Bounds is saved as `MiniMapScans/World.png` next to your scene and assigned to the minimap. With Painted, every tree and rock becomes a flat painted shape with a soft outline.

![The scan next to a top-down Scene view](assets/images/setup_07.jpg)

{: .tip }
Scan again whenever you change the level. The map is an image, so it doesn't update by itself.

## 5. Put things on the map

Any GameObject can be a marker. Here, a capsule stands in for a quest giver: **+ → 3D Object → Capsule**.

![Create a capsule as the quest giver](assets/images/setup_08.jpg)

With it selected, press **Add Component**, search for "mini map" and pick **Mini Map Marker**.

![Add Component, Mini Map Marker](assets/images/setup_09.jpg)

Then choose its **Type**: Quest, NPC, Enemy, Teleport, Waypoint or Custom. Each has a built-in icon, or set your own (see [Markers](markers.md)).

![Type set to Quest](assets/images/setup_10.jpg)

![The marker's settings](assets/images/setup_11.jpg)

## 6. Add GPS navigation

Select the **MiniMap** again and add three components: **Mini Map GPS** (routes), **Mini Map Nav Trail** (the glowing trail in the world) and **Mini Map Pins** (the "Add a pin" dialog). Add **Mini Map Auto Travel** too if the character should walk the route by itself (see [Auto-travel](auto-travel.md)).

![Add Component, Mini Map GPS](assets/images/setup_12.jpg)

![GPS, Nav Trail and Pins on the MiniMap](assets/images/setup_13.jpg)

## 7. Bake a NavMesh

GPS routes follow Unity's NavMesh. Create an empty GameObject (**+ → Create Empty**), add a **NavMesh Surface** and set **Use Geometry** to **Physics Colliders**, so grass and leaves don't count as obstacles.

![NavMesh Surface, Use Geometry: Physics Colliders](assets/images/setup_15.jpg)

Press **Bake**. The blue area is where routes can go.

![The baked NavMesh](assets/images/setup_16.jpg)

{: .note }
NavMesh Surface comes with the **AI Navigation** package (Package Manager → Unity Registry → AI Navigation).

## 8. Press Play

The minimap shows the scan, the quest marker and the compass. Click the minimap to open the world map.

![The minimap in play](assets/images/setup_17.jpg)

Click the quest icon. The bottom-left shows your coordinates, the distance and a **Navigate** link.

![The world map with the quest picked](assets/images/setup_18.jpg)

Press **Navigate**: the shortest walkable route appears as flowing gold dots.

![Navigating](assets/images/setup_19.jpg)

Close the map and follow the route. Under the minimap, the destination's coordinates and distance count down.

![Following the route](assets/images/setup_20.jpg)

![Arrived at the quest giver](assets/images/setup_21.jpg)

That's the whole setup. From here:
- Make the minimap rotate with the camera, or change its shape: [Minimap](minimap.md).
- Give buildings their own floor maps: [Interiors & floors](interiors.md).
- Let the character walk the route: [Auto-travel](auto-travel.md).
