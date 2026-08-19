# 🧠 AI Infra 知识图谱（完整版）

> 这是 AI Infra 工程师需要掌握的知识体系。每个知识点都标注了重要性和学习资源。

## 一、硬件基础

### 1.1 GPU 架构
- **NVIDIA GPU 架构演进：** Volta → Turing → Ampere → Hopper → Blackwell
- **SM (Streaming Multiprocessor)：** 核心计算单元，包含 CUDA Core + Tensor Core
- **Tensor Core：** 矩阵乘法加速器，支持 FP16/BF16/FP8/INT8
- **HBM (High Bandwidth Memory)：** 高带宽显存，A100 80GB 带宽 2TB/s
- **L1/L2 Cache：** GPU 的缓存层次
- **NVLink / NVSwitch：** GPU 间高速互联

### 1.2 内存层次
- **Global Memory (HBM)：** 容量最大，延迟最高（~数百 cycles）
- **L2 Cache：** 所有 SM 共享
- **L1 Cache / Shared Memory：** Block 内共享，低延迟（~数十 cycles）
- **Register：** 每个线程私有，最快（~1 cycle）
- **Constant Memory / Texture Memory：** 只读，有缓存

### 1.3 算力与带宽
- **Roofline 模型：** 分析 Kernel 是 Memory Bound 还是 Compute Bound
- **Arithmetic Intensity：** FLOPs / Bytes，衡量计算密度
- **Occupancy：** Warp 占用率，影响 Latency Hiding

## 二、编程模型

### 2.1 CUDA C++
- **线程层次：** Thread → Warp (32 threads) → Block → Grid
- **内存模型：** Global, Shared, Local, Constant, Texture
- **同步：** `__syncthreads()`, Cooperative Groups
- **Stream：** 异步并发执行
- **Event：** 时间测量、同步
- **CUDA Graph：** 减少 Kernel Launch 开销

### 2.2 Triton
- **Block-based 编程：** 每个 program instance 处理一个 block
- **自动优化：** 编译器自动处理 Tiling, Coalescing, Bank Conflict
- **`tl.constexpr`：** 编译时常量，用于自动调优
- **`tl.autotune`：** 自动搜索最优配置
- **与 CUDA 对比：** 更简洁，但控制粒度更粗

### 2.3 CPU 并行（已有基础）
- **OpenMP：** 共享内存并行
- **MPI：** 分布式内存并行（`ompi` 仓库）
- **SIMD：** AVX2/AVX-512（`bitcal` 仓库）

## 三、算子优化

### 3.1 GEMM 优化
- **Naive 实现：** 每个线程计算一个输出元素
- **Coalescing：** 相邻线程访问相邻内存
- **Shared Memory Tiling：** 减少全局内存访问
- **Register Tiling：** 每个线程计算子块
- **Double Buffering：** 隐藏内存延迟
- **Bank Conflict Avoidance：** Padding
- **Tensor Core 使用：** `mma.sync` 指令

### 3.2 Flash Attention
- **问题：** 标准 Attention 的 O(N²) 内存访问
- **Tiling：** 分块计算，减少 HBM 访问
- **Online Softmax：** 流式计算 softmax
- **Recomputation：** 反向传播时重新计算
- **Flash Attention 2：** 减少非 matmul FLOPs，更好的并行
- **Flash Attention 3：** Hopper 架构，异步，FP8

### 3.3 其他算子优化
- **LayerNorm / RMSNorm：** 归约优化
- **Softmax：** 数值稳定性 + 性能
- **Activation：** GELU, SiLU, SwiGLU
- **RoPE (Rotary Position Embedding)：** 位置编码
- **算子融合：** 将多个算子合并为一个 Kernel

## 四、推理引擎

### 4.1 KV Cache
- **原理：** 缓存已计算的 Key 和 Value，避免重复计算
- **内存管理：** PagedAttention（Block 管理）、RadixAttention（前缀共享）
- **驱逐策略：** LRU, FIFO, 优先级
- **前缀复用：** 多个请求共享相同前缀的 KV Cache

### 4.2 批处理
- **Static Batching：** 固定 batch size，等待所有请求完成
- **Continuous Batching (In-Flight Batching)：** 动态加入/移除请求
- **Prefill vs Decode：** 两个阶段的计算特点不同
- **Chunked Prefill：** 将长 prefill 分成多个 chunk

### 4.3 调度策略
- **FCFS (First Come First Serve)：** 最简单
- **Priority：** 优先级调度
- **Preemption：** 抢占式调度
- **公平性：** 防止饥饿

### 4.4 模型量化
- **INT8：** SmoothQuant, 需要校准
- **FP8：** H100 原生支持，精度更高
- **INT4：** GPTQ, AWQ, 需要 group-wise 量化
- **Weight-only：** 只量化权重，激活保持高精度

### 4.5 并行策略
- **Tensor Parallelism (TP)：** 将权重矩阵切分到多个 GPU
- **Pipeline Parallelism (PP)：** 将模型层切分到多个 GPU
- **Data Parallelism (DP)：** 多个 GPU 处理不同请求
- **Expert Parallelism (EP)：** MoE 模型的专家分布
- **Context Parallelism (CP)：** 长序列的上下文并行

## 五、编译器

### 5.1 ML 编译器概念
- **前端：** 支持多种框架（PyTorch, TensorFlow, ONNX）
- **IR (Intermediate Representation)：** 多层 IR（Graph IR → Operator IR → Loop IR）
- **Pass：** 优化遍（融合、折叠、消除、调度）
- **后端：** 代码生成（CUDA, ROCm, OpenCL, LLVM）

### 5.2 调度原语
- **split：** 将循环轴分割
- **fuse：** 合并多个循环
- **reorder：** 重新排列循环顺序
- **tile：** split + reorder 的组合
- **bind：** 绑定到线程/Block
- **cache_read/cache_write：** 添加缓存
- **vectorize：** 向量化
- **unroll：** 循环展开

### 5.3 自动调优
- **AutoTVM：** 基于模板 + 搜索
- **AutoScheduler：** 无模板的自动搜索
- **Triton Autotuner：** 基于 `tl.autotune`

## 六、分布式系统

### 6.1 通信原语
- **AllReduce：** 所有 GPU 求和
- **AllGather：** 收集所有 GPU 的数据
- **ReduceScatter：** 求和后分散
- **Broadcast：** 广播
- **NCCL：** NVIDIA 集合通信库

### 6.2 分布式训练
- **Data Parallelism：** 每个 GPU 有完整模型副本
- **Model Parallelism：** 模型切分到多个 GPU
- **ZeRO (DeepSpeed)：** 优化器状态、梯度、参数分片
- **FSDP (PyTorch)：** 类似 ZeRO-3

## 七、C++ 基础（已有基础，复习）

### 7.1 现代 C++（C++11/14/17/20）
- **智能指针：** unique_ptr, shared_ptr, weak_ptr
- **移动语义：** move constructor, move assignment, std::move
- **Lambda：** 匿名函数，捕获列表
- **模板：** 模板元编程, SFINAE, concepts (C++20)
- **constexpr：** 编译时计算
- **RAII：** 资源管理

### 7.2 并发与系统
- **std::thread, std::mutex, std::atomic**
- **内存模型：** acquire/release, sequential consistency
- **SIMD：** AVX2, AVX-512 intrinsics
- **性能优化：** cache line, false sharing, branch prediction

## 学习优先级

| 知识点 | 重要性 | 先修知识 | 建议时间 |
|--------|--------|----------|----------|
| CUDA 编程模型 | ⭐⭐⭐⭐⭐ | C++ | 第 1-3 周 |
| Flash Attention | ⭐⭐⭐⭐⭐ | CUDA, Attention | 第 4 周 |
| LLM 推理引擎 | ⭐⭐⭐⭐⭐ | CUDA, Transformer | 第 5-6 周 |
| Triton 语言 | ⭐⭐⭐⭐⭐ | CUDA | 第 7 周 |
| ML 编译器 | ⭐⭐⭐⭐ | 编译器基础 | 第 8 周 |
| Kernel 优化 | ⭐⭐⭐⭐ | CUDA | 第 9 周 |
| 分布式系统 | ⭐⭐⭐ | MPI, NCCL | 按需 |
| C++ 复习 | ⭐⭐⭐ | 已有基础 | 贯穿 |
