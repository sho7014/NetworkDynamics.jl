Fork of [NetworkDynamics.jl](https://github.com/PIK-ICoNe/NetworkDynamics.jl) modified to deal with non-diagonal noise.

A new vertex struct **`NonDiagonalSDEVertex(f!, dim, noise_dim, slide, mass_matrix, sym)`** is introduced.  

- **`noise_dim`** is the number of components of noise in a vertex equation (Ito dimension). Only problems with homogeneous Ito dimesions are currently supported.  
- **`slide`** controls how the non-diagonal noise is injected. if it is set zero, the noise is vertex-independent (common noise), while if it is set equals to **`noise_dim`**, the noise can be vertex-dependent.  
    **`noise_rate_prototype`** of a **`SDEProblem`** should also be appropriately adjusted in accordance with whether the noise is shared or not. Consider a system of SDEs with **`N`** vertices for an example. If the noise is shared among vertices, **`noise_rate_prototype`** should be an array of size **`(N*dim, noise_dim)`**, otherwise set it that of size **`(N*dim, N*noise_dim)`**. 

This is just a naive workaround, so its performance has not been examined and important features such as sparse arrays for **`noise_rate_prototype`** are not supported. The features which are not tested and hence might not be supported currently is as follows. 

- Non-identity mass matrix
- **`ODEEdge`**
- DDEs (promotions are not defined)
- **`noise_rate_prototype`** option defined as other than normal **`Array`**  
- Networks with heterogeneous Ito dimensions
