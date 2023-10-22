---
title : "[Hair][Yeti] yeti shivering"
header:
  teaser: assets/images/shivering/shivering_thumbnail.png
  overlay_image: assets/images/shivering/shivering_thumbnail.png
  overlay_filter: 0.5
tages:
  - maya
  - hair
  - yeti
---

yeti shivering problem solving experience.  

![alt]({{ site.url }}{{ site.baseurl }}/assets/images/shivering/shivering_root.gif)  
Outsourcing company gave me this shivering data.  

I assumed that curves' data is not fitting for yeti.  
![alt]({{ site.url }}{{ site.baseurl }}/assets/images/errorcheck/inverted2.png)  
It was certain that the root points are the problem.  

![alt]({{ site.url }}{{ site.baseurl }}/assets/images/shivering/shivering_root_cu.gif)  
![alt]({{ site.url }}{{ site.baseurl }}/assets/images/shivering/shivering_root_normal.png)  
I could understand they give me this data because of collision evaluation.  
Talking to my production manager with this problem, I could solve the problems.  

Another cuase was decimal error.  
![alt]({{ site.url }}{{ site.baseurl }}/assets/images/shivering/shivering_transform.gif)  
I heard the outsourcing company doesn't have scripting ability.  
So i just scripted simple python code, to make my company's schedule flow smoothly.  

~~~python
import pymel.core as pm

#####################################################
# 1 ##### delete CV_GRP in the asstname_GRP ##########
#####################################################
# 2 ###### select CV_GRP + assetname_GRP ############
#####################################################
#### please rename CV GRP as "assetname_CV_GRP" ######

cv, GRP = pm.ls(sl=1)

def CvCorrect(cv, GRP):
    keyGRP = pm.duplicate(GRP, po=1, name = GRP.replace("GRP", "keysave_GRP"))[0]

    if GRP.tx.inputs(p=1):
        GRP.tx.inputs(p=1)[0]>>keyGRP.tx
        GRP.tx.inputs(p=1)[0]//GRP.tx
    if GRP.ty.inputs(p=1):
        GRP.ty.inputs(p=1)[0]>>keyGRP.ty
        GRP.ty.inputs(p=1)[0]//GRP.ty
    if GRP.tz.inputs(p=1):
        GRP.tz.inputs(p=1)[0]>>keyGRP.tz
        GRP.tz.inputs(p=1)[0]//GRP.tz
    if GRP.rx.inputs(p=1):
        GRP.rx.inputs(p=1)[0]>>keyGRP.rx
        GRP.rx.inputs(p=1)[0]//GRP.rx
    if GRP.ry.inputs(p=1):
        GRP.ry.inputs(p=1)[0]>>keyGRP.ry
        GRP.ry.inputs(p=1)[0]//GRP.ry
    if GRP.rz.inputs(p=1):
        GRP.rz.inputs(p=1)[0]>>keyGRP.rz
        GRP.rz.inputs(p=1)[0]//GRP.rz

    GRP.t.set(0,0,0)
    GRP.r.set(0,0,0)

    pm.select(cv, hi=1)
    cv_finding_list = pm.ls(sl=1)
    cvs = []
    for x in cv_finding_list:
        if x.nodeType() =='nurbsCurve':
            cvs.append(x.getParent())

    pm.select(cl=1)
    cluster, cluster_handle = pm.cluster(cvs)
    cluster_grp = pm.group(em=1, n=GRP.replace('GRP', 'cluster_GRP'))
    pm.parent(cluster_handle,cluster_grp)

    dcmx = pm.createNode('decomposeMatrix', n = '{}_DCMX'.format(keyGRP))
    keyGRP.worldInverseMatrix>>dcmx.inputMatrix
    dcmx.outputTranslate>>cluster_grp.t
    dcmx.outputRotate>>cluster_grp.rq
    
    pm.parent(cv, GRP)
    
    keyGRP.t>>GRP.t
    keyGRP.r>>GRP.r
    pm.select(cl=1)

CvCorrect(cv,GRP)
~~~
