# Week 4 - General Principles for Parallel Algorithm Design

### Speedup

Measure of relative performance improvement over sequential algotithms.

$$S=\frac{T_s}{T_p}$$
where $T_s$ is the time for sequential program and $T_p$ is the time for parallele program. It measures the relative performance improvement over sequential program.

### Efficiency

The proportion of processors usefulluy utilized by the computation and defined as 
$$E=\frac{S}{p}=\frac{T_s}{pT_p}$$

**Overheads** will be introduced in most parallel programs including:
- Thread communication or synchronization
- Workload imbalance among available threads
- Extra work introduced to manage the computation and increase parallelism

$$T_o=pT_p-T_s$$

In practice, the more processors we use, the more overheads we will have.

## Amdahl's law 

Amdahl’s law is used to predict the theoretical speedup when using multiple processors for parallel computing. Assume $\beta$ part of program is purely sequential and $1-\beta$ part can be parallized.

$$T_p=\beta T_s + (1-\beta) T_s/p$$

The theoretical speedup is
$$S=\frac{T_s}{\beta T_s + (1-\beta) T_s/p}=\frac{p}{1-\beta(p-1)}$$
when $p\rightarrow \infin$, $S\rightarrow \frac{1}{\beta}$


## General design process

