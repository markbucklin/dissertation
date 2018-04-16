---
author: "Mark Bucklin"
title: "Development & Application of a Closed-Loop Continuous Optical Neural Interface"
date: "April 13, 2017"
---

# Development & Application of a Closed-Loop Continuous Optical Neural Interface 

## Procedures for real-time image processing,n eural signal extraction, and application to closed-loop control using wide-field Ca2+ fluorescence with awake behaving animals 

April 13, 2017 

Mark Bucklin

---

## Wide-field Fluorescence
* Virus -> sensor expression
* LED -> sensor excitation 
  * (~470nm +/-15) + excitation filter + dichroic mirror
* sCMOS Camera

* “Virtual-Reality”
  * In reality -> simply more stable (and fun for mouse)

---

## Outline
1. Background
2. Image Processing
3. Effective and Efficient Code
4. Streaming

---


# Background #			
---									
## Background
* Microscopy and Functional Imaging
* Image Processing
* "Big Data"

---
      
## Microscopy and Functional Imaging
Two core innovations in available technology
1. Synthetic bio (i.e. GCaMP)
2. Cameras
  * scientific CMOS
  * inexpensive "machine vision" cameras

---
      
## Image Processing
1. Computing Power and Connectivity
  * Remote Clusters (AWS)
  * Graphics Processing Units (NVIDIA GTX)
  * Embedded Units (NVIDIA Tegra X2)
2. Well developed libraries
  * ImageJ (so so)
  * OpenCV (uses OpenCL)
  * GStreamer (much better)
  * OpenGL -> Shader Language extensions (GLSL, HLSL)
  * CUDA (the best)						

---
      
## "Big Data"
* not exactly...
* disparate simple queries across massive databases
* but can be applied

---
      
## Map-Reduce -> Dataflow Processing
  * Actors model
  * Petri Nets
  * **Graph** Processing
  * i.e. Tensorflow

---

## Image Processing
* Motion Correction
* Image Enhancement
* Feature Extraction

---
      
## Motion Correction
  Two approaches to find displacement
  1. Spatialy Homogeneous 
  * phase correlation, aka normalized cross correlation
  2. Feature Matching
    * Detect features (i.e. corners)
    * Triangulate best match

---
      
## Image Enhancement
  1. Contrast
    * Linear Scaling
    * Lookup Tables
  2. Spatial and Temporal Filtering
  3. "Feature" images
    * Gradients
    * Surface Curvature								

---
          
## Feature Extraction
1. "Feature" images (temporally independent)
* Gradients
* Surface Curvature							
2. Long Term Memory
* Statistics changes (single pixel)
* Mutual information changes (inter-pixel)
    
---


# Efficient Code #			
          
## EfficientCode
* Scalable
* Reusable
** Make it MODULAR **

---