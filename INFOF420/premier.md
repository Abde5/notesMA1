# Practical information
Prof: Stefan Langerman

INFO-F-420: Computational Geometry

Webpage: http://homepages.ulb.ac.be/~slanger/cg/

## Reference Books
- (Main) Computational Geometry 2nd Edition (M. de Berg)
- Computational Geometry: An introduction (Franco P. Preparata)
- Computational Geometry in C (Joseph O'Rourke)

## Expected work
Programming assignment every course ! (little 1-2 hours)

At the end of course real project with a scientific paper (do something with the
  knowledge in the paper).

NO EXAM. (10% homework, 50% project, 40% presentation).
# Introduction
## What is computational Geometry
Computational = compute, geometry = Geometry

How to solve problems related in geometry in real life with the power of computers.

In the 80s computer graphics began, and they were used algorithms very poor designed
because those algorithms were designed to resolve them by hand.

## Objects to use:
  - Points
  - Lines
  - Segments
  - Planes (3D)
  - Vectors
  - ...

## RAM Model

The RAM model is different from the Turing Machine, precisely because of the Random Access Memory instead of the tape used in the TMs, so we don't have to move the tape to the Memory Adress to write on it.

In the memory we store numbers (integers), and we can have a problem because in geometry we don't use only Integers, but the objects described before. Also the calculus needed for geometry problems are not suitable for the RAM model, like square roots, etc...

Then we'll invent a new machine able to resolve these problems

## Ruler & Compass Model

The Ruler&Compass is a computer model where we can use operations with circles, points and lines. Between 2 points we can construct a line, and put a compass to draw a circle. We can also find intersections between circles and lines, and between 2 lines, and between 2 circles.

Some problems we cannot solve with this model:
- Squaring the circle $\to$ find a square from a circle with the same area as this circle.
- Trisecting an angle $\to$ divide an angle in 3 equal parts
- Duplication of the cube $\to$ create a cube from another cube double the *volume*

These problems come from the Galois Theory.

## Real-RAM Model

It's a RAM Model where in each placement of the Memory you can store a *real number*. It's useful to design algorithms, but in computers this will not work.

The Real-RAM uses just 4 operators: $+, -, *, /$.

Is this machine able to do everything the R&C and RAM can do? Let's see:

(SEE NOTES ON NOTEBOOK)

- Scalar Product
  We can compute this like $\dot x . \dot y = u_x v_x + u_y v_y$ instead of cosine, so this is good for us, also if we need the sinus we can use the cosinus to compute it with the formula $\sin^2x + \cos^2x = 1$.

- Cross Product:
  We can calculate with the determinant method. The cross product is also the area of the zone created by the 2 vectors.

## Right-turn Left-turn determinant (Homework)

If we have 3 points abc and we have segments lacing these 3 points $abc$, how to know when this structure "turns left" or "turns right". We have to find the angle at b, and to find that the sinus changes to positive or negative because of the direction.

We then can apply the cross product (because it uses the sinus) and determine if it's positive or negative, without having to calculate any trigonometry.

## Convexity

**DEFINITION:** A set $S \subseteq \mathbb{R}$ is convex if $\forall a,v \in S$ $[a,b]\subseteq S$

**DEFINITION:** A segment $[a,b] = \{\lambda a+(1-\lambda)b : 0 \leq \lambda \leq 1\}$ (this is a convex combination).

## Convex Hull

**DEFINITION:** The convex hull is the smalles convex set $C$ s.t. $S\subseteq C$.
