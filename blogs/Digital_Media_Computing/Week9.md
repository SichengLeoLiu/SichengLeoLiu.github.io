# Week 9

## Dehazing

- Attenuation
- Airlight

Scattering model
$$\mathbf{I}(x)=\mathbf{J}(x)t(x)+\mathbf{A}(1-t(x))$$
$$t(x)=e^{-\beta d(x)}$$
where $\mathbf{I}(x)$ is the observed radiance at $x$, $\mathbf{A}$ is the airlight.

The goal is recover $\mathbf{J}(x)$ from $\mathbf{I}(x)$. We need to figure what is $t(x)$ and $\mathbf{A}$.

**Input**:
- Multiple images
- One image + depth-map
- Single image

### Single Image based Dehazing

#### Dark Channel Prior

- A portion of the scene is dominated by airlight.
- The minmum intensity is such a patch should have a very low value.

Steps:
$$\mathrm{min}(r,b,g)$$
$$\mathrm{min}(\text{local patch})$$

For outdoor haze-free images, $\mathrm{min}_\Omega(\mathrm{min}_c J^c)\rightarrow 0$.



## Seam Carving

- Remove unimportant pixels
- Preserve rectangular shape.

Identify low energy pixels:

$$e_1(\mathbf{I})=|\frac{\partial}{\partial x}\mathbf{I}||\frac{\partial}{\partial y}\mathbf{I}|$$
where $\mathbf{I}$ is an image.

The certical seam:
$$\mathbf{s^x}=\{s_i^x\}_{i=1}^n=\{(x(i),i)\}_{i=1}^n,\quad \text{s.t. } \forall i, |x(i)-x(i-1)|\le1$$

Energy function:
$$E[x,y]=|I_x|+|I_y|$$

$$E(S)=\sum_{(x,y)\in S}E[x,y]$$



## Super Resolution
 
### Interpolation

Image content is diverse, it can't ensure all regions can be batter.

#### Linear Interpolation
$$f(x)=\sum_{i=0}^l a_ix$$

#### Cubic Interpoltion




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