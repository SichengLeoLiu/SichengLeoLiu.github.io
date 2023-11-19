# Week 3 - Hypothesis Complexity and Generalization

## Predefined Hypothesis Class
Assume the target function is $c$, which fits the data best.
$$c=\underset{h}{\operatorname{\argmin}}R(h)$$
where $c$ can be inside or outside the predefined hypothesis.

### Risk
**Empirical risk.** is defined as:
$$R_S(h)=\frac{1}{n}\sum^n_{i=1}l(X_i,Y_i,h)$$
where $S$ is the training sample.

**Expected risk.** is defined as:
$$R(h)=\mathbb{E}[R_S(h)]=\mathbb{E}(l(X,Y,h))$$

The optimal hypothesis in the predefined hypothesis class:
$$h^*=\underset{h \in H}{\operatorname{\argmin}}R(h)$$

The hypothesis we can learn from data:
$$h_S=\underset{h \in H}{\operatorname{\argmin}}R_S(h)=\underset{h \in H}{\operatorname{\argmin}}\frac{1}{n}\sum^n_{i=1}l(X_i,Y_i,h)$$

**Approximation error.** is the difference between $h^*$ and $c$.

**Estimation error.** is the difference between $h_S$ and $h^*$.

By enlarging the predefined hypothesis class may be able to reduce the **Approximation error**, but large hypothesis class is hard to learn leading to a large **Estimation error**.

## Probably Approximately Correct Learning (PAC Learning)

PAC learning explains how many training examples are needed to learn the best hypothesis in the predefined class.

It provides a theoretical foundation for understanding the **generalization performance** (difference between  test performance and training performance) of learning algorithms.

It focuses on:
- Size of the training dataset
- Complexity of the hypothesis class
- Generalization error of the learned model

### Definition
$$p\{R(h_S)-\underset{h \in H}{\operatorname{\min}}R(h) \le \epsilon\} \ge 1-\delta$$
where $\epsilon$ is acceptable error and $1-\delta$ is desired confidence level.

## VC Dimension: Binary Case

We can group the classifiers.
$$H=\{(h^1_1,...,h^1_{n_1}),...,(h^G_1,...,h^G_{n_G})\}$$
Let $h^1,...,h^G$ be the representatives of each group
$$H'=\{h^1,...,h^G\}$$ 

**If VC dimension exist, $H$ is PAC learnabel.**

### Growth Function
Counts the number of distinct labeling of a hypothesis class produced on any subset of data points.
$$\forall n\in \mathbb{N}, \prod_H(n)=\underset{X_1,...,X_n}{\operatorname{\max}}|\{h(X_1),...,h(X_n):h \in H\}|$$

### Shattering
A hypothesis class shatters a set of points if it can assign all possible binary labels (0 or 1) to those points.

If data points can be shattered by a hypothesis class $H$, then
$$\prod_H(n)=2^n$$

### VC Dimension
The VC dimension of a hypothesis class $H$ is the size of the largest set that can be fully shattered by $H$:
$$VC dimension(H)=\underset{n}{\operatorname{\max}}\{n:\prod_H (n)=2^n\}$$