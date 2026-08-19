# 🧠 AI Infra 知识图谱

## 一、硬件基础
- GPU 架构（NVIDIA SM, Tensor Core, HBM）
- 内存层次（Global, Shared, Register, L1/L2 Cache）
- NVLink / NVSwitch / InfiniBand
- 算力与带宽计算

## 二、编程模型
- CUDA C++（Thread, Block, Grid, Warp, Stream, Event）
- Triton（Block-based programming）
- OpenMP / MPI（CPU 并行）

## 三、算子优化
- GEMM 优化（Tiling, Coalescing, Bank Conflict, Software Pipelining）
- Flash Attention（Tiling, Recomputation, Online Softmax）
- LayerNorm / Softmax / Activation 优化
- 算子融合

## 四、推理引擎
- KV Cache 管理
- PagedAttention
- Continuous Batching / Inflight Batching
- 调度策略（FCFS, Priority, Preemption）
- 模型量化（INT8/FP8/INT4）
- 模型并行（Tensor Parallelism, Pipeline Parallelism）

## 五、编译器
- 计算图 IR（TVM Relay, MLIR, Triton IR）
- 图优化（常量折叠、算子融合、死代码消除）
- 自动调优（AutoTVM, AutoScheduler, Triton Autotuner）
- 代码生成（CUDA, ROCm, OpenCL, Metal）

## 六、分布式系统
- 数据并行 / 模型并行 / 混合并行
- 集合通信（AllReduce, AllGather, ReduceScatter）
- NCCL / MPI
- 分布式训练框架（DeepSpeed, Megatron-LM, FSDP）

## 七、C++ 基础（复习）
- C++11/14/17/20 新特性
- 智能指针、RAII
- 模板元编程
- 多线程与并发
- SIMD 编程（AVX2/AVX-512）
