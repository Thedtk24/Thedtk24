# Thed Arthur TOKO DIKONGUE

**Computer Science Engineering Student**

Studying computer scienc, specializing in High Performance Computing at ISTY, Paris-Saclay University. 

**Available May 2027** for HPC Internship.

![High Performance Computing](https://img.shields.io/badge/C-333333?style=for-the-badge&logo=c&logoColor=white)
![Computer Architecture](https://img.shields.io/badge/C%2B%2B-333333?style=for-the-badge&logo=cplusplus&logoColor=white)
![Distributed Computing](https://img.shields.io/badge/Python-333333?style=for-the-badge&logo=python&logoColor=white)
![Parallel Computing](https://img.shields.io/badge/Fortran-333333?style=for-the-badge&logo=fortran&logoColor=white)
![GPU Computing](https://img.shields.io/badge/CUDA-333333?style=for-the-badge&logo=nvidia&logoColor=white)

[LinkedIn](https://www.linkedin.com/in/thed-arthur-toko-dikongue/) | [Website](https://thed-arthur-toko-dikongue.netlify.app/)

---

## Oak Ridge National Laboratory, summer 2025

Research Intern, Graduate Research at ORNL (GRO), summer 2025. I built GPU energy-measurement tooling for **Kokkos**, the C++ performance-portability library behind many US Department of Energy codes: a sampling daemon and connectors that read power through NVML or Variorum every 20 ms, plus an AMD path through ROCm SMI, not public yet, which is the version that ran on Frontier. They attach at run time through Kokkos Tools, so an application is measured without a rebuild.

- **Ran on Frontier**, the first exascale supercomputer (the ROCm SMI version; those runs were not kept), and on production SLURM clusters.
- **Found a cost a timer understates.** On the same input and result, ArborX's dense DBSCAN takes 19% less time than the default one but 25% less energy, because it also draws 9% less power (medians of 64 runs on an H100 NVL, [re-analysed in 2026](https://ethan-puyaubreau.github.io/blog/kokkos-gpu-energy); [traces and script](https://github.com/ethan-puyaubreau/smc2025-gpu-energy-poster#data-and-reproduction) are public).
- **Went through public review.** 11 PRs, [10 to kokkos-tools](https://github.com/kokkos/kokkos-tools/pulls?q=is%3Apr+author%3Aethan-puyaubreau) and [1 to LAMMPS](https://github.com/lammps/lammps/pull/4624): 4 merged: the sampling daemon I started ([kokkos-tools #300](https://github.com/kokkos/kokkos-tools/pull/300), reworked through review by my ORNL mentor after my stay), two build fixes and a fix for the nightly ROCm builds ([#349](https://github.com/kokkos/kokkos-tools/pull/349)). The core ([#299](https://github.com/kokkos/kokkos-tools/pull/299)), the NVML connector ([#301](https://github.com/kokkos/kokkos-tools/pull/301), changes requested) and the Variorum connector with its unit tests ([#302](https://github.com/kokkos/kokkos-tools/pull/302), draft) are still open, as is a follow-up that fixes, builds and tests the daemon ([#350](https://github.com/kokkos/kokkos-tools/pull/350)).
- **Presented.** Poster at the 2025 Smoky Mountains Conference and at an ORNL internal session ([*Understanding GPU energy dynamics in HPC applications*](https://github.com/ethan-puyaubreau/smc2025-gpu-energy-poster)), and invited to present at SC25 (declined, apprenticeship schedule). Cited in ORNL's [S4PST 2024-2025 report](https://www.osti.gov/biblio/3016977).

The analysis side is open source and archived on Zenodo ([DOI 10.5281/zenodo.22943410](https://doi.org/10.5281/zenodo.22943410)): [energy-dashboard-for-kokkos](https://github.com/ethan-puyaubreau/energy-dashboard-for-kokkos), rewritten in September 2026 as a single Rust binary that attributes measured energy to Kokkos regions and kernels, with a console table, a Perfetto trace and a standalone HTML report.

In October 2026 I repeated the DBSCAN study on an AMD Instinct MI210 with [mi210-energy-counter](https://github.com/ethan-puyaubreau/mi210-energy-counter): a characterization of AMD's cumulative energy counter (15.3 µJ resolution, refreshed every millisecond) and an experimental Kokkos Tools connector that samples it, separate from the version that ran on Frontier. Same input, 64 runs of each: the dense implementation takes 38% less time and 42% less energy.

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