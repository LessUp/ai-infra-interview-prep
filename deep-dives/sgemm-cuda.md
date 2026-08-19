# 🔬 SGEMM_CUDA 深度学习指南

> **上游：** [siboehm/SGEMM_CUDA](https://github.com/siboehm/SGEMM_CUDA)
> **你的 Fork：** [LessUp/SGEMM_CUDA](https://github.com/LessUp/SGEMM_CUDA)
> **语言：** CUDA
> **建议学习时间：** 3 天
> **面试重要性：** ⭐⭐⭐⭐

---

## 📌 这个仓库是什么？

从零实现 CUDA 矩阵乘法（GEMM）的教学项目，从 naive 实现逐步优化到接近 cuBLAS 的性能。这是理解 GPU 优化最经典的案例。

## 🎯 为什么对 AI Infra 重要？

1. **GEMM 是 AI 的核心** — 神经网络中 90%+ 的计算是矩阵乘法
2. **理解优化层次** — 从 naive 到优化，每一步都对应一个优化技术
3. **面试必考** — "如何优化矩阵乘法？" 是最高频的面试题
4. **最佳教学案例** — 代码清晰，注释详细，适合学习

## 🔑 精髓：GEMM 优化的 6 个层次

### 层次 0：Naive 实现
```cuda
// 每个线程计算一个输出元素
// 性能：~10 GFLOPS（A100 理论峰值 312 TFLOPS 的 0.003%）
C[i][j] = sum(A[i][k] * B[k][j])
```

### 层次 1：Global Memory Coalescing
- 确保相邻线程访问相邻的内存地址
- 性能提升：2-3x

### 层次 2：Shared Memory Tiling
- 将矩阵分块，每个 Block 将一块数据加载到共享内存
- 减少全局内存访问
- 性能提升：5-10x

### 层次 3：Register Tiling
- 每个线程计算一个小的子块（如 4x4）
- 利用寄存器减少共享内存访问
- 性能提升：2-3x

### 层次 4：Double Buffering
- 使用两个共享内存缓冲区
- 一个用于计算，一个用于加载下一块数据
- 隐藏内存延迟
- 性能提升：1.5-2x

### 层次 5：Bank Conflict Avoidance
- 通过 Padding 避免共享内存 Bank Conflict
- 性能提升：1.2-1.5x

## 📖 推荐学习路径

### Day 1：理解基础
1. 阅读项目 README 和博客文章
2. 运行 naive 版本，用 ncu 分析性能
3. 运行 coalescing 版本，理解内存合并访问
4. 运行 tiling 版本，理解共享内存

### Day 2：深入优化
5. 运行 register tiling 版本
6. 运行 double buffering 版本
7. 运行最终优化版本，对比 cuBLAS 性能

### Day 3：动手实践
8. **核心练习**：自己从头实现一个 GEMM Kernel
9. 从 naive 开始，逐步添加优化
10. 用 ncu 分析每个版本的瓶颈

## 🎤 面试考点

1. "如何优化矩阵乘法？" — 按层次回答
2. "什么是 Coalesced Memory Access？"
3. "共享内存 Tiling 的原理？"
4. "Bank Conflict 如何解决？"
5. "Double Buffering 的作用？"

## 🔗 相关仓库
- [cuda-samples](./cuda-samples.md) — 更多 CUDA 示例
- [cuda-course](./cuda-course.md) — CUDA 课程
