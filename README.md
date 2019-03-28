# GPU Tutorial

## Table of Contents
- [1 CPU and GPU](#1-fundamentals-of-git)
- [2 Hardware and Software](#)
- [3 GPU Memory Hierarchy](#)
- [4 GPU Core Microachitecture](#)
- [5 Branch Divergence](#)
- [6 NVIDIA GPU Technologies](#)
- [7 AMD GPU Technologies](#)
- [8 GPU Interconnects](#)

## 1 CPU and GPU
## 2 Hardware and Software
## 3 GPU Memory Hierarchy
## 4 GPU Core Microachitecture
## 5 Branch Divergence
## 6 NVIDIA GPU Technologies
## 7 AMD GPU Technologies
## 8 GPU Interconnects

### Hazards<br />
- Structure hazards<br />
A required resource is busy
- Data hazards<br />
Need to wait for previous instruction to complete its data read/write
- Control hazards<br />
Deciding on control action depends on previous instruction

### Cache<br />
direct-mapped cache
associative cache

### 
Memory Hierarchy

###
block
hit
miss

Temporal locality
Spatial locality

ILP: Instruction-Level Parallelism
MLP: Memory-Level Parallelism
TLP: Thread-Level Parallelism

Unified Shader Model

Multiple Contexts(Thread groups/Warps) 
Can hide stall times

32 threads within a Warp

Streaming Multiprocessor: warps within a thread block 
Stream Processors: thread

kernel < thread block < warps < 32 threads
