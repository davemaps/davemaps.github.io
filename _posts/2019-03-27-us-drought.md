---
title:  The United States of Drought
date:   2019-03-27 20:18:18 -0400
categories: [ maps ]
---

<video src="/assets/vid/us-drought-4k.mp4" poster="/assets/img/us-drought-thumb.png" controls style="max-width: 100%;">
    Nineteen years of drought in the United States in one minute.
</video>

Here are nineteen years’ worth of drought maps, animated across just over a minute. Darker red-orange marks more severe drought conditions, as you might have guessed. Look at how parts of Southern California have spent essentially the last decade in drought, with few periods of relief.

I manipulated the data on the map (ArcGIS Pro) with Python and arcpy, scripting the export of each frame as a png. Then I used [GMIC][1] to smooth an extra frame in-between (“tween”) the maps, which helps the animation not feel quite as jumpy. Lastly, I compiled all of those frames into a video with [FFmpeg][2].

The base map is made with [Natural Earth data][3].

Data: [United State Drought Monitor][4]

[1]: https://gmic.eu/
[2]: https://ffmpeg.org/
[3]: https://www.naturalearthdata.com/
[4]: https://droughtmonitor.unl.edu/
