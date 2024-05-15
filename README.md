# INF648-Project

## Dataset

### Link
[SGEMM GPU kernel performance](https://archive.ics.uci.edu/dataset/440/sgemm+gpu+kernel+performance)

### Citation
Paredes,Enrique and Ballester-Ripoll,Rafael. (2018). SGEMM GPU kernel performance. UCI Machine Learning Repository. https://doi.org/10.24432/C5MK70.

### Description

Running times for multiplying two 2048 x 2048 matrices using a GPU OpenCL SGEMM kernel with varying parameters (using the library 'CLTune').

Parameters description:
```
// =================================================================================================
//
// Matrices are accessed as follows:
// A: [k*M + m], with 'k' ranging from 0:K and 'm' from 0:M (m,k,m)
// B: [k*N + n], with 'k' ranging from 0:K and 'n' from 0:N (n,k,n)
// C: [n*M + m], with 'n' ranging from 0:N and 'm' from 0:M (m,n,m)
//
// Or as an image (assuming column-major)
//       K                      
//    o-------o                 
//    |       |                 
//  N | [B^T] |                 
//    |       |                 
//    o-------o                 
//        K               N     
//    o-------o        o-----o  
//  M |  [A]  |      M | [C] |  
//    |       |        |     |  
//    o-------o        o-----o  
//                              
//
// Parameters determined by the tuner
// MWG       : Tile-size in dimension M (e.g. 64, 128)
// NWG       : Tile-size in dimension N (e.g. 64, 128)
// KWG       : Tile-size in dimension K (e.g. 8, 16)
// MDIMC     : Threads per workgroup in M-dimension (e.g. 8, 16, 32)
// NDIMC     : Threads per workgroup in N-dimension (e.g. 8, 16, 32)
// MDIMA     : Re-shaped tile dimension of matrix A: KDIMA * MDIMA
// NDIMB     : Re-shaped tile dimension of matrix B: KDIMB * NDIMB
// KWI       : Unroll factor of the KWG loop (smaller or equal than KWG)
// VWM       : Vector width of matrices A and C (supported 1, 2, 4, and 8)
// VWN       : Vector width of matrix B (supported 1, 2, 4, and 8)
// STRM      : Use strided access within a thread in the M-dimension (1) or not (0)
// STRN      : Use strided access within a thread in the N-dimension (1) or not (0)
// SA        : Use local/shared memory to cache matrix A (1) or not (0)
// SB        : Use local/shared memory to cache matrix B (1) or not (0)
// PRECISION : Whether to use single (32) or double (64) precision data-types
//
// =================================================================================================
```

## Resources

- [CLTune: A Generic Auto-Tuner for OpenCL Kernels (2015)](https://cnugteren.github.io/downloads/Nugteren2015a.pdf)
- [Towards a Benchmarking Suite for Kernel Tuners (2023)](https://www.researchgate.net/publication/369300511_Towards_a_Benchmarking_Suite_for_Kernel_Tuners)
- [Sobol Tensor Trains for Global Sensitivity Analysis (2017)](https://arxiv.org/pdf/1712.00233)

