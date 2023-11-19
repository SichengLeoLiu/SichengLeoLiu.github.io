# Week 8 - Domain Adaptation and Transfer Learning

## Transfer Learning

The data in source domain: $\{(x_1^S,y_1^S),...,(x_{n_S}^S,y_{n_S}^S)\}$.
The data in target domain: $\{(x_1^T,y_1^T),...,(x_{n_S}^T,y_{n_S}^T)\}$.

### Importance Reweighting
The expected risk in source domain is:
$$R^S(h)=\mathbb{E}_{(X,Y)\sim p_s(X,Y)}[l(X,Y,h)]$$

Similary, the expected risk in target domain is:
$$R^T(h)=\mathbb{E}_{(X,Y)\sim p_t(X,Y)}[l(X,Y,h)]\\\\
=\int_{(X,Y)}l(X,Y,h)p_t(X,Y)dXdY\\\\
=\int_{(X,Y)}l(X,Y,h)\frac{p_t(X,Y)}{p_s(X,Y)}p_s(X,Y)dXdY\\\\
=\mathbb{E}_{(X,Y)\sim p_s(X,Y)}[\frac{p_t(X,Y)}{p_s(X,Y)}l(X,Y,h)]\\\\
=\mathbb{E}_{(X,Y)\sim p_s(X,Y)}[\beta (X,Y)l(X,Y,h)]$$

where $\beta(X,Y)=\frac{p_t(X,Y)}{p_s(X,Y)}$ represent the changes across domains. If we know the value of $\beta(X,Y)$, we can use source domain data to approximate the expected risk for target domain.

## Domain Adaptation
In machine learning, a specific domain can be regarded as a specific joint distribution $p(X,Y)$.

### Kernel Mean Matching
Kernel function can capture the similarity of two vectors.

A freature mapping function $\phi$:
$$\phi:X\rightarrow \mathcal{H}$$
where $\mathcal{H}$ is a Reproducing Kernel Hilbert Space (RKHS).

The kernel function:
$$K(x_1,x_2)=\langle \phi(x_1),\phi(x_2) \rang$$
where $x_1$ and $x_2$ are two vectors. If they represent two distributions, we can use the kernel function to measure the similarity of two distributions.

Let
$$\mu(p(X))=\mathbb{E}_{X \sim p(X)}[\phi(X)]$$
where $p(X)$ is a marginal distribution (only focus on the distribution of $X$) on the ferature space $X$.

The expectation $\mu$ is a bijective function (if $\mu(x_1)=\mu(x_2)$, $x_1=x_2$) if $K$ is a universal kernel.

Then we have:
$$\mu(p_t(X))=\mathbb{E}_{X\sim p_s}[\beta(X)\phi(X)]=\mu(\beta(X)p_s(X))\\\\
s.t. \beta(X)\ge 0,\mathbb{E}_{X\sim p_s}[\beta(X)]=1$$
where $\mathbb{E}_{X\sim p_s}[\beta(X)]=1$ means we have enough features.

We want to minimize the difference between expection on target domain and source domain.
$$\underset{\beta}{\operatorname{\min}}||\mu(p_t(X))-\mathbb{E}_{X \sim p_s(X)}[\beta(X)\phi(X)]||^2 \\\\
s.t. \beta(X)\ge 0,\mathbb{E}_{X\sim p_s}[\beta(X)]=1$$
Note, we can get $\beta(X)$ here!

As we can't calculate the expection risk, we can calculate empirical risk instead.

## Transfer Learning Models

### Covariate Shift Model
We assume that $p_t(Y|X)=p_s(Y|X)$ and that $p_t(X) \neq p_s(X)$

Then
$$\beta(X,Y)=\frac{p_t(X,Y)}{p_s(X,Y)}=\frac{p_t(Y|X)p_t(X)}{p_s(Y|X)p_s(X)}=\frac{p_t(X)}{p_s(X)}=\beta(X)$$

$\beta(X)$ can be learned by kernel mean matching.

### Target Shift Model
We assume that $p_t(Y|X)=p_s(Y|X)$ and that $p_t(Y) \neq p_s(Y)$, which means the labeling distribution is different.

Then
$$\beta(X,Y)=\frac{p_t(X,Y)}{p_s(X,Y)}=\frac{p_t(X|Y)p_t(Y)}{p_s(X|Y)p_s(Y)}=\frac{p_t(Y)}{p_s(Y)}=\beta(Y)$$

However, most of time we don't know the label distribution on the target domain.


