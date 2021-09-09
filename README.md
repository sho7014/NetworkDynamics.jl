Fork of [NetworkDynamics.jl](https://github.com/PIK-ICoNe/NetworkDynamics.jl) modified to deal with non-diagonal noise.

A new vertex struct **`NonDiagonalSDEVertex(f!, dim, noise_dim, slide, mass_matrix, sym)`** is introduced.  
**`noise_dim`** is the number of compunents of noise in the a vertex equation and **`slide`** controls how the non-diagonal noise is injected. if it is set zero, the noise is vertex-independent (common noise), while if it is set equals to **`noise_dim`**, the noise can be vertex-dependent. **`noise_rate_prototype`** of a SDEProblem should also be appropiately adjusted in accordance with whether the noise is common or not. 

This is just a naive workaround, so its performance has not been examined and important features such as sparse arrays for **`noise_rate_prototype`** are not supported. 
