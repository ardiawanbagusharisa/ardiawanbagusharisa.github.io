---
layout: post
title: "Computer Graphics with OpenGL"
date: 2025-04-17 00:00:00 +0800
categories: ["Course Notes"] 
tags: ["Programming", "C++", "OpenGL", "Computer Graphics"]
---

This is my personal notes for Computer Graphics with OpenGL course. The materials are compiled from several resources. 

# Computer Graphics  
Computer Graphics (CG) is a branch of Computer Science (CS) (and also the products: video games, multimedia apps) that explores the creation of 2D and 3D graphics. It involves the process of creation, manipulation, and rendering of the visual objects using computer to the screen.  
* How? The system take graphical objectss (points, etc) and feed it to CPU where it will communicate the data flow from RAM to the graphics system. The graphics system which contains GPU and graphics memory (VRAM and buffers), will process the graphical operations. Finally, the Graphics subsystem (either GPU or buffers) may directly render the CG to the display.  

Input (graphical objects) -> CPU [<-> Memory (RAM, External), -> Graphics System (GPU, VRAM & Buffer) -> Display]  

[show figure CG process overview: https://www3.ntu.edu.sg/home/ehchua/programming/opengl/images/Graphics3D_Hardware.png https://www3.ntu.edu.sg/home/ehchua/programming/opengl/CG_BasicsTheory.html]  

## OpenGL 
OpenGL (Open Graphics Library) is a cross platform and open-source API for 2D and 3D graphics rendering, using c++. It commonly useed in multimedia applications such as video games, CAD (computer-aided design), and scientific visualization apps. It utilizes GPU for hardware-accelerated rendering. 
* How? It provides functions that send instructions to GPU how to render shapes, apply textures, and manipulate many things.  

[show figure OpenGL pipeline: https://learnopengl.com/img/getting-started/pipeline.png https://www3.ntu.edu.sg/home/ehchua/programming/opengl/images/Graphics3D_Pipe.png] 

The OpenGL rendering pipeline is a sequence of steps that process and transform data (like vertices and textures) to generate the final image on screen. It has several stages, which can be programmable (like shaders) or fixed-function.

OpenGL Pipeline:   
1. Vertex Specification 
2. Vertex Shader (1)
3. Tessellation (optional) (2)
4. Geometry Shader (optional) (3)
5. Rasterization (4)
6. Fragment Shader (5)
7. Per-Sample Operations (Blending, Depth Test, etc.) (6 Pixel process)

---

## Chapters Overview  
[Todo https://www3.ntu.edu.sg/home/ehchua/programming/opengl/CG_BasicsTheory.html#zz-2. ]  
Then, I will outline my notes as follows;  
1. Intro to Computer Graphics: Overview, CG Components  
2. Basic Theory: CG Rendering Pipeline, Drawing basics, Primitives, Vector & Matrices (Algebra),   
3. Primitives: Coordinate System, Primitives, Vertices, Indexed Vertices, Pixels, Fragments   
4. Pipeline 1 - Vertex Processing: Homogeneous Coordinates, Transformation (Translation, Scale, Rotation), View, Projection   
5. Pipeline 2 - Rasterization Processing: Viewport, Culling  
6. Pipeline 3 - Fragment Processing   
7. Pipeline 4 - Output merging: Z-Buffer, Alpha-Blending, Lighting   
8. Advance - Shaders: Vertex, Fragment, GLSL    
9. Advance - Texture  

A template for code: 
{% highlight cpp%}
 // Some c++ code go here. 
{% endhighlight %}

### References: 
1. Theory: https://www3.ntu.edu.sg/home/ehchua/programming/opengl/CG_BasicsTheory.html#zz-2. 
2. Practical: https://learnopengl.com/Introduction 
3. Practical: https://ogldev.org/instructions.html 
4. Using GLFW: https://www.opengl-tutorial.org/beginners-tutorials/