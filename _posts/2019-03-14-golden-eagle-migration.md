---
title:  Golden Eagle Migration
date:   2019-03-14 09:19:15 -0400
categories: [ maps ]
---

<video src="/assets/vid/golden-eagle-migration.mp4" poster="/assets/img/golden-eagle-migration-thumb.png" controls style="max-width: 100%;">
    Five Years of Golden Eagle Migration in One Minute
</video>

Five years of golden eagle (Aquila chrysaetos) migration in one minute!

In early 2008, The [The Center for Conservation Biology](https://ccbbirds.org/) fitted three juvenile eagles who winter in the Mid-Atlantic with GPS trackers. I’m fascinated by the variability in how closely they follow previous years’ paths as they migrate to Maine, Quebec, and New Brunswick for the summers. The animation adds nuance to my comprehension of their movements compared to a single static map.

I manipulated the data and animated the map (ArcMap) with Python and arcpy for a project in Penn State’s GEOG 485 GIS Programming and Software Development course.

The base map is made with [Natural Earth data](https://www.naturalearthdata.com/). I overlayed the eagles locations as points, scripted the sequential exporting of each day as an image, then compiled those images into a video with [FFmpeg](https://ffmpeg.org).

Many thanks to CCB for their work and for access to the data from their [Tracking Golden Eagles in Eastern North America](https://ccbbirds.org/what-we-do/research/tracking/tracking-projects/tracking-golden-eagles-eastern-north-america/) project, where you can learn more about the birds and the impetus for studying them.
