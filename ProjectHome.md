**LOcal Gpu Optimization TSP solver**

http://olab.is.s.u-tokyo.ac.jp/~kamil.rocki/projects.html

http://olab.is.s.u-tokyo.ac.jp/~kamil.rocki/rocki_hpcs2012.pdf

http://olab.is.s.u-tokyo.ac.jp/~kamil.rocki/rocki_pco13.pdf

**TODO**

  1. Parallel 2.5-opt, 3-opt, LK
  1. Improve perturbation
  1. MPI
  1. Improve performance for Fermi GPUs (fix the registers problem)
  1. Fix backtracking
  1. Include hostname in logging
  1. Windows GUI client source (in progress)
  1. Improve the file parser (support for other file types, i.e. ATT or GEO)
  1. Change parameter parsing (still depends on CUDA Toolkit code)
  1. Improve/Change Makefile - there are too many parameters now
  1. Implement parallel multi-GPU search for the initial descend (hybrid algorithm)
  1. Tune CUDA and OpenCL code (remove unnecessary OPs as in the CPU version)
  1. Neighborhood pruning (exponential function)
  1. Asynchronous CUDA/OpenCL execution (while GPU executes the code, CPU can work on better perturbations)

**CHANGELOG**

Logo v. 0.61 2013-04-30

---

- Fixed/Improved perturbation function

Logo v. 0.6 2013-04-18

---

  1. Parallel CPU local optimization + SSE/AVX/MIC (Xeon Phi) features
  * ./src/utils/cpusimd.h
  * ./src/solvers/cpuMTSolver.cpp
  * ./src/solvers/cpuSolver.cpp
  1. Code optimization, removed redundant calculations, fewer FLOPs
  1. Hydrid Parallel/MT CPU execution model (initial optimization done in parallel, later multiple independent threads)
  1. Tuned the kernel for Tesla K20 GPUs
  1. Fixed benchmark mode

**Older versions**

Logo v. 0.52 2013-03-29

---

  1. Reimplemented logging solutions to a file
  1. Fixed local optimization information display
  1. Multithreaded CPU mode added
  1. Fixed thread no display

Logo v. 0.51 2013-03-25

---

- Added CUDA Legacy GPUs' (i.e. 1.1, 1.2) support (Makefile - LEGACY\_GPUS Option) (no atomic operations, 16kB of shared memory and 16 registers used, reduced number of threads per block)

Logo v. 0.5 2013-03-12

---

  1. Reimplemented most of the code in C++
  1. Local and global Solvers became classes
  1. Multi-device (CPU and/or OpenCL and/or CUDA) support with multithreading
  1. Moved solvers to /solvers directory
  1. Added time limited optimization
  1. Writing visited solutions to file
  1. Removed move backtracking (need to rewrite) and partial communication
  1. Improved Makefile
  1. Fixed OS X support

Logo v. 0.4, 2013-02-08

---

  1. Added pthreads support for multithreaded multiple starting point algorithm
  1. Added communication algorithm between the threads to accelerate global search
  1. Added move backtracking to avoid being stuck in a group of local minima
  1. Improved the code structure, removed redundant parts (solver.c)
  1. Corrected the 2-opt edge swap (thanks to Bernd Paradies)

Logo v. 0.3, 2013-01-18

---

  1. Added OpenCL support
  1. Improved perturbation algorithm

Logo v. 0.2, 2012-09-26

---

  1. Fixed the memcpy to symbol in gpu.cu causing the GPU code to crash sometimes. Currently the symbol copying is substituted by simple memcpy
  1. Improved the kernels' performance by ordering input data and avoiding conflicts while copying data from global to shared memory
  1. CPU optimization routine added (sequential)
  1. KD-tree construction added to find nearest neighbors efficiently - based on the libkdtree++ library
  1. KD-tree based NN tour construction O(nlogn) time
  1. Multifragment tour construction heuristic added
  1. k nearest neighbors of point x can be found in sorted order in O(klogn) time in KD-tree

Logo v. 0.1, 2012-08-12

---

  * The initial version