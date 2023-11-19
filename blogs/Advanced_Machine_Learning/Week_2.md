# Week 2 - Loss Functions and Convex Optimization

## Loss Function
0-1 loss function is not convex or smooth, hard to optimize.

Convex objective has only one minimum. The convexity makes optimisation 
easier than the general case since local minimum must be a global minimum.


Surrogate loss functions:
- Hinge loss
  - Linear SVM
- Logistic loss
- Least square loss
- Exponential loss
- Cauchy loss (not convex)
- Correntropy loss (not convex)

Not convex surrogate loss function may have good approximation.

Let
$$\phi(Yh(x))=l(X,Y,h)$$
if $\phi$ is convex and if $\phi$ is differentiable at 0, and 
$$\phi'(0)<0$$
the loss function si classification-calibrated.

If the traning data is sufficiently large, the sorrogate loss function will result in the same classifier as the 0-1 loss functrion.

$$h_s=\underset{h}{\operatorname{\argmin}}\frac{1}{n}\sum_{i=1}^n l(X_i,Y_i,h)$$
$$h_c=\underset{h}{\operatorname{\argmin}}\frac{1}{n}\mathbb{E}[1_{Y \neq sign(h(x))}]$$
$$\mathbb{E}[1_{Y \neq sign(h_s(x))}] \stackrel{n\rightarrow \infin}{\longrightarrow} \mathbb{E}[1_{Y \neq sign(h_c(x))}]$$

## Convex Optimization


### Convex Functions
Two properities:
- Derivative exist every points
- Convex combination above the function

If Hessian matrix exist at each point in the domain of $f$, $f$ is twice differentiable. The $f$ is convex if and only if Hessian matrix is positive semidefinite for all point in the domain.

A square matrix $H\in \mathbb{R}^{d \times d}$ is positive semidefinite if and only if:
$$\forall x \in \mathbb{R}^d, x^THx\ge0$$

We can calculate the minimum of the convex functions.

A point $x$ is optimal for $f$ if and only if it is feasible and 
$$\nabla f(x)^T(y-x)\ge0$$
where $\nabla f(x)^T$ is gradient and $(y-x)$ is the direction.

## Gradient Descent Method

### Taylor's Theorem


