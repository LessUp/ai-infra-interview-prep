# 第 1 周：CUDA 编程基础

> 📅 日期范围：YYYY-MM-DD ~ YYYY-MM-DD
> 🎯 本周目标：掌握 CUDA 核心编程模型，能写简单的优化 Kernel

## 学习内容

### 周一：CUDA 编程模型入门
- [ ] 阅读 CUDA C++ Programming Guide 第 1-2 章
- [ ] 运行 `cuda-samples/Samples/0_Introduction/vectorAdd` — 理解 host/device 代码结构
- [ ] 运行 `cuda-samples/Samples/0_Introduction/deviceQuery` — 了解你的 GPU 硬件参数
- [ ] 手写一个向量加法的 CUDA Kernel
- [ ] **核心概念：** Thread, Block, Grid, Warp 的层次结构

### 周二：内存模型
- [ ] 阅读 CUDA C++ Programming Guide 第 3 章（内存）
- [ ] 运行 `cuda-samples/Samples/0_Introduction/matrixMul` — 理解共享内存
- [ ] 运行 `cuda-samples/Samples/2_Concepts_and_Techniques/transpose` — 理解 Bank Conflict
- [ ] **核心概念：** Global Memory, Shared Memory, Register, Constant Memory, Texture Memory
- [ ] **面试题：** "什么是 Bank Conflict？如何解决？"

### 周三：异步并发与 Stream
- [ ] 运行 `cuda-samples/Samples/0_Introduction/asyncAPI` — 理解 Stream
- [ ] 运行 `cuda-samples/Samples/0_Introduction/concurrentKernels` — 多 Stream 并发
- [ ] **核心概念：** Stream, Event, cudaMemcpyAsync, 重叠执行
- [ ] **面试题：** "Stream 的作用是什么？如何实现 Kernel 和 memcpy 的重叠？"

### 周四：矩阵乘法优化（一）
- [ ] 阅读 `SGEMM_CUDA` 的 naive 实现和 coalescing 版本
- [ ] 理解 Global Memory Coalescing
- [ ] 运行并对比性能
- [ ] **核心概念：** Coalesced Memory Access, 内存对齐

### 周五：矩阵乘法优化（二）
- [ ] 阅读 `SGEMM_CUDA` 的 shared memory tiling 版本
- [ ] 理解 Tiling 如何减少全局内存访问
- [ ] 运行并对比性能
- [ ] **核心概念：** Tiling, Shared Memory, Thread Synchronization

### 周六：动手实践
- [ ] 从零实现一个矩阵乘法 Kernel（naive 版本）
- [ ] 添加 Coalescing 优化
- [ ] 添加 Shared Memory Tiling
- [ ] 用 `ncu`（Nsight Compute）分析每个版本的性能瓶颈

### 周日：复习与总结
- [ ] 整理本周笔记
- [ ] 完成 progress-tracker 打卡
- [ ] 列出本周遇到的问题
- [ ] 预览下周内容

## 本周总结

### 收获
- 

### 问题
- 

### 下周计划
- 第 2 周：PyTorch 内部机制与 C++ 扩展
