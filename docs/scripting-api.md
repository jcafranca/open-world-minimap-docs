---
title: Scripting API
nav_order: 15
---

# Scripting API

All types are in the `MiniMapUI` namespace.

```csharp
using MiniMapUI;

MiniMap map = FindAnyObjectByType<MiniMap>();
MiniMapGPS gps = map.GetComponent<MiniMapGPS>();

// Minimap
map.rotation = MiniMap.RotationMode.Rotating;   // or Fixed
map.ToggleRotation();
map.ZoomBy(0.8f);                                // < 1 zooms in
map.shape = MiniMap.Shape.Square;

// World map
map.OpenWorldMap();  map.CloseWorldMap();  map.ToggleWorldMap();
map.ZoomWorldMap(0.75f);
map.CenterWorldMapOnPlayer();                    // what the find-me button does
bool open = map.IsWorldMapOpen;

// Clicks on the map (world position under the cursor)
map.MapClicked += (worldPos, eventData) => Debug.Log(worldPos);
MiniMapMarker m = map.MarkerAt(screenPos, eventCamera); // the icon under a screen point, or null

// GPS
gps.MarkPoint(pos);            // drop a marker (what a click does)
gps.MarkMarker(marker);        // mark one of your markers (what clicking its icon does)
gps.NavigateToMarkedPoint();   // what the Navigate link does
gps.SetDestination(marker);    // navigate to a marker; the route follows it if it moves
gps.SetDestination(pos);       // navigate to a point straight away
gps.ClearDestination();        // what Cancel does
float metresLeft = gps.RemainingDistance;
bool onNavMesh = gps.RouteIsNavMesh;
gps.DestinationSet += p => { };
gps.Arrived += () => { };

// Pins
var pins = map.GetComponent<MiniMapPins>();
MiniMapMarker pin = pins.AddPin(0, pos);       // type index into pins.types
pins.RemovePin(pin);
pins.RemoveAllPins();

// Icons
map.iconSet = myIconSet;                       // restyle all icons
marker.iconName = "Chest";                     // pick a named icon from the set
marker.SetIcon(myTexture2D);                   // any texture as the icon
Sprite shown = map.ResolveIcon(marker, out Color tint, out float scale);

// Auto-travel
var travel = map.GetComponent<MiniMapAutoTravel>();
travel.PauseForManualControl();  // call each frame the player steers
travel.Cancel();
bool walking = travel.IsTraveling;
```

## Hooking up your own keys

The minimap has no input bindings of its own, so it works with any input setup. For example, with the Input System:

```csharp
using MiniMapUI;
using UnityEngine;
using UnityEngine.InputSystem;

public class MapKeys : MonoBehaviour
{
    public MiniMap map;

    void Update()
    {
        var k = Keyboard.current;
        if (k == null) return;
        if (k.mKey.wasPressedThisFrame) map.ToggleWorldMap();
        if (k.tabKey.wasPressedThisFrame) map.ToggleRotation();
        if (k.equalsKey.wasPressedThisFrame) map.ZoomBy(0.8f);
        if (k.minusKey.wasPressedThisFrame) map.ZoomBy(1.25f);
    }
}
```
