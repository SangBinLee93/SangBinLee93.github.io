---
title : "[2024] Vanellope Facial Rig"
header:
  teaser: /assets/images/portfolio/VNL.png
  video:
    id: jW-nAg0ITXI
    provider: youtube
tages:
  - maya
  - rig
  - facial rig
  - sculpt
  - modeling
  - animation
---

[Personal][Facial Rig][Fan Art][RIG][MOD][ANIM]

Maya 2024 Multi-Skin Clusters / Rig / Mod / Anim

<h3> Modelling </h3>

<img src="/assets/images/vanellope/mod_bd.gif" style="width:720px">

process
- modeling rough mesh in maya
- sculpting dynamesh in zbrush
- modeling detail retopology in maya
- modeling cloth simulation mesh in marvelousDesigner
- modeling detail face shape in maya
- texturing face in substance painter

<h3> Basic rig </h3>

<img src="/assets/images/vanellope/basic_BD.png" style="width:720px">

process
- blendshape[shape fix] (purple)
- multi SkinClusters[lip, eye, ear&nose&cheek1, cheeck2, eyebrow] base on world (yellow)
- main SkinCluster[neck, head] (red)
- add SkinCluster[up, mid, low] following main (blue)  <img src="/assets/images/vanellope/bindPreMatrix.png" style="width:720px">
- add nonLinear,lattice, deformers (green)
- add deltaMushes

<h3> Sculpting Mouth (+ eye ) </h3>

<img src="/assets/images/vanellope/bs_BD.gif" style="width:720px">

process
- rigging face, based on joint
- extracting distance weight value from world based mouth rig
- sculpting blendshape (out/in/up/down)
- painting deltaMush influence weight
- made (attribute * weight) multiplyer

<h3> Bezier Curve = Mouth/Eye's Low Curve </h3>

<img src="/assets/images/vanellope/wireDeform_BD.gif" style="width:720px">

process
- rigging Bezier curve(+ upVector curve) as low curve
- (mouth only) devide left/right curve as high curve
- connecting wire deformer to hire curve
- rigging final joints with motion path following high curve
- The football shape idea from (hippydrome.com). I would say it is very similar with 'Central Limit Theorem'. => thickness, front, height

<img src="/assets/images/vanellope/CLT_BD2.gif" style="width:720px">

<img src="/assets/images/vanellope/CLT_BD.gif" style="width:720px">