# Week 5 - Dictionary Learning and Non-Negative Matrix Factorisation

> Dictionary: $D$
>
> New representation of input data (sparse): $\alpha$

## Dictionary Learning
Let $x \in \mathbb{R}^d$, $D \in \mathbb{R}^{d \times k}$, we have:
$$\alpha^* = \underset{\alpha \in \mathbb{R}^k}{\operatorname{\argmin}}||x - D \alpha||^2$$
where $k$ is much smaller than $d$. $(x - D \alpha)$ is the reconstruction error. For all samples:
$$\underset{D \in \mathcal{D}, R \in \mathcal{R}}{\operatorname{\argmin}}||X-DR||_F^2$$
where $X = [x_1,x_2,...,x_n] \in \mathbb{R}^{d \times n}$ and $R = [\alpha_1,\alpha_2,...,\alpha_n] \in \mathbb{R}^{k \times n}$.

We want to find the optimal $\mathcal{D}$ and $\mathcal{R}$ that minimises the resconstruction error.

### Singular Value Decomposition (SVD)


### PCA
Columns of $D$ are orthonormal to each other, which means there are less common elements in $D$. Therefore, it may have less information loss.

### K-means

$R$ is a one-hot vector. Therefore, whole faces information should be used as dictionary $D$ for restruction.

## Non-negative Matrix Factorisation

Data is often nonnegative by nature.
- Image intensities
- Movie ratings
- Document-term counts

$$\underset{D \in \mathcal{D}, R \in \mathcal{R}}{\operatorname{\argmin}}||X-DR||_F^2 \\ \text{s.t.} \mathcal{D}=\mathbb{R}_+^{d \times k}, \mathcal{R}=R_+^{k \times n}$$

### Optimization
**Multiplicative Update Rules (MUR).** Since updating $D$ and $R$ simutaneously is non-convex, we update them respectively.

Fix $D^k$, solve for $R^{k+1}$:
$$ \frac{\partial ||X-DR||^2_F}{\partial R} = -2D^T X + 2D^T D R$$

$$R_{i,j}^{k+1} = R_{i,j}^{k} + \frac{\eta_{i,j}}{2} ({2D^k}^T X + 2{D^k}^T D^k R^k)_{i,j}$$

$$ \eta_{i,j} = \frac{R_{i,j}^{k}}{ { (D^k}^T D^k R^k)_{i,j}} $$

Therefore, 
$$ R_{i,j}^{k+1} = R_{i,j}^k \frac{({D^k}^T X)_{i,j}}{({D^k}^T D^k R^k)_{i,j}} $$

Similarly,

$$ D_{i,j}^{k+1} = D_{i,j}^k \frac{(X {R^{k+1}}^T)_{i,j}}{(D^k R^{k+1} {R^{k+1}}^T)_{i,j}} $$

