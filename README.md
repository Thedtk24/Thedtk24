# Thed Arthur

**Computer Science Engineering Student**

Studying computer science, specializing in High Performance Computing at ISTY, Paris-Saclay University. 

**Available May 2027** for HPC Internship.

`High Performance Computing` `Computer Architecture`\
`Distributed Computing` `Parallel Computing` `CUDA`

[LinkedIn](https://www.linkedin.com/in/thed-arthur-toko-dikongue/) | [Website](https://thed-arthur-toko-dikongue.netlify.app/)

---

## CNRS - Institut Pprime, 2026

A **4-months** research HPC engineer internship at Institut Pprime - @ISAE-ENSMA, Université de Poitiers. 

*Hardware Characterization & Performance Optimization for the **ASPHODELE** DNS Solver*

- Migrated the legacy build system to **CMake** with parallel compilation, reducing build times by **4.6x** across 256 source files.
- Transitioned to **Intel oneAPI (`ifx`)** and rebuilt the scientific stack from source (**HDF5**, **HYPRE**, **SUNDIALS**) to ensure ABI compatibility and prepare the code for national supercomputers.
- Conducted low-level performance analysis using `perf stat`, **MAQAO**, and `gprof`. Identified an arithmetic intensity of $0.557\text{ Flop/Byte}$ and an effective vectorization rate of $84.8\%$ in AVX-256, diagnosing the code as memory-bound.
- Compared Poisson solver strategies (**FFT** vs. **HYPRE PFMG** vs. **FISHPACK**), achieving a **2.9x speedup** with FFT on periodic domains, and executed strong/weak scaling runs on the *Curta* supercomputer via **SLURM**.

## ACT-ON GROUP, 2025

A **2-months** data & performance engineering internship at ACT-ON GROUP (ACT-ON DATA).

*ETL Pipeline Architecture & Performance Optimization for the **CISIRH** (RenoiRH Paie) Project*

- Engineered automated Python/SQL data pipelines (`pandas`, `sqlite3`) to process and ingest heterogeneous HR data sources into structured Staging and Data Warehouse schemas.
- Diagnosed major performance bottlenecks caused by massive data volumes, where naive historical table generation scripts required up to 2 days of execution time.
- Refactored data ingestion and processing workflows by implementing strategic table concatenations, optimized mapping dictionaries (`JSON`), and efficient relational joins to drastically improve script execution efficiency.
- Structured relational databases following a robust schema hierarchy (`CSV Staging` → `Data Warehouse` → `DataMart`) to feed analytical dashboards.

## Stack

**Programming :** C/C++, Python, GPU (CUDA), Vectorisation SIMD\
**Tools :** MPI, OpenMP, CMake, Git, Docker, SLURM, MAQAO, Linux