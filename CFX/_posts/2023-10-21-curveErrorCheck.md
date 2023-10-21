---
title : "[Hair][Python] checking script for error curves"
header:
  teaser: assets/images/errorcheck/shot_231022_000438.png
  overlay_image: assets/images/errorcheck/shot_231022_000438.png
  overlay_filter: 0.5
tages:
  - maya
  - hair
---

check lots of hair with python scripting.

![Alt Text](assets/images/errorcheck/ErrorCheck.gif)

### Error events
- green : root point is too far from subdivision
- red : root point is on the uv boarderline.
- white : root vector is opposite from mesh normal vector.
(This script is available for multi yeti nodes, multi meshes)

#### [green] root point is too far from mesh's subdivision
> This is just for convinience for grooming and scripting. 
![Alt Text](assets/images/errorcheck/rootSnap.gif)
(This script include snapping function)

#### [red] root point is on the uv boarderline.
> This makes the curve cannot follow uvPin or follicle.
because there are no uv coordinate for the curve.

(This script include pinning curves to mesh with uvPin node)

#### [white]

