---
title: "1. The Backward Error Analysis of Mixed-precision Linear Algebra Solver"
excerpt: "Oct. 14, 2022, Edited by Cheng Long"
collection: portfolio
---

&ensp;For the solution of linear system of equations: $\mathbf{Ax} = \mathbf{b}$, in the mixed-precision algorithms [Higham, SIAM of JSC], the low-precision matrix decomposition: $\mathbf{A}=\mathbf{LU}$ is used as the preconditioner in the iterative refinment(IR) phase. The complete three-precision algorithm is shown below: 
&ensp;(1) The low-precision matrix decomposition: $\mathbf{A}=\mathbf{(LU)}$ (fp16)  
(2) Obtain the initial low-precision solution $\mathbf{x0}$ with substitution operations: $\mathbf{Ly} =\mathbf{b}$ (fp32), and $\mathbf{Ux}=\mathbf{y}$ (fp32)  
(3) Iteration Refinement:    
(4) for i = 1 : N  
(5) &emsp; residual calculation: $\mathbf{r} = \mathbf{(b-Ax)}$(fp64)  
(6) &emsp; correction equation: $\mathbf{M} \mathbf{d} = \mathbf{r}$(fp64)  
(7) &emsp; correction: $\mathbf{x} = \mathbf{x0} + \mathbf{d}$(fp64)  
(8) end  

&ensp; For instance, in the single-double-quad three-precision LU-GMRES algorithm, when the matrix $\mathbf{A}$ is decomposed as $\mathbf{A}=\mathbf{LU}$, the single-precision $\mathbf{LU}$ factor is obtained. But in the following IR phase, the following formulation is adopted:  
$$\mathbf{Ad} =\mathbf{r}$$  
where  
$$\mathbf{A} = (\mathbf{LU})$$  
and  
$$\mathbf{r} = \mathbf{b - Ax}$$  
