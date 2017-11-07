# Practical information

TP the Thursdays, Theory the Tuesdays

# Course overview
We'll learn OpenGL (Open Graphics Library). The main subject of the course is Virtual Reality.
## Applications
Virtual Reality can be found in so many applications, like multimedia applications (videogames) or pedagogic applications (surgery simulation).

## Course objective
We'll make a game and we'll do all the rendering just using OpenGL (with mouse and Oculus interaction).

For example, there have been bowling, chess and roller coaster interactive videogames done for the course.

## Real vs Synthetic
We'll see how to render realistic images (not in real time) and compare it to OpenGL.

## Theory vs Practice
 - Theory
    - 50% OpenGL
    - 50% Depth Image-Based Rendering
 - Practice
    - Exercises
    - Report + Presentation

Final score: $\frac{2}{3}$ max(score1,score2) + $\frac{1}{3}$ min(score1,score2)

## Interpolation
In 4D scenes, going through all the cameras give a "bad" effect of non continuosity. This is fixed by interpolation. **IMPORTANT** $\to$ surely for the exam!!!

# Introduction

## Point Clouds
This technique goes faster than the mesh rendering, because we'll just take sufficient points to represent the object we see, without needing a texture.

### Splatting
Technique to "fill the gaps" on point clouds.

## Light Fields
Technique to throw a different image on every possible angle, so when moving, we can see a different image.

These 2 techniques will have a conventional format (MPEG).

**Uncanny Valley Effect**:
When modeling a person in 3D, it has to be perfect, or not realistic at all, but if it's a bad quality realistic model, the empathy of the model will just go down.

Point clouds can be used to represent objects seen from far away, because we'd need not a lot of points to represent the object (like the images of a football game from the spectator point of view).

## 360 Video or 3DoF

**STITCHING:** Adapting multiple images (stretching) to cover a 360º image.

**HOMOGRAPHY:** Taking a texture and adapt its geometry to the surface of a 3D model by doing only translations and rotations.

Book: Computer Vision with Python (O'REILLY)

# OpenGL Pipeline

![pipeline](https://www.ntu.edu.sg/home/ehchua/programming/opengl/images/Graphics3D_Pipe.png)

On 3D we have an object represented by 3D points (a mesh). Some vertices will form triangles and a texture will be applied to this triangle. The triangle wil be rendered from the camera point of view, the triangle will then be projected perpectively in the screen with a FoV.

Then pixel by pixel the triangle will be scanned by the OpenGL driver and colour it looking the texture value of the triangle at that position (*Texel* -> Texture Pixel).

Some important equations:

- Cross product: to the normal of a triangle
- Scalar product: to find a cosine between 2 vectors

Those 2 equations are always used for lightning.

**CLIPPING:** Cutting a polygon that is going over the screen.

**Z-buffering:** When drawing a triangle on screen, take the color of the closest texel on that pixel.

There are other shaders Geometry, Tesselation that are used for geometry modification like the subdivision technique. There are also compute shaders, that are often used for physics calculations.

For the use of shaders, we'll have to *bind* variables in the OpenGL program with the variables in the shaders.

For the projection, OpenGL uses a hyperfocal regime so that every object, whatever the distance, will be on focus. If we want to have this unfocus we'll have to program it ourselves in a shader with the formula $\frac{1}{f} = \frac{1}{a} + \frac{1}{b}$ where $a = \infty$ in hyperfocal regime.

## Lightning

Thanks to normals we can write shaders for the shadows and lightning. OpenGL only supports one bounce lights. We can also use shaders for particles (fire effects, etc...).
