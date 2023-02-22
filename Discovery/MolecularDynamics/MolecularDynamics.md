# Molecular Dynamics


<br>

****
<br>

## Amber

* ### [Amber 2020 Reference Manual](https://ambermd.org/doc12/Amber20.pdf)
  * 商业软件, NV不提供Docker
  * Starting with Amber 20, Amber supports use of the NVidia NCCL library for communications between multiple GPUs, which an provide a performance improvement over plain MPI. If the library is enabled (using - DNCCL=TRUE), then it will be activated when pmemd.MPI.cuda is run on 3 or more GPUs.
  * The NVIDIA Collective Communications Library (NCCL) is a library of multi-GPU collective communication primitives that are topology-aware. NCCL can be enabled when running on more than 2 GPUs in the same node. This may improve multi-GPU scaling, especially on systems with NVLINKs between GPUs. NCCL requires glibc 2.17 or higher CUDA 10.0 or higher, and runs on GPU’s with a compute capability of 3.5 (K80 equivalent) and higher..
    * To enable NCCL, first install NCCL on your system. There are two ways to install NCCL. To install NCCL from source
    * Alternatively, pre-built NCCL packages can be downloaded from NVIDIA’s website.
    * Next, the environment variable NCCL_HOME should be set to point to NCCL install path.
    * Finally, to enable NCCL in Amber, add -DNCCL=TRUE to the cmake configure options. Note NCCL build requires both MPI and CUDA to be enabled. 
    * ![](./images/Amber2020_nccl.jpg)

<br><br>

* ### [Amber开发计划]()
  * Amber is basically a single GPU application. The multi-GPU scaling is expected to be bad. That's mainly because almost all Amber users only use single GPU to run Amber so Amber developers don't care very much about multi-GPU scaling. BTW, we integrated NCCL into Amber. So if you really want to do multi-GPU, it's recommended to turn on NCCL. See section 2.2.2 of https://ambermd.org/doc12/Amber20.pdf.
  * This is some old data on DGX-1V comparing the MPI vs NCCL for Amber multi-GPU scaling.
  * Furthermore, AFAIK, there is no current effort or plan to optimize Amber on multi-GPU.

<br><br>

* ### [155个GPU！多云场景下的Amber自由能计算](https://fastonetech.com/blog/bio-amber-and-multi-cloud/)
  * 对药物分子的虚拟筛选，仅仅实现分子对接是不够的，往往会面临一个问题就是药物分子活性的评价。许多药物和其它生物分子的活性都是通过与受体大分子之间的相互作用表现出来的，是动态的。
  * 受体和配体之间结合自由能（Binding Afinity）评价是基于结构的计算机辅助药物分子设计的核心问题。
  * 基于分子动力学（Molecular Dynamics, MD）模拟的炼金术自由能（Alchemical Free Energy，AFE）计算是提高我们对各种生物过程的理解以及加快多种疾病的药物设计和优化的关键工具。
  * MD模拟实验数据量大，计算周期长，常用软件包括Amber、NAMD、GROMACS、Schrödinger等等。GPU的并行处理技术能大大加速计算效率，所以很多MD模拟软件都开始支持GPU。
    * GROMACS作为一款开源软件，完全免费，但其成熟版本对于GPU的支持并不理想，教程相对少，对用户的要求比较高。
    * Schrödinger是商用软件，功能全面，GPU支持很好，但License是按使用核数计算的，价格相对昂贵。
    * Amber软件包包括两个部分：AmberTools和Amber
      * AmberTools可以在Amber官网免费下载和使用，Tools中包含了Amber绝大部分模块，但不支持PMEMD和GPU加速。
      * Amber是收费的，从Amber11开始支持GPU加速仿真，Amber18开始支持GPU计算自由能，且教程齐全易操作，不限制CORE的使用数量。2020年4月，已经更新到Amber20版本。

<br>

****

<br>

## MISC

