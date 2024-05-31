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
\end{bmatrix}

$$