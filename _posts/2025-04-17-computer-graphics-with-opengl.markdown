---
layout: post
title: "Computer Graphics with OpenGL"
date: 2025-04-17 00:00:00 +0800
categories: ["Course Notes"] 
tags: ["Programming", "C++", "OpenGL", "Computer Graphics"]
---

This is my personal notes for Computer Graphics with OpenGL course. The materials are compiled from several resources. 


## Chapters Overview {#chapters}
1. Intro to Computer Graphics  
2. OpenGL Graphics Pipeline
<!-- 2. Basic Theory: CG Rendering Pipeline, Drawing basics, Primitives, Vector & Matrices (Algebra),   
3. Primitives: Coordinate System, Primitives, Vertices, Indexed Vertices, Pixels, Fragments   
4. Pipeline 1 - Vertex Processing: Homogeneous Coordinates, Transformation (Translation, Scale, Rotation), View, Projection   
5. Pipeline 2 - Rasterization Processing: Viewport, Culling  
6. Pipeline 3 - Fragment Processing   
7. Pipeline 4 - Output merging: Z-Buffer, Alpha-Blending, Lighting   
8. Advance - Shaders: Vertex, Fragment, GLSL    
9. Advance - Texture -->

### References: 
1. Theory: https://www3.ntu.edu.sg/home/ehchua/programming/opengl/CG_BasicsTheory.html#zz-2. 
2. Practical: https://learnopengl.com/Introduction 
3. Practical: https://ogldev.org/instructions.html 
4. GLFW: https://www.opengl-tutorial.org/beginners-tutorials/

--- 

## 1. Computer Graphics  {#chapter1}
Computer Graphics (CG) is a branch of Computer Science (CS) (and also the products: video games, multimedia apps) that explores the creation of 2D and 3D graphics. It involves the process of creation, manipulation, and rendering of the visual objects using computer to the screen.  
* How? The system take graphical objectss (points, etc) and feed it to CPU where it will communicate the data flow from RAM to the graphics system. The graphics system which contains GPU and graphics memory (VRAM and buffers), will process the graphical operations. Finally, the Graphics subsystem (either GPU or buffers) may directly render the CG to the display.  

<center><img src="/images/cgoverview.png" title="Overview" alt="Overview"/> <br>Computer Graphic Overview. <br>Ref: 
https://www3.ntu.edu.sg/home/ehchua/programming/opengl/CG_BasicsTheory.html</center>  

<br>  

### OpenGL  

OpenGL (Open Graphics Library) is a cross platform and open-source API for 2D and 3D graphics rendering, using c++. It commonly useed in multimedia applications such as video games, CAD (computer-aided design), and scientific visualization apps. It utilizes GPU for hardware-accelerated rendering. How? It provides functions that send instructions to GPU how to render shapes, apply textures, and manipulate many things.  

The OpenGL rendering pipeline is a sequence of steps that process and transform data (like vertices and textures) to generate the final image on screen. It has several stages, which can be programmable (like shaders) or fixed-function.

<center><img src="/images/cgpipeline.png" width="400" title="OpenGL Pipeline" alt="OpenGL Pipeline"/> <br>OpenGL Pipeline. <br>This illustration is inspired by https://www3.ntu.edu.sg/home/ehchua/programming/opengl/CG_BasicsTheory.html and  https://learnopengl.com/Getting-started/Hello-Triangle. </center>  

The basic process is originally this:  
1. Vertex Processing   
2. Rasterization   
3. Fragment Processing   
4. Pixel Processing   

Then, the modern OpenGL is developed to be this: 
1. Vertex Processing  
   a. Vertex Specification (programmable - mandatory)  
   b. Vertex Shader (programmable - mandatory)   
2. Primitive Processing  
   a. Tessellation Shader (programmable - optional)    
   b. Geometry Shader (programmable - optional)   
3. Fragment Processing 
   a. Rasterization (fixed)
   b. Fragment Shader (programmable - mandatory)
4. Per-Sample (Pixel) Operations (fixed)  
   (HSR, Blending, Depth Test, etc.)

Most common OpenGL library:  
| Category | Library |  
| --- | --- |  
| C++ | Programming language. It can be compiled into the native machine. |  
| GLFW | Windowing management. |  
| GLEW or GLAD | Extension library. |  
| GLM | Math library. |  
| SOIL2 | Texture management. |  

---

## 2. OpenGL Graphics Pipeline  

### 1. Vertex Processing  
####   a. Vertex Specification (programmable - mandatory)  
####   b. Vertex Shader (programmable - mandatory)   
### 2. Primitive Processing  
####   a. Tessellation Shader (programmable - optional)    
####   b. Geometry Shader (programmable - optional)   
### 3. Fragment Processing 
####   a. Rasterization (fixed)
####   b. Fragment Shader (programmable - mandatory)
### 4. Per-Sample (Pixel) Operations (fixed)  
####   (HSR, Blending, Depth Test, etc.)

