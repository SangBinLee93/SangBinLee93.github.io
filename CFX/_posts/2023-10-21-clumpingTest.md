---
title : "[Houdini][Hair] clumped hair simulation"
header:
  teaser: assets/images/hairClumping/hairClumping_thumbnail.png
  overlay_image: assets/images/hairClumping/hairClumping.png
  overlay_filter: 0.5
tages:
  - houdini
  - hair
---

Stylized animation character's clumping test  

{% include video id="dT2EpjffYmk" provider="youtube" %}

- use Center Curve with pscale(thickness).
- pointDeform with this center curve.
- and blend root with origin.  

If you want, make a result as a restBlend. 
And simulate it again for spliting it again.
