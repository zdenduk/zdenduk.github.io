---
layout: post
title: "Driver data"
subtitle: "Comparing driver data based on G-G-V diagrams"
background: '/img/posts/DriverData/header.JPG'
tags: "Matlab"
---
## Background

This application is the result of my homework topic in the CTU Matlab course used for the CTU Formula Student team eForce.

### Installation & Setup

Run the driver_graph.m in Matlab.

### Application overview

Knowing how much more performance you could have produced in racing is an incredibly challenging task. But the truth is that maximizing performance is the whole point!

This application aims to let people compare their driving data and enable them to extract more performance.

### How does it work?

First, the lateral, longitudinal and speed data are combined, producing the G-G-V diagram. Then a minimum convex hull is constructed, using Matlab native function delaunayTriangulation. The user can then slice this hull at any speed, essentially producing a G-G diagram at that speed. This is calculated via the sliceDelaunay function, available [here](https://www.mathworks.com/matlabcentral/fileexchange/56536-slicedelaunay).

## [GitHub link](https://github.com/zdenduk/DriverData)

