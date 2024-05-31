# Week 3 - Digital Image Processing


- Gray Image Processing - Spatial, Frequency, Geometry
- Color Image Processing - Fundatmentals, Models, Processing
- HDRI(High Dynamic Range Image) - Introduction, Acquisition, Tone Mapping

## Spatial Domain Image Processing

The processes can be denoted as:
$$ g(x,y) = T[f(x,y)]$$
where $f(x,y)$ is the input image, $g(x,y)$ is the output image. $T$ is the operator. When we only consizer current pixel, we can rewrite as:
$$s=T(r)$$

### Image Enhancement

- Contrast stretching
- Histogram equalization
- Noise smoothing
- Filtering

#### Linear Transformation - Image Negatives

- Reverse the order of pixel intensities.
- Useful when the black areas are dominant in size.

$$s=L-1-r$$
where $L-1$ is the largest gray level.

#### Log Transformation

- Map a narrow range of low gray-level values in the input image to a wider range of output levels or reverse.
- Suitable when only the brightest parts of the image are visible on the display.
$$s = c\mathrm{log}(1+lrl)$$

#### Power-Law Transformation

- Map a narrow range of dark input values into a wider range of output values.
- We can have different transformation by using different $\gamma$.

$$s=cr^\gamma$$
when $\gamma$ less than 1, the image becomes lighter, otherwise, it becomes dacker.

### Piecewise-Linear Transformation


#### Contrast Stretching

Low contrast images lack of dynamic range in the image sensor. 

$$(r_1,s_1)=(r_{min},0)\\(r_2,s_2)=(r_{max},L-1)$$

### Histogram

$$h(r_k) = n_k$$
where $r_k$ is the $k$-th gray level and $n_k$ is the numberof pixels in the image having gray level $r_k$. 

#### Histogram Equalization

Increase the contrast by stretching its histogram to  approximately uniformly distributed.
$$s_k = T(r_k)=\sum_{j=0}^k \frac{n_j}{n}$$
where $s_k$ records the amount of the pixels lower than $k$. $s \in [0,1]$ we need to transfer it to $ss \in [0, \text{Max-grey-level-value}]$.

By doing this, we keep the distribution, whereas contrast stretching will distrot the distribution.

### Spatial Filtering

Considering the neighboring pixels.

#### Smoothing

we can use average filter:
$$\frac{1}{9}*
\begin{bmatrix}
    1 & 1 & 1 \\
    1 & 1 & 1 \\
    1 & 1 & 1 \\
\end{bmatrix}$$
or weighted average filter:
$$\frac{1}{16}*
\begin{bmatrix}
    1 & 2 & 1 \\
    2 & 4 & 2 \\
    1 & 2 & 1 \\
\end{bmatrix}$$

#### Sharpening

Detect the edges and then add to the original image.

Use to calculate the  derivative:
$$
\begin{bmatrix}
    0 & 1 & 0 \\
    1 & -4 & 1 \\
    0 & 1 & 0 \\
\end{bmatrix}$$
or second order derivative:
$$
\begin{bmatrix}
    1 & 1 & 1 \\
    1 & -8 & 1 \\
    1 & 1 & 1 \\
\end{bmatrix}$$

#### Edge Detection

We can also calculate the second order derivative.

Canny
- Noise reduction
- Finding intensity gradient of the image
- Non-maximum suppression
  - Make the edge as thin as possible
- Hysteries thresholding
  - Two thresholde, if the point in between is connect to the point larger than max threshold, it should be regarded as a edge otherwidth it's not a edge point.
  - If the point is larger than max threshold, it's a edge point.
  - If the point is less than min threshold, it should not ne regarded as a edge point no matter whether it is connect to the points larger than msx threshold.

## Frequency Domain Image Processing

The image can be regarded as a wave. We can use Fourier Transformation to convert image to frequency domain.
$$F(\omega) = \int_{-\infty}^{\infty}f(x)\mathrm{exp}(-2j\pi\omega x)dx$$
where $x$ is the spatial information, $\omega$ is the frequency.

### Image Smoothing - Ideal Low Pass Filter (ILPF)

Keep low frequencies and cut off large frequencies (usually is noise information).
$$H(u,v) = \begin{cases}
    1 \quad \text{if} \quad D(u,v)\le D_0\\
    0 \quad \text{if} \quad D(u,v)> D_0
\end{cases}$$ 
where $D(u,v)$ is the distance between a point $(u,v)$ and the center of the frequency rectangle.
$$D(u,v) = [(u-P/2)^2(v-Q/2)^2]^{1/2}$$

### Geometric Transform