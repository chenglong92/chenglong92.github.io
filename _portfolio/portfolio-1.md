---
title: "1. The Backward Error Analysis of $\mathbf{Ax} = \mathbf{b}$ with Mixed Precisions"
excerpt: "Oct. 14, 2022, Edited by Cheng Long"
collection: portfolio
---

&ensp;For the solution of linear system of equations: $\mathbf{Ax} = \mathbf{b}$, in the mixed-precision algorithms [Higham, SIAM of JSC], the low-precision matrix decomposition: $\mathbf{A}=\mathbf{LU}$ is used as the preconditioner in the iterative refinment(IR) phase. The complete three-precision algorithm is shown below:
```bash
1: Do the low-precision matrix decomposition.
```

&ensp; For instance, in the single-double-quad three-precision LU-GMRES algorithm, when the matrix $\mathbf{A}$ is decomposed as $\mathbf{A}=\mathbf{LU}$, the single-precision $\mathbf{LU}$ factor is obtained. But in the following IR phase, the following formulation is adopted:  
<center>$$\mathbf{A}_{fp32} \mathbf{d}_{fp64}=\mathbf{r}_{fp64}$$,  </center>
where  
<center>$$\mathbf{A}_{fp32} = (\mathbf{LU})_{fp64}$$,  </center>
and  
<center>$$\mathbf{r}_{fp64} = \mathbf{b}_{fp64} - \mathbf{A}_{fp64}\mathbf{x}_{fp64}$$.  </center>  
