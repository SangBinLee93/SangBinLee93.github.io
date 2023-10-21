---
title : "[Study][Tip] Optimizing a rig file"
categories:
  - RIG
  - study
tages:
  - maya
---

[original document]  
https://disneyanimation.com/publications/?drawer=/publications/optimizing-rig-manipulation-with-gpu-and-parallel-evaluation/  


##Key Concept
- Optimize rig for Parallel evaluation, multi-thread.
- Use multi/smaller nodes rather than fewer/heavy nodes

<br/>

##### Rig Opimizations

- Create Unique Deformer Chains
> ( OK )
ShapeOrig → Deformer → Shape

> ( NO!! )
ShapeOrig → Deformer → Multiple Shapes


- Optimize Mesh Size
> split meshes per 1000 to 2000 points
>> and comebine the cut-up meshes to a single mesh with a custom parallel blending node.

- Break Large Evaluation Graph Cycles
> IK system system naturally form a cycle. If possible, use other methods.
- Remove Output Mesh Dependencies
> Make intermediate meshes smaller.
- Remove Head Geometry
> Cutting off Head and blendding back onto body is optimization for single-threaded performance
>> Transfer all head deformers to the body, making it possible to remove head from the rigs entirely.

##### Tool Updates for Parallel Evaluation

- Make Deformers Thread Safe
- Break Up Complex Deformer Nodes
- Convert Python Nodes to C++ Nodes.
- Create A Custom Evaluator for PBCS
- Implement GPU Deformers

