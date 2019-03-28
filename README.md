# GPU Tutorial

## Table of Contents
- [1. CPU and GPU](#1-cpu-and-gput)
- [2. Hardware and Software](#2-hardware-and-software)
- [3. GPU Memory Hierarchy](#3-gpu-memory-hierarchy)
- [4. GPU Core Microarchitecture](#4-gpu-core-microarchitecture)
- [5. Branch Divergence](#5-branch-divergence)
- [6. NVIDIA GPU Technologies](#6-nvidia-gpu-technologies)
- [7. AMD GPU Technologies](#7-amd-gpu-technologies)
- [8. GPU Interconnects](#8-gpu-interconnects)

## 1. CPU and GPU
### 1.1. Five-stage Processor Pipeline (CPU)
1. IF: Instruction Fetch
2. ID: Instruction Decode / Register File Read
3. EX: Execute / Address Calculation
4. MEM: Memory Access
5. WB: Write Back
![cpu_pipeline](images/ch1/cpu_pipeline.png)

### 1.2. Hazards<br />
Hazards: `Situations that stall the starting of the next instruction in the next cycle.`<br />
1. Structure hazards<br />
A required resource is busy.<br />
2. Data hazards<br />
Need to wait for previous instruction to complete its data read/write.<br />
3. Control hazards<br />
Deciding on control action depends on previous instruction.<br />

### 1.3. Out-of-Order (OoO) CPU
?

### 1.4. Associative Cache
- One-way set associative (direct-mapped) cache<br />
![](images/ch1/1way.png)
- Two-way set associative cache<br />
![](images/ch1/2way.png)
- Four-way set associative cache<br />
![](images/ch1/4way.png)
- Eight-way set associative cache<br />
![](images/ch1/8way.png)

### 1.5. Typical CPU Memory Hierarchy
![](images/ch1/memory_hierarchy.png)

- Block (Line): `Unit of copying, has multiple words.`<br />
- Hit: `If accessed data is present in upper level.`<br />
- Miss: `If accessed data is present in upper level.`<br />
Block copied from lower level, if it's a miss.<br />

### 1.6. Memory Locality
1. Temporal locality: `Items accessed recently are likely to be accessed again soon.`<br />
2. Spatial locality: `Items near those accessed recently are likely to be accessed soon.`<br />

## 1.7. Types of Parallelism
1. ILP: Instruction-Level Parallelism
2. MLP: Memory-Level Parallelism
3. TLP: Thread-Level Parallelism

## 1.8. History of GPU Evolution
GPU: Initially for Graphics<br />
Graphics-based GPU Pipeline (before 2006) Processor per function<br />
Vertex
-> Geometry
-> Pixel
-> Render Output Unit
-> Framebuffer

#### Unified Shader Model(GeForce 8 Series)
Any work can be performed on any shader
core -> High performance computing

Why?
Vertex Workload != Pixel Workload

Need balanced use of vertex shader and pixel shader?

After 2006
Vertex | Geometry | Pixel
-> Render Output Unit
-> Framebuffer

#### SM

#### Basic idea of high performance GPU
Many simple cores
- No fancy Branch prediction
- No Complex O-o-O control logic
- No memory prefetcher
- No cache coherence

Unified shader cores
- Sharing instruction stream across groups of fragments

Stall latency hiding
- When a group stalls, work on another group
Multiple Contexts(Thread groups/Warps) 
Can hide stall times

## 2 Hardware and Software
![](images/ch2/sw2hw.png)

### CUDA
Grid <- Blocks <- Threads

Grid, Block
Number of blocks specified in three dimensions 
dimGrid(X, Y, Z)

example
Define how many blocks<br />
dim3 dimGrid(1, 1, 1);

Block, Thread
Number of threads per block is specified in three dimensions 
dimBlock(X, Y, Z)

example
Define how many threads per block.<br />
dim3 dimBlock(M.height * N.width, 1, 1);

Kernel is a dimGrid; 
each block in the grid has;<br />

example
MatrixMulKernel<<< dimGrid, dimBlock>>>(AonGPU, BonGPU, ConGPU);<br />

### Threads and Thread Blocks
### Thread Assignment

macroscopically
### NVIDA Fermi(GeForce400) pipeline microscopically

## 3 GPU Memory Hierarchy
### Layout
![](images/ch3/fermi_layout.png)
![](images/ch3/fermi_sm_layout.png)

## 4 GPU Core Microarchitecture
- Fetch & Decode
- Scoreboard<br />
Traditional hazard detection score board for RAW and WAW hazards<br />
- Operand Collector, for Register Read
- Instruction Scheduler
- Execution Stage

### Four execution blocks within a Fermi SM

![](images/ch4/fermi_execution.png)

## 5 Branch Divergence

## 6 NVIDIA GPU Technologies
32 threads within a Warp

Streaming Multiprocessor: warps within a thread block 
Stream Processors: thread

kernel < thread block < warps < 32 threads

## 7 AMD GPU Technologies
![](images/ch7/cuda_vs_opencl.png)

## 8 GPU Interconnects


