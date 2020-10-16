---
title:  Monitoring Water Levels in the Asheville Metro Area
date:   2020-01-05 10:37:37 -0500
categories: [ maps ]
---

[![Screenshot of an interactive map of the Asheville, NC area.]({{ "/assets/img/map-asheville-water-levels.jpg" | absolute_url }})](http://personal.psu.edu/dcm20/geog585/term/index.html)

For an open web mapping graduate course, I created an [interactive map for Monitoring Water Levels in the Asheville Metro Area](http://personal.psu.edu/dcm20/geog585/term/index.html).

I created the custom basemap from scratch in QGIS, using data obtained through the [USDA Natural Resources Conservation Service data gateway](https://gdg.sc.egov.usda.gov). I then pre-baked all the tiles using TileMill and use Leaflet to display the interactive map.

The feature layers (water level gauges) are hand-crafted, artisanal GeoJSON files. Clicking on a water gauge point on the map will then go make an API request to the USGS Water Service to retrieve live data on the water level at that point, which I then chart using D3.

[Try it out!]((http://personal.psu.edu/dcm20/geog585/term/index.html))
