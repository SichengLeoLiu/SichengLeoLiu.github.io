# Week 9 - Learning with Noise Data: Label Noise
> Problem setup:
> 
> Observation: $X \in \mathcal{X} \subset \mathbb{R}^d$.
> 
> Clean but unobservable label: $Y \in \mathcal{Y}=\{-1,+1\}$.
> 
> Observable but noisy label: $\widetilde{Y} \in \mathcal{Y}$
> 
> Clean distribution: $D(X,Y)$
> 
> Noisy distribution: $D_{\rho}(X,\widetilde{Y})$

Our target is to learn a discriminant function $f_n:\mathcal{X} \rightarrow \mathbb{R}$ such that the classifier predicts the correct label $y$ given an observation $x$ (using noisy learn clean label).

A probabilistic model:
$$\rho_Y(X)=P(\widetilde{Y}|Y,X)$$
where $\rho_Y(X)$ is called flipping probability (flip rate).

## Random Classification Noise (RCN)
The flipping probability is independent of $X$ and $Y$.
$$\rho_{+1}(X)=\rho_{-1}(X)=\rho$$

Symmetric loss function is robust to RCN when the function class $\mathcal{F}_{lin}$ is extended to the universal function space (any kind of hyphothesis), which means the function in it can be of any form.

Symmetric loss function follow
$$L(f(X),+1)+L(f(X),-1)=C$$
where $C$ is a constant. That is
$$\underset{f}{\operatorname{\argmin}}R_{D,L}(f)=\underset{f}{\operatorname{\argmin}}R_{D_\rho,L}(f)$$




## Class-dependent Label Noise: Binary
The flipping probability is depend on the class.
$$\rho_{+1}(X)=\rho_{+1}\\\rho_{-1}(X)=\rho_{-1}$$

### Importance Reweighting
Viewing the noisy data and clean data are sampled from two domains.

$$R_{D,L}(f)=\mathbb{E}_{(X,Y) \sim D}[L(f(X),Y)]=\int P_D(X,Y)L(f(X),Y)dXdY\\
=\mathbb{E}_{(X,Y) \sim D_\rho}[\frac{P_D(X,Y)}{P_{D_\rho}(X,Y)}L(f(X),Y)]\\
=\mathbb{E}_{(X,Y) \sim D_\rho}[\beta(X,Y)L(f(X),Y)]$$
where $\beta(x,y)=\frac{P_D(X=x,Y=y)}{P_{D_\rho}(X=x,\widetilde{Y}=y)}$.

In RCN, we have:
$$P_{D_\rho}(\widetilde{Y}=y|X=x)=(1-\rho_{+1}-\rho_{-1})P_D(Y=y|X=x)+\rho_{-y}$$

Then we can calculate the value of $\beta$ if we know the flip rate $\rho$.
$$ \beta(x,y)=\frac{P_D(X=x,Y=y)}{P_{D_\rho}(X=x,\widetilde{Y}=y)} \\
=\frac{P_D(Y=y|X=x)}{P_{D_\rho}(\widetilde{Y}=y|X=x)} \\
=\frac{P_{D_\rho}(\widetilde{Y}=y|X=x)-\rho_{-y}}{(1-\rho_{+1}-\rho_{-1}P_{D_\rho})(\widetilde{Y}=y|X=x)}$$

## Class-dependent Label Noise: Multi-class

In multi-class case, we have:
$$\begin{bmatrix} P(\widetilde{Y}=1|x) \\ ... \\ P(\widetilde{Y}=C|x) \end{bmatrix}=\begin{bmatrix} P(\widetilde{Y}=1|Y=1,x) & ... &P(\widetilde{Y}=1|Y=C,x) \\ ... &...&...\\ P(\widetilde{Y}=C|x) &...& P(\widetilde{Y}=C|Y=C,x)\end{bmatrix}\begin{bmatrix} P(Y=1|x) \\ ... \\ P(Y=C|x) \end{bmatrix}$$
where $C$ is the num of class. We call this transition matrix noted as $T$.

**Forward.** 

**Backward.** 