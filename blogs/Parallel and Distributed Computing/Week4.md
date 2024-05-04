# Week 4 

## General Principles for Parallel Algorithm Design

### Speedup and efficiency

#### Speedup

Measure of relative performance improvement oversequential algotithms.

$$S=\frac{T_s}{T_p}$$
whetner adding processors can increase speedup.

#### Efficiency

The proportion of processors usefulluy utilized by the computation and defined as 
$$E=\frac{S}{p}=\frac{T_s}{pT_p}$$

**Overheads** will be introduced in most parallel programs including:
- Thread communication or synchronization
- Workload imbalance among available threads
- Extra work introduced to manage the computation and increase parallelism

$$T_O=pT_p-T_s$$

### Amdahl's law and overheads




### General desxign process


