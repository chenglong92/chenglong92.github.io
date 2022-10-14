---
title: "1. The Backward Error Analysis of \mathbf{Ax} = \mathbf{b} with Mixed Precisions"
excerpt: "Oct. 14, 2022, Edited by Cheng Long"
collection: portfolio
---

&ensp;In the mixed-precision algorithms [Higham, SIAM of JSC], the low-precision matrix decomposition: $\boldsymbol{Ax}=\boldsymbol{b}$ is used as the preconditioner in the iterative refinment(IR) phase. The complete three-precision algorithm is shown below:
```bash
1: Do the low-precision matrix decomposition.
```

&ensp; For instance, in the single-double-quad three-precision LU-GMRES algorithm, when the matrix $\mathbf{A}$ is decomposed as $\mathbf{A}=\mathbf{LU}$, the single-precision $\mathbf{LU}$ factor is obtained. But in the following IR phase, the following formulation is adopted:
$$\mathbf{A}_{fp32} \mathbf{d}_{fp64}=\mathbf{r}_{fp64}$$,
where
$$\mathbf{A}_{fp32} = (\mathbf{LU})_{fp64}$$
and 
$$\mathbf{r}_{fp64} = \mathbf{b}_{fp64} - \mathbf{A}_{fp64}\mathbf{x}_{fp64}$$
