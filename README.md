# Thed Arthur TOKO DIKONGUE

**Computer Science Engineering Student**

Studying computer scienc, specializing in High Performance Computing at ISTY, Paris-Saclay University. 

**Available May 2027** for HPC Internship.

![High Performance Computing](https://img.shields.io/badge/High_Performance_Computing-00599C?style=for-the-badge&logoColor=white)
![Computer Architecture](https://img.shields.io/badge/Computer_Architecture-00599C?style=for-the-badge&logoColor=white)
![Distributed Computing](https://img.shields.io/badge/Distributed_Computing-00599C?style=for-the-badge&logoColor=white) 

![Parallel Computing](https://img.shields.io/badge/Parallel_Computing-00599C?style=for-the-badge&logoColor=white) 
![CUDA](https://img.shields.io/badge/CUDA-00599C?style=for-the-badge&logoColor=white) 

[LinkedIn](https://www.linkedin.com/in/thed-arthur-toko-dikongue/) | [Website](https://thed-arthur-toko-dikongue.netlify.app/)

---

## CNRS - Institut Pprime, summer 2026

Research HPC Engineer - Internship at @ISAE-ENSMA, Université de Poitiers. 

*Hardware Characterization & Performance Optimization for the **ASPHODELE** DNS Solver*

- Migrated the legacy build system to **CMake** with parallel compilation, reducing build times by **4.6x** across 256 source files.
- Transitioned to **Intel oneAPI (`ifx`)** and rebuilt the scientific stack from source (**HDF5**, **HYPRE**, **SUNDIALS**) to ensure ABI compatibility and prepare the code for national supercomputers.
- Conducted low-level performance analysis using `perf stat`, **MAQAO**, and `gprof`. Identified an arithmetic intensity of $0.557\text{ Flop/Byte}$ and an effective vectorization rate of $84.8\%$ in AVX-256, diagnosing the code as memory-bound.
- Compared Poisson solver strategies (**FFT** vs. **HYPRE PFMG** vs. **FISHPACK**), achieving a **2.9x speedup** with FFT on periodic domains, and executed strong/weak scaling runs on the *Curta* supercomputer via **SLURM**.

## EDF R&D, work-study (2023-2026)

On the C++ platform that simulates EDF's nuclear reactor cores (500k+ lines, 30+ engineers):

- **Wrote the memory and compute-time profilers** (C++, Python bindings). The memory profiler pinned down a memory blow-up the team had been chasing for days.
- **Developed the prototype of a new modular architecture for the neutronics solvers** and measured it with those tools: bit-for-bit identical results, **up to 12% faster** on the compute core, **38% lower peak memory**.
- **Automated the test and delivery chain**: cluster runs, result validation, PostgreSQL ingestion, Debian packaging (Jenkins, GitLab CI/CD).
- **Worked in the team's process**: code reviews given and received, five internal technical notes, Sphinx documentation for the tools.

## heapline

**[heapline](https://github.com/ethan-puyaubreau/heapline)** reports the heap usage of a Linux program through `LD_PRELOAD`, without recompiling it. The idea comes from the memory profiler I wrote at EDF; heapline is a new implementation, written after my work-study ended from the same open mechanism (interposing the glibc allocation functions) and none of the internal code, built the way I wanted that tool to be.

- **Packaged**: x86_64 and aarch64 archives, RPM and Debian packages, a manual page, six releases since September 2026.
- **[Documented](https://ethan-puyaubreau.github.io/heapline/)** with tutorials for one program and for an MPI job, and a case study of miniAMR, LULESH and CloverLeaf built with Spack.
- **[heapline-gate](https://github.com/ethan-puyaubreau/heapline-gate)** fails a CI build when a program's heap peak exceeds a budget.

## Infrastructure I run

A [5-node Proxmox cluster](https://ethan-puyaubreau.github.io/cluster) I have designed and operated alone since 2020, for about twenty services and ~60 regular users. Over the years it has run Ceph, Ansible and GitLab CI; today Gitea and Coolify carry the CI/CD and a Kubernetes VM runs alongside, behind Traefik, Authelia SSO and a VyOS-segmented network, watched by Gatus and Uptime Kuma. Every incident is mine.

**[proxmox-ops-mcp](https://github.com/ethan-puyaubreau/proxmox-ops-mcp)** lets an AI assistant operate that cluster. Every command goes through a deny-by-default classifier; destructive ones wait for my approval on a separate channel and land in an append-only audit log, so a prompt injection cannot approve itself.

## Side project

**[nbody-webgpu](https://github.com/ethan-puyaubreau/nbody-webgpu)**: up to 65,536 bodies in a WGSL compute shader, tiled through workgroup shared memory, leapfrog integrator. [Run it in your browser](https://ethan-puyaubreau.github.io/nbody-webgpu/).

<a href="https://ethan-puyaubreau.github.io/nbody-webgpu/"><img src="galaxy.webp" alt="Spiral galaxy simulated in real time with WebGPU compute shaders" width="560"></a>

## Stack

**HPC:** C++17/20 · CUDA · Kokkos · MPI · OpenMP · SLURM · NVML · ROCm-SMI\
**Research software:** Python · PyBind11 · CMake · Spack · Rust · Git · GitHub Actions · GitLab CI · Sphinx\
**Infra:** Proxmox · Kubernetes · Ceph · Docker · Traefik · Ansible\
**Also:** PostgreSQL · TypeScript · WebGPU

---

**Hiring a research software engineer for early 2027? [Email me](mailto:ethan.puyaubreau@gmail.com).**