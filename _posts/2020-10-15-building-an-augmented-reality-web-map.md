---
title:  Building an Augmented Reality Web Map
date:   2020-10-15 15:25:25 -0400
categories: [ maps ]
---

WORK IN PROGRESS

During [NACIS 2020](https://nacis.org), I presented Using Augmented Reality to Communicate Climate Change Pressure on Vancouver Island Marmot Habitat, my capstone project for the [Penn State Master of GIS program](https://gis.e-education.psu.edu/mgis). [Learn more about the project and test it yourself.](https://marmots.davemaps.com)

Below is a step-by-step guide to creating an augmented reality web map. Click on any of the screenshots for a larger view.

This guide uses [QGIS](https://qgis.org), [Blender](https://blender.org) and the [BlenderGIS plugin](https://github.com/domlysz/BlenderGIS), [Photoshop](https://www.adobe.com/products/photoshop.html), and [Xcode](https://developer.apple.com/xcode/) on macOS. You could likely use [ArcGIS](https://www.esri.com/en-us/arcgis/products/arcgis-pro/overview) or other GIS software, and replace the step in Photoshop with [GDAL](https://gdal.org) or other image manipulation software, for example. I am not aware of a substitute for Xcode, where we convert the scene to a mobile USDZ file, although one may certainly exist.

## Prepare Your DEM

[![Exporting the DEM from QGIS]({{ "/assets/img/map-ar-how-to-qgis-dem.jpg" | absolute_url }})](/assets/img/map-ar-how-to-qgis-dem.png)

I’ve loaded a large digital elevation model into QGIS. I then created a polygon to use as a clipping mask, which will be the extent of the 3D model. I clip the DEM to my polygon and make sure to export that as a GeoTIFF with the same target coordinate reference system which I’ll use for all of my files.

## Prepare Your Map

[![Exporting the map from QGIS]({{ "/assets/img/map-ar-how-to-qgis-export-map.jpg" | absolute_url }})](/assets/img/map-ar-how-to-qgis-export-map.png)

Next I need to save my map which will drape over the 3D model as a single GeoTIFF. You can see here I’m using satellite imagery as a basemap and have symbolized marmot habitat layers with some transparency, the habitat projected to be lost in a striped red and the remaining habitat in bright green. I used the mask layer as the extent and increased the resolution of the exported file to make sure there is plenty of detail in the imagery. This is a balancing act between file sizes and detail, of course.

## Clip the Map TIFF

[![Clipping the map TIFF in QGIS]({{ "/assets/img/map-ar-how-to-qgis-clip-tif.jpg" | absolute_url }})](/assets/img/map-ar-how-to-qgis-clip-tif.png)

Because these GeoTIFF files are huge, I’m going to trim off any bit of extra that I can, clipping the newly exported map image by that same mask polygon.

## Two Clipped TIFFs

[![The clipped TIFF in QGIS]({{ "/assets/img/map-ar-how-to-qgis-map-clipped.jpg" | absolute_url }})](/assets/img/map-ar-how-to-qgis-map-clipped.png)

That leaves us with two clipped TIFs that we’re going to use to make the 3D model in the next step.

## Importing into Blender with BlenderGIS

[![Importing the DEM into Blender]({{ "/assets/img/map-ar-how-to-blender-import-dem.jpg" | absolute_url }})](/assets/img/map-ar-how-to-blender-import-dem.png)

Now I move into [Blender](https://blender.org), a popular free and open source 3D modeling software. Key to making everything work, especially for someone new to working with geospatial data in 3D (like me), is the [BlenderGIS plugin](https://github.com/domlysz/BlenderGIS). Follow the BlenderGIS instructions to get it installed, and then you’re ready to go.

The first step in Blender is to use the BlenderGIS plugin (click the GIS button at the top left of the viewport) to import the DEM as a raw data build, which creates the 3D mesh.

## First Look at the Model

[![Viewing the model for the first time in Blender]({{ "/assets/img/map-ar-how-to-blender-import-dem2.jpg" | absolute_url }})](/assets/img/map-ar-how-to-blender-import-dem2.png)

This can take a bit of time to process, but this is what you end up with. Depending on a number of factors, like the resolution of your DEM, the mesh might have some visible banding like you see here.

## Smoothing

[![Applying a Smooth modifier in Blender]({{ "/assets/img/map-ar-how-to-blender-smooth.jpg" | absolute_url }})](/assets/img/map-ar-how-to-blender-smooth.png)

It’s probably a good idea to smooth the model at least a little. You could also choose to use the Decimate modifier (with the un-subdivide setting) at this step in the process to reduce the number of points in the mesh for big file size savings.

## Importing Our Map onto the Model

[![Importing the map TIFF in Blender]({{ "/assets/img/map-ar-how-to-blender-import-map.jpg" | absolute_url }})](/assets/img/map-ar-how-to-blender-import-map.png)

Now that we have our 3D mesh ready to go, it’s time to import our map georaster on top of the mesh, again using the Blender GIS plugin.

## Imported Map

[![Viewing the map on the model for the first time in Blender]({{ "/assets/img/map-ar-how-to-blender-import-map2.jpg" | absolute_url }})](/assets/img/map-ar-how-to-blender-import-map2.png)

BlenderGIS uses the map as a custom material for the surface of the model and we’re getting closer to a finished product.

## Scaling in Blender

[![Scaling the model in Blender]({{ "/assets/img/map-ar-how-to-blender-scaling.jpg" | absolute_url }})](/assets/img/map-ar-how-to-blender-scaling.png)

My last step in Blender before exporting is to scale the model down a good bit, to get its dimensions relative to the real world more manageable for when we display this in AR. In this example I also do more scaling in Xcode, but liked the flexibility of breaking it into two steps so I could make fine adjustments later. Your mileage may vary!

## Exporting a USD from Blender

[![Exporting the model from Blender]({{ "/assets/img/map-ar-how-to-blender-export.jpg" | absolute_url }})](/assets/img/map-ar-how-to-blender-export.png)

And now we export from Blender as a Universal Scene Description file so that we can move into Xcode.



