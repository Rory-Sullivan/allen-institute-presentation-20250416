# Presentation

## Introduction
Hi my name is Rory. I'm from Ireland originally, I've been in Seattle just over
2 years now. I did an undergraduate degree in mathematics. This is where I first
started programming. After college I taught myself how to write code. I've now
been working as a software engineer for the last 4 years mostly in full stack
web development. The main languages I've worked with over the years are
TypeScript, C#, Python, SQL, and Rust. My other hobbies include rock climbing
and skiing.

## What is ray tracing?
The first project I am going to be talking about today is a ray tracing engine.
Do you all know what ray tracing is?

Ray tracing is a method for generating images of 3D scenes. It works by sending
out rays from a camera for each pixel on the screen. These rays then bounce off
objects, sometimes multiple times, before eventually ending at a light source
(or not).

As we can see in the diagram some rays scatter off the ball and end in the
light. Other rays scatter off the ground and are blocked from reaching the light
source by the ball. Typically multiple rays are sent per pixel all scattering in
different directions, we average all of these rays to determine  the colour of
each pixel.

Ray tracing is a very computationally intensive compared to other methods of
rendering an image like rasterization. It prioritizes image quality over speed.
Ray tracing is able to produce photorealistic images.

## Rust ray tracer
So onto the ray tracing engine that I built. This was a passion project to build
a ray tracing engine from scratch. It was originally inspired by learning about
the math behind ray tracers in college. Later when I was learning Rust (a new
programming language) I was looking for a good compute intensive project to test
my skills with and ray tracing seemed like a good candidate.

It's based on the 'Ray tracing in one weekend' book series, which takes you
through how to build a simple ray tracing engine from scratch. It's all based on
CPU code so it is not very efficient, but given enough time it can produce some
cool images.

### Show the image
So this is an image produced by my ray tracer. The dragon you see in the middle
is the 'Stanford dragon' which is a common 3D model that is used to test 3D
software. It has about 900,000 triangles.

Here we have a glass ball. Note how it inverts the image that we see through it
and how it focuses the light on the ground.

We can also see a metal ball here which reflects other objects around it. We
also have a moving object over here which exhibits motion blur as we are
simulating a camera shutter.

**Any questions?**

### Bounding volume hierarchy
Something I thought was particularly interesting in this project that I want to
talk about is bounding volume hierarchies, which is a performance optimization
that is applied to our intersection search.

As I mentioned before this dragon has just under 900,000 triangles in it. That
is a lot of triangles to test for an intersection for every ray that we send out
and would take a long time.  So what we do instead it break the triangles into
boxes so that we can test multiple triangles at the same time.

**Move to BVH slide**

Here we can see how this is done. We enclose all of our objects in a box. We can
then easily test if a our ray intersects with the box, if it doesn't then we
know it does not intersect with any of the objects in the box. If it does then
we keep going. We divide the objects in the box into two smaller boxes and test
for intersection with each of those boxes and so on. This gives us the tree like
structure that you can see here.

In this case we have 6 objects, now instead of testing all 6 objects for an
intersection we only have to do at most 4 intersection tests. In the case of our
dragon instead of 900,000 tests we only have to do at most 21. This scales very
well with larger triangle counts.
