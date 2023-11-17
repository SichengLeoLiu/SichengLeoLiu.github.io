# Week 12 - Multi-Task Learning

## Multi-Task Learning
Multi-task Learning is an approach to learn multiple related problems at the same time, by exploiting the **relatedness** between problems.

###  Problem Setup
Given $m$ learning tasks $\{\tau_i\}^m_{i=1}$, multi-task learning aims to help improve the learning for a model for $\tau_i$ by using gthe knowledge contained in all or some of the $m$ tasks.

For task $\tau_i$, we have training set $\mathcal{D}_i=\{x_j^i, y_j^i\}_{j=1}^{n_i}$.

Our taks is to learn hypothesis for $\{\tau_i\}^m_{i=1}$.

### What to share?
- Parameters
- Features


## MLT Model

> Consider we have:
>
> Linear hypothesis function: $h(x)=w^Tx$.
>
> Different tasks: $\{\tau_i\}^m_{i=1}$
>
> The hypothesis for $i^{th}$ task: $w^i$

The empirical risk can be:
$$\underset{W=[w^1,...W^m]}{\operatorname{\min}}\frac{1}{m} \sum^m_{i=1} \frac{1}{n_i} \sum^{n_i}_{j=1}(l(x_j^i, y_j^i, w^i))$$
but there is no relativeness been considered.

### Parameter-based MTL Models
If we assume the multiple tasks are related by their parameter that
$$w^i = w_0+\Delta w^i$$
where $w_0$ is the shared features and $\Delta w^i$ is the task specific features.

Therefore, we can have the new objective function.
$$\underset{w_0,\Delta W=[\Delta w^1,...\Delta W^m]}{\operatorname{\min}}\frac{1}{m} \sum^m_{i=1} \frac{1}{n_i} \sum^{n_i}_{j=1}(l(x_j^i, y_j^i, w_0+\Delta w^i))$$

In order to enforcing the model to have stronger relatedness, we want to enlarge $w_0$ and reduce the $\Delta w^i$. We can add a regularizer in the objective function.
$$\underset{w_0,\Delta W=[\Delta w^1,...\Delta W^m]}{\operatorname{\min}}\frac{1}{m} \sum^m_{i=1} \frac{1}{n_i} \sum^{n_i}_{j=1}(l(x_j^i, y_j^i, w_0+\Delta w^i))+\lambda ||\Delta W||^2_F$$

### Feature-based MTL Models

We want to project features to a new feature space so that those features are more related.
$$\mathcal{D}_i=\{P^Tx_j^i, y_j^i\}_{j=1}^{n_i}$$
where $P$ is a projection matrix.

Then the new objective function can be
$$\underset{W,P}{\operatorname{\min}}\frac{1}{m} \sum^m_{i=1} \frac{1}{n_i} \sum^{n_i}_{j=1}(l(P^T x_j^i, y_j^i,w^i))+\lambda rank(W) \\ s.t. PP^T=I$$
