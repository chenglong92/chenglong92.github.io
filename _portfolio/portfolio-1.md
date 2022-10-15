---
title: "1. The Backward Error Analysis of Mixed-precision Linear Algebra Solver"
excerpt: "Oct. 14, 2022, Edited by Cheng Long"
collection: portfolio
---

&ensp;For the solution of linear system of equations: $\mathbf{Ax} = \mathbf{b}$, in the mixed-precision algorithms [Higham, SIAM of JSC], the low-precision matrix decomposition: $\mathbf{A}=\mathbf{LU}$ is used as the preconditioner in the iterative refinment(IR) phase. The complete three-precision algorithm is shown below:

***

1: The low-precision matrix decomposition: $\mathbf{A} = \mathbf{M}_{fp16} = \mathbf{LU}_{fp16}$  
2: Obtain the initial low-precision solution, $\mathbf{x}_0$, with substitution operations: $\mathbf{Ly}_{fp32}=\mathbf{b}_{fp32}$, and $\mathbf{Ux}_{fp32}=\mathbf{y}_{fp32}$  
3: Iteration Refinement:    
4: for i = 1 : N  
5:     residual calculation: $\mathbf{r}_{fp64} = \mathbf{(b-Ax)}_{fp64}$  
6:     correction equation: $\mathbf{M}_{fp16} \mathbf{d}_{fp64} = \mathbf{r}_{fp64}$  
7:     correction: $\mathbf{x}_{fp64} = \mathbf{x}_0 + \mathbf{d}_{fp64}$  
8: end  

***

&ensp; For instance, in the single-double-quad three-precision LU-GMRES algorithm, when the matrix $\mathbf{A}$ is decomposed as $\mathbf{A}=\mathbf{LU}$, the single-precision $\mathbf{LU}$ factor is obtained. But in the following IR phase, the following formulation is adopted:  
<center>$$\mathbf{A}_{fp32} \mathbf{d}_{fp64}=\mathbf{r}_{fp64}$$  </center>
where  
<center>$$\mathbf{A}_{fp32} = (\mathbf{LU})_{fp64}$$  </center>
and  
<center>$$\mathbf{r}_{fp64} = \mathbf{b}_{fp64} - \mathbf{A}_{fp64}\mathbf{x}_{fp64}$$  </center>  
