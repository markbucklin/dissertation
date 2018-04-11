
## Outline 

### Background 

### Image Processing 

### Effective and Efficient Code
- Background - Microscopy and Functional Imaging - Image Processing

## Microscopy and Functional Imaging Two core innovations in available
- technology 
      1. Synthetic bio (i.e. GCaMP) 
      2. Cameras 
- scientific CMOS

## Image Processing 1. Computing Power and Connectivity 
- Remote Clusters (AWS) 
- Graphics Processing Units (NVIDIA GTX) 
- Embedded Units (NVIDIA Tegra X2) 2. Well developed libraries 
- ImageJ (so so) 
-
OpenCV (uses OpenCL) 
- GStreamer (much better) 
- OpenGL 
- Shader

## Big Data 
- not exactly\... 
- disparate simple queries across

## Map-Reduce 
- Dataflow Processing 
- Actors model
- Petri Nets 
- Graph Processing 
      - i.e. Tensorflow

## Image Processing 
- Motion Correction 
- Image Enhancement 

## Motion Correction Two approaches to find displacement
###  Spatially Homogeneous phase correlation
- aka normalized cross correlation - Feature Matching 
- Detect features (i.e. corners) 
### Triangulate best

## Image Enhancement 
1. Contrast - Linear Scaling - Lookup Tables 
2. Spatial and Temporal Filtering 
3. Feature images - Gradients

## Feature Extraction 
1. Feature images (temporally independent)

- Gradients - Surface Curvature 2. Long Term Memory - Statistics
      - changes (single pixel) 
- Mutual information changes (inter-pixel)

## EfficientCode 
- Scalable - Reusable - Make it MODULAR 

## Tutorial


### Incremental Update of Statistics
#### central moments
```matlab
      function [m1,m2,m3,m4,fmin,fmax] = updateStatistics(x,m1,m2,m3,m4))
            n = n + 1;
            
            % GET PIXEL SAMPLE
            f = F(rowIdx,colIdx,k);
            
            % PRECOMPUTE & CACHE SOME VALUES FOR SPEED
            d = single(f) - m1;
            dk = d/n;
            dk2 = dk^2;
            s = d*dk*(n-1);
            
            % UPDATE CENTRAL MOMENTS
            m1 = m1 + dk;
            m4 = m4 + s*dk2*(n.^2-3*n+3) + 6*dk2*m2 - 4*dk*m3;
            m3 = m3 + s*dk*(n-2) - 3*dk*m2;
            m2 = m2 + s;
            
            % UPDATE MIN & MAX
            fmin = min(fmin, f);
            fmax = max(fmax, f);
      end
```                        
#### Extract Features
```matlab

      function [dm1,dm2,dm3,dm4] = getStatisticUpdate(x,m1,m2,m3,m4)
            % COMPUTE DIFFERENTIAL UPDATE TO CENTRAL MOMENTS
            dm1 = dk;
            m1 = m1 + dm1;
            dm4 = s*dk2*(n^2-3*n+3) + 6*dk2*m2 - 4*dk*m3;   
            dm3 = s*dk*(n-2) - 3*dk*m2;
            dm2 = s;
            m2 = m2 + dm2;
            % NORMALIZE BY VARIANCE & SAMPLE NUMBER -> CONVERSION TO dVar, dSkew, dKurt   
            dm2 = dm2/max(1,n-1);
            dm3 = dm3*sqrt(max(1,n))/(m2^1.5);
            dm4 = dm4*n/(m2^2);                 
      end
```                        


Simple Processing on GPU
```matlab
      [dm1,dm2,dm3,dm4] = arrayfun(@getStatisticUpdate(x,m1,m2,m3,m4)
      [dm1,dm2,dm3,dm4] = arrayfun(@getStatisticUpdate(rowidx,colidx)
```       



## DataFLow Architectures

### "Globally Asynchronous Locally Synchronous"