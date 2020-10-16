---
title:  Building an Augmented Reality Web Map
date:   2020-10-15 15:25:25 -0400
categories: [ maps ]
---

WORK IN PROGRESS

During NACIS 2020, I presented Using Augmented Reality to Communicate Climate Change Pressure on Vancouver Island Marmot Habitat, my capstone project for the Penn State Master of GIS program. [Learn more about the project and test it yourself.](https://marmots.davemaps.com)

Below is a step-by-step guide to creating an augmented reality web map. Click on any of the screenshots for a larger view.

This guide uses QGIS, Blender, Photoshop, and Xcode on macOS. You could certainly use ArcGIS or another GIS software, and replace the step in Photoshop with GDAL or GIMP, for example. I am not aware of a substitute for Xcode, where we convert the scene to a mobile USDZ file, although one may certainly exist.

## Prepare Your DEM

[![Exporting the DEM from QGIS]({{ "/assets/img/map-ar-how-to-qgis-dem.jpg" | absolute_url }})](/assets/img/map-ar-how-to-qgis-dem.png)

I’ve loaded a large digital elevation model into QGIS. I then created a polygon to use as a clipping mask, which will be the extent of the 3D model. I clip the DEM to my polygon and make sure to export that as a GeoTIFF with the same target coordinate reference system which I’ll use for all of my files.

## Prepare Your Map

[![Exporting the map from QGIS]({{ "/assets/img/map-ar-how-to-qgis-export-map.jpg" | absolute_url }})](/assets/img/map-ar-how-to-qgis-export-map.png)

Next I need to save my map which will drape over the 3D model as a single GeoTIFF. You can see here I’m using satellite imagery as a basemap and have symbolized the habitat layers with some transparency, the habitat projected to be lost in a striped red and the remaining habitat in bright green. I used the mask layer as the extent and increased the resolution of the exported file to make sure there is plenty of detail in the imagery. This is a balancing act between file sizes and detail, of course.
