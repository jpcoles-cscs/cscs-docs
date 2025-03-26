[](){#openmpi}
# OpenMP

[OpenMP](https://www.openmp.org/specifications/) OpenMP is a shared-memory parallel programming API that provides compiler directives, runtime routines, and environment variables to simplify multithreading in C, C++, and Fortran.
It is a common library that HPC applications use to achieve node-level parallelism.


## Known issues

!!! warning
    As of 26-Mar-2025 the [Santis][ref-cluster-santis] cluster is configured in "Low Noise Mode" (LNM). This setting confines system processes and operations
    to the first core of each of the four NUMA regions in a node (i.e., cores 0, 72, 144, 216).

    The consequence of this setting is that only 71 cores per socket can be requested by an application (for a total of 284 cores instead of 288 cores per node).

    Furthermore, LNM requires that OpenMP-based applications instruct OpenMP to properly place threads on the remaining cores.

On [Santis][ref-cluster-santis] the recommended OpenMP affinity settings are

```bash
export OPENMP_PLACES=cores
export OPENMP_PROC_BIND=close
```
