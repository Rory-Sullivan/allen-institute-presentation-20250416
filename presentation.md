# Presentation

## Introduction
Hi my name is Rory. I'm from Ireland, I've been in Seattle just over 2 years
now. I did an undergraduate degree in mathematics. That's where I first dabbled
in programming. After college I taught myself how to code more seriously. I've
now been working as a software engineer for the last 4 years, mostly in full
stack web development. The main languages I've worked with are TypeScript, C#,
Python, SQL, and Rust. My other hobbies include rock climbing and skiing.

## Abbey Capital
My last job was at a company called Abbey Capital. They are a financial fund
manager, while I was there I built and maintained internal tooling for the
company.

## Atlas
The main project I worked on at Abbey was called Atlas. Which was a full
re-build of their internal fund accounting application. It was a web application
built with a TypeScript React frontend, C# ASP.NET on the backend, and a
MySQL database. All running on AWS.

I was part of a small team working on this project, there were just two of us
initially so I was deeply involved with many different aspects of the project.

The project was split into five main parts:
- **Specification:** We spent several months working with users, creating the
  specification for the project. This was largely based on the old version of
  the application with a bunch of new features. We used a tool called Balsamiq to
  create visual mock-ups and aid in the design process.
- **Design:** We researched different options and decided what architecture and
  technologies we were going to use. One of big criteria was to give the
  application a "real-time" feel to it. So when you make a change to a data
  point in one place it automatically propagates those changes to derived data
  and other users.
- **Build:** Then we started actually building the application. Once we started
  building user interfaces we started doing user testing. This allowed us to use
  an iterative design process and build what our users wanted.
- **Parallel testing:** After the main features were built we entered a period
  of parallel testing. During this time we were validating our calculations
  against the old system. We also started with full scale user testing. Of
  course this led to many bug fixes and some minor changes.
- **Production:** Finally after we were satisfied with our system we turn off
  the old system and Atlas took over.

### My contributions:
The main things I contributed to this project are:
- I setup the continuous integration/continuous deployment pipeline
- I setup the C# and React projects and integrated them so they would work
  together
- I built the event system that automatically propagated data changes
- I built the real-time system that kept the frontend up to date using web
  sockets (SignalR)
- I built reusable components for the frontend. Several screens looked very
  similar so these components were used across all of them to keep the user
  experience consistent.

### Results
The Atlas project was a great success.

- We made a 20x performance improvement to the core calculation engine, going
  from over 20mins in the old system to just under 1min
- We had a completely re-designed modern user interface that was much easier to
  work with.
- We now had real-time updates that synchronised across all users. Previously
  they would have to manually trigger the calculations and then wait 20 mins and
  re-fresh their screens
- Most importantly we saved our users time and made their jobs easier

### Why is this relevant??
This project gave me invaluable experience in delivering a technical software
project. I was working with subject experts to deliver them a product they will
use everyday. I believe this experience will translate very well to this role at the Allen Institute.

**Any questions?**

## Rust ray tracer
Next I want to tell you about a 3D graphics project I worked on.

The next project I am going to be talking about today is a ray tracing engine.
This was a passion project to build a ray tracing engine from scratch. I was
originally inspired by learning about the math behind ray tracers in college.
Later when I was learning Rust (a new programming language) I was looking for a
good compute intensive project to test my skills with and ray tracing seemed
like a good candidate.

It's based on the 'Ray tracing in one weekend' book series, which takes you
through how to build a simple ray tracing engine from scratch. It's all based on
CPU code so it is not very fast, but given enough time it can produce some
cool images.

### What is ray tracing?
Ray tracing is a method for generating images of 3D scenes. It works by sending
out rays from a camera for each pixel on the screen. These rays then bounce off
objects, sometimes multiple times, before eventually ending at a light source
(or not).

As we can see in the diagram some rays scatter off the ball and end in the
light. Other rays scatter off the ground and are blocked from reaching the light
source by the ball creating a shadow. Typically multiple rays are sent per pixel
all scattering in different directions, we average all of these rays to
determine  the colour of each pixel.

Ray tracing is a very computationally intensive compared to other methods of
rendering an image like rasterization. It prioritizes image quality over speed.
Ray tracing is able to produce photorealistic images.

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
that is applied to our intersection search. **Improve this wording??**

As I mentioned before this dragon has just under 900,000 triangles in it. That
is a lot of triangles to test for an intersection for every ray that we send out
and would take a long time. So what we do instead is break the triangles into
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

## WebGL project
When I found out about this job I wanted to familiarize myself with WebGL so I
created this project. It is a port of the same scene from my ray tracing engine to the browser using WebGL (three.js). This one we can interact with!

The most challenging thing to get working were the environment maps, these are
what allow the glass ball to be transparent and the metal ball to reflect it's surroundings.

The skills I learnt from my ray tracing project transferred over well to this
and I was able to do it in less than a weekend.

Alternate: I was able to build on the skills I learnt from my ray tracing
project and my knowledge of web development to complete this in just under a
weekend.

## Open source work
I am passionate about open source work, I think it is an opportunity to give
back to the communities that I am a part of as well as a great way to learn new
skills. I want to highlight a couple of projects that I have been involved with.

### Dry Rock
Dry Rock is a personal project I started about 5 years ago. It is a weather
website for rock climbers. It is designed for high information density so that
you can figure out where the best weather to go climbing is with the least
amount of effort. It is also specifically designed to work well on mobile
devices.

I regularly use it along with a few of my friends. The main feedback I've
received about it is simply to add more places. When people just want more of
something I generally take that as a good thing.

The application is built entirely with Python. It renders static HTML pages
which are then hosted on GitHub pages. A job runs periodically to update the
weather data on the site.

Lydia thinks:
- This is why I made Dry Rock
- I use it myself and my friends use it
- I've learnt about the UI from me and friends using it
- The main feedback I get is to add new places

### Avy
I have been volunteering for the Northwest Avalanche Center (NWAC) since
January, helping them maintain their Avy app. The app provides avalanche
forecasts and weather data from various avalanche centers in the US. It is used
by thousands of people for backcountry skiing and other winter activities.

It is built on React Native and targets Android and iOS. I have been working
them to fix bugs mostly to do with their Android app. This was my first time
working on a mobile app, but it's been great getting to dabble in this area.

Lydia thinks:
- This is another thing I care about and I want to contribute to
- Fix bugs that are important to me
- Also just fixing issues

### Notes
Theme: Why is this going to help me in this job!

Why am I interested in graphics.

Working with experts in the field during Atlas (also I was not the end user)
