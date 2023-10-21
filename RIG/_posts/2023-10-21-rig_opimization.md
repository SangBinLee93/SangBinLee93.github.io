---
title : "[Study][Tip] Optimizing a rig file"
header:
  teaser: /assets/images/rig_optimize/realtimerigmanip.jpg
  overlay_image: /assets/images/rig_optimize/realtimerigmanip.jpg
tages:
  - maya
  - study
---

[original document : Disney's SIGGRAPH 2019 Talk](https://disneyanimation.com/publications/?drawer=/publications/optimizing-rig-manipulation-with-gpu-and-parallel-evaluation/)
<br/>
![styled-image]({{ site.url }}{{ site.baseurl }}/assets/images/rig_optimize/rig_opimize.png)

## Key Concept
- Optimize rig for Parallel evaluation, multi-thread.
- Use multi/smaller nodes rather than fewer/heavy nodes<br/>
![styled-image]({{ site.url }}{{ site.baseurl }}/assets/images/rig_optimize/singlethread_vs_multithread.png)
<br/>

##### Rig Opimizations

- Create Unique Deformer Chains
> ( NO!! )
Shape → Deformer → Multiple Shapes  

- Optimize Mesh Size
> split meshes per 1000 to 2000 points  
> and comebine the cut-up meshes to a single mesh with a custom parallel blending node.  
![styled-image]({{ site.url }}{{ site.baseurl }}/assets/images/rig_optimize/split.png){: style="width: 40%;"}  
> Sometimes howerver, too many meshes are much slower than combined mesh. Cutting up appropriately is very important.

- Break Large Evaluation Graph Cycles
> IK system is naturally form a cycle. If possible, use other methods.

- Remove Output Mesh Dependencies
> Make intermediate meshes smaller.

- Remove Head Geometry
> Cutting off Head and blendding back onto body is optimization for single-threaded performance  
> Transfer all head deformers to the body, making it possible to remove head from the rigs entirely.

##### Tool Updates for Parallel Evaluation

- Make Deformers Thread Safe
- Break Up Complex Deformer Nodes
- Convert Python Nodes to C++ Nodes.
- Create A Custom Evaluator for PBCS
- Implement GPU Deformers

