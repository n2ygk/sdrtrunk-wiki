**Version:** 0.3.0

Map
---

The map displays any decoded messages that contain location data like GPS positions.

The map component uses [aliases](Aliases_V0.3.0) to determine the display label, icon 
and color to use when plotting decoded messages.  Update messages from the same 
entity are chained together.

The map uses map tiles from the open street map server.  If you do not have an 
internet connection, no map data will be displayed, however decoded messages 
will be plotted.

#### Default Location and Zoom
Drag the map to re-center the view and use the mouse wheel to zoom in or out.  
Right-click on the map to store the location and zoom level as the map default.

![Map Display](v0.3/images/Map_V0.3.0.png)

**Figure 1:** Map Display