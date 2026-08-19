# 📋 3 个月 AI Infra 学习路线图

## 总体目标

在 3 个月内具备 AI Infra 工程师的面试能力，能够：
- 熟练编写 CUDA/Triton 高性能 Kernel
- 理解 LLM 推理引擎的完整架构与优化技术
- 掌握 ML 编译器的基本原理
- 有 1-2 个可展示的实战项目

## 阶段一：基础夯实（第 1-4 周）

### 第 1 周：CUDA 编程基础
- [ ] CUDA 编程模型（Thread, Block, Grid, Warp）
- [ ] 内存层次（Global, Shared, Local, Constant, Texture）
- [ ] 异步并发与 Stream
- [ ] 矩阵乘法优化（Tiling, Coalescing, Bank Conflict）
- [ ] 运行 cuda-samples 中的关键示例
- [ ] 完成 SGEMM_CUDA 的阅读与运行

### 第 2 周：PyTorch 内部机制
- [ ] PyTorch 的 dispatch 机制
- [ ] C++ extension 编写（ATen, C10）
- [ ] Autograd 原理
- [ ] 自定义 CUDA Kernel for PyTorch
- [ ] 完成 extension-cpp 教程

### 第 3 周：GPU 性能优化
- [ ] Nsight Systems / Nsight Compute 使用
- [ ] Roofline 模型
- [ ] 内存带宽 vs 计算瓶颈分析
- [ ] Occupancy 与 Latency Hiding
- [ ] 完成 lectures 中相关章节

### 第 4 周：Flash Attention
- [ ] 标准 Attention 的内存瓶颈
- [ ] Tiling / Recomputation 策略
- [ ] Online Softmax
- [ ] Flash Attention 2 的改进
- [ ] 阅读 flash-attention 源码

## 阶段二：核心深入（第 5-8 周）

### 第 5 周：LLM 推理引擎
- [ ] KV Cache 管理
- [ ] PagedAttention
- [ ] Continuous Batching
- [ ] 调度策略
- [ ] 阅读 vllm 和 sglang 源码

### 第 6 周：TensorRT-LLM
- [ ] 图优化（Layer Fusion, Constant Folding）
- [ ] INT8/FP8 量化
- [ ] Tensor Parallelism / Pipeline Parallelism
- [ ] 阅读 TensorRT-LLM 源码

### 第 7 周：Triton 语言
- [ ] Triton 编程模型
- [ ] 写 Matrix Multiply Kernel
- [ ] 写 Flash Attention Kernel
- [ ] 写 LayerNorm Kernel
- [ ] 完成 Triton-Puzzles

### 第 8 周：ML 编译器
- [ ] 计算图 IR
- [ ] 调度原语
- [ ] AutoTVM / AutoScheduler
- [ ] 代码生成
- [ ] 阅读 tvm 源码

## 阶段三：实战与面试（第 9-12 周）

### 第 9 周：FlashInfer 与 Kernel 开发
- [ ] 阅读 flashinfer 源码
- [ ] 自定义 Kernel 编写

### 第 10 周：个人项目
- [ ] 完成 1-2 个展示项目

### 第 11 周：系统设计与面试
- [ ] 系统设计练习
- [ ] 刷题

### 第 12 周：查漏补缺
- [ ] 全面复习
- [ ] 模拟面试
