# Week 9

## Dehazing

- Attenuation
- Airlight

Mathematical model
$$\mathbf{I}(x)=\mathbf{J}(x)t(x)+\mathbf{A}(1-t(x))$$
$$t(x)=e^{-\beta d(x)}$$
where $\mathbf{I}(x)$ is the observed radiance at $x$, $\mathbf{A}$ is the airlight.

## Image Resizing

## Super Resolution
 
### Interpolation

It can't ensure all regions can be batter.

### Deep Learning 

- Preprocessing
  - Upscale a low-resolution image to the desired size using bicubic interpolation.
  - Recory $Y$ to true image $X$
- Patch extraction and representation
  - Extract patches from $Y$.
  - Represent patch as high-dimensional vector.
- Reconstruction

Using MSE

### Video Super Resolution

Temporal consistence needed to be considered.