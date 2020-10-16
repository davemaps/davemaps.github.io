---
title:  Building an Augmented Reality Web Map
date:   2020-10-15 15:25:25 -0400
categories: [ maps ]
---

During NACIS 2020, I presented Using Augmented Reality to Communicate Climate Change Pressure on Vancouver Island Marmot Habitat, my capstone project for the Penn State Master of GIS program. [Learn more about the project and test it yourself.](https://marmots.davemaps.com)

Below is a step-by-step guide to creating an augmented reality web map. This guide uses QGIS, Blender, Photoshop, and Xcode on macOS. You could certainly use ArcGIS or another GIS software, and replace the step in Photoshop with GDAL or GIMP, for example. I am not aware of a substitute for Xcode, where we convert the scene to a mobile USDZ file, although one may certainly exist.

# Prepare Your DEM

[![Exporting the DEM from QGIS]({{ "/assets/img/map-ar-how-to-qgis-dem.jpg" | absolute_url }})](/assets/img/map-ar-how-to-qgis-dem.png)

I’ve loaded a large digital elevation model into QGIS. I then created a polygon to use as a clipping mask, which will be the extent of the 3D model. I clip the DEM to my polygon and make sure to export that as a GeoTIFF with the same target coordinate reference system which I’ll use for all of my files.