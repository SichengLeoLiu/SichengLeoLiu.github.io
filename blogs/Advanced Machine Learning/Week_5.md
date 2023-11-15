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