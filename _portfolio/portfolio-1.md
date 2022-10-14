---
title: "1. The Backward Error Analysis of \boldsymbol{Ax} = \boldsymbol{b} with Mixed Precisions"
excerpt: "Oct. 14, 2022, Edited by Cheng Long"
collection: portfolio
---

&ensp;In the mixed-precision algorithms [Higham, SIAM of JSC], the low-precision matrix decomposition: $\boldsymbol{Ax}=\boldsymbol{b}$ is used as the preconditioner in the iterative refinment(IR) phase. The complete three-precision algorithm is shown below:
```bash
1: Do the low-precision matrix decomposition.
```

&ensp; For instance, in the single-double-quad three-precision LU-GMRES algorithm, when the matrix $\boldsymbol{A}$ is decomposed as $\boldsymbol{A}=\boldsymbol{LU}$, the single-precision $\boldsymbol{LU}$ factor is obtained. But in the following IR phase, the following formulation is adopted:
$$\boldsymbol{A}_{fp32} \boldsymbol{d}_{fp64}=\boldsymbol{r}_{fp64}$$,
where
$$\boldsymbol{A}_{fp32} = (\boldsymbol{LU})_{fp64}$$
and 
$$\boldsymbol{r}_{fp64} = \boldsymbol{b}_{fp64} - \boldsymbol{A}_{fp64}\boldsymbol{x}_{fp64}$$
