# Week 7 - Learning with Noisy Data: On the Robustness of Surrogate Loss Functions

## Probabilistic Perspective of Noise

> Target: $y=h(x)+\epsilon$
> 
> Noise: $\epsilon \sim \mathcal{N}(0, \beta^{-1})$
> 
> What we learn: $y|x \sim \mathcal{N}(h(x), \beta^{-1})$ (We want it have high probability.)

### Bayes' Rule
$$p(\theta|S)=\frac{p(S|\theta)p(\theta)}{p(S)}$$
where $S$ is training sample, $\theta$ is the model parameter. $p(S)$ can be the distribution of training sample.

### Maximum Likelihood Estimation (MLE)
We want to find the value of $\theta$ to maximise the likelihood $p(S|\theta)$.
$$p(S|\theta)=\prod_{i=1}^n p(x_i,y_i|\theta)$$

### Modelling Noisy Observation
For all training samples:
$$p\{S|X,h,\beta^{-1}\}=\prod_{i=1}^n \mathcal{N}(y_i|h(x_i),\beta^{-1})\\
=\prod_{i=1}^n \sqrt{\frac{\beta}{2\pi}}exp\Bigl(-\frac{\beta(y_i-h(x_i))^2}{2}\Bigl)$$
if we add $-\ln()$ on both side,
$$\ln p (S|X,h,\beta^{-1}) = -\frac{n}{2}\ln \beta+\frac{n}{2}\ln(2\pi)+\frac{\beta}{2} \sum_{i=1}^n (y_i-h(x_i))^2\\
=-\frac{n}{2}\ln \beta+\frac{n}{2}\ln(2\pi)+\frac{\beta}{2} R_S(h)$$
where $R_S(s)$ is the empirical risk. 

Therefore, if we want to maxmize the conditional likelihood term $p\{S|X,h,\beta^{-1}\}$, we need to minimize the empirical risk term $R_S(s)$.

## Bias and Variance
> Underfitting - High bias
> 
> Overfitting - High variance

A large $\lambda$ leads to high bias, a small $\lambda$ leads to high variance (more complex model).

## Robustness of Surrogate Loss Functions

Let
$$f(h) = \frac{1}{n}\sum_{i=1}^n l(X_i,Y_i,h) $$
the optimality will be achieved at $h$ such that
$$\nabla f(h)=0$$

Let
$$g(t)=f(th),t \in \mathbb{R}, h \in \mathbb{R^d}$$
then
$$g'(t)=\nabla f(th)^Th$$
if
$$\nabla f(h)=0$$
then
$$g'(1)=0$$
which means we need to find an $h$ such that $g'(1)=0$.


