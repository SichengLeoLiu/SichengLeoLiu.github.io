# Week 8 - Graphics and Animation

## Computer Graphics

Model $\rightarrow$ Rendering (Transform, Lighting, Clip Rasterize) $\rightarrow$ Display 

### Transforation

Rotation:
$$\begin{bmatrix}
    \cos(\theta) & -\sin(\theta) & 0 \\
    \sin(\theta) & \cos(\theta) & 0 \\
    0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
    x\\y\\0 \text{ or } 1
\end{bmatrix}=
\begin{bmatrix}
    x' \\ y'\\ 0 \text{ or }1
\end{bmatrix}$$

Translation:
$$\begin{bmatrix}
    1 & 0 & \Delta x \\
    0 & 1 & \Delta y \\
    0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
    x\\y\\ 1
\end{bmatrix}=
\begin{bmatrix}
    x+\Delta x \\ y+ \Delta y\\ 1
\end{bmatrix}$$

## 3D Modeling

### Modeling with Mesh

### Particle System

## 3D Rendering

Colour
  

### Flat Rendering

The colour in one mesh is same. Not smooth. 

### Gouraud Rendering

Linear combination.

### Phong Rendering

Consider the material.

### Ray Tracing

$$I = I_{local} + K_r*I_{reflected}+K_t*I_{transmitted}$$


## Texture Mapping

## Animation
