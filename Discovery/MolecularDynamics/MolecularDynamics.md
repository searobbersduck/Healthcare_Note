# Molecular Dynamics


## Amber

* [Amber 2020 Reference Manual](https://ambermd.org/doc12/Amber20.pdf)
  * 商业软件
  * Starting with Amber 20, Amber supports use of the NVidia NCCL library for communications between multiple GPUs, which an provide a performance improvement over plain MPI. If the library is enabled (using - DNCCL=TRUE), then it will be activated when pmemd.MPI.cuda is run on 3 or more GPUs.
  * The NVIDIA Collective Communications Library (NCCL) is a library of multi-GPU collective communication primitives that are topology-aware. NCCL can be enabled when running on more than 2 GPUs in the same node. This may improve multi-GPU scaling, especially on systems with NVLINKs between GPUs. NCCL requires glibc 2.17 or higher CUDA 10.0 or higher, and runs on GPU’s with a compute capability of 3.5 (K80 equivalent) and higher..
    * To enable NCCL, first install NCCL on your system. There are two ways to install NCCL. To install NCCL from source
    * Alternatively, pre-built NCCL packages can be downloaded from NVIDIA’s website.
    * Next, the environment variable NCCL_HOME should be set to point to NCCL install path.
    * Finally, to enable NCCL in Amber, add -DNCCL=TRUE to the cmake configure options. Note NCCL build requires both MPI and CUDA to be enabled. 