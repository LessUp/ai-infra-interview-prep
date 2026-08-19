# 🔬 CUDA Samples 深度学习指南

> **上游：** [NVIDIA/cuda-samples](https://github.com/NVIDIA/cuda-samples)
> **你的 Fork：** [LessUp/cuda-samples](https://github.com/LessUp/cuda-samples)
> **语言：** C++ / CUDA
> **建议学习时间：** 2 周
> **面试重要性：** ⭐⭐⭐⭐⭐

---

## 📌 这个仓库是什么？

NVIDIA 官方维护的 CUDA 示例代码库，涵盖了从基础的内存拷贝到高级的多 GPU 并发等几乎所有 CUDA 特性。这是学习 CUDA 编程的**第一手权威资料**。

## 🎯 为什么对 AI Infra 重要？

AI Infra 工程师的核心工作之一是**写出高性能的 GPU Kernel**。CUDA Samples 提供了：
1. 每个 CUDA 特性的**最小可运行示例**，是理解 CUDA 编程模型的捷径
2. 许多示例直接对应 AI Infra 中的实际场景（矩阵乘法、卷积、归约、排序等）
3. 代码风格和最佳实践来自 NVIDIA 官方，是写 production Kernel 的参考标准

## 🧬 架构分析

### 目录结构
```
cuda-samples/
├── Common/           # 公共辅助头文件（错误处理、图像处理、数学函数）
│   ├── helper_cuda.h       # CUDA 错误检查、设备信息查询
│   ├── helper_math.h       # 向量/矩阵运算辅助函数
│   └── exception.h         # 异常处理
├── Samples/           # 按主题组织的示例（核心！）
│   ├── 0_Introduction/     # 入门：内存拷贝、设备查询、并发
│   ├── 1_Utilities/        # 工具：带宽测试、PCIe 检查
│   ├── 2_Concepts_and_Techniques/  # 核心概念：归约、扫描、排序
│   ├── 3_CUDA_Features/    # CUDA 特性：动态并行、协作组、图
│   ├── 4_CUDA_Libraries/   # 库：cuBLAS, cuFFT, cuDNN, cuSPARSE
│   └── 5_Multi_GPU/        # 多 GPU：P2P、UCX、域间
├── cpp/               # 第 13 个版本后改用 C++ 重写
└── python/            # 部分示例的 Python 版本
```

## 🔑 精髓：必须掌握的核心示例

### 第 1 优先级 — CUDA 编程基础（第 1 周前 3 天）

| 示例 | 路径 | 核心知识点 | 面试考点 |
|------|------|------------|----------|
| **vectorAdd** | `0_Introduction/vectorAdd` | 最基础的 CUDA 程序：host→device 拷贝、kernel launch、同步 | "写一个完整的 CUDA 程序框架" |
| **asyncAPI** | `0_Introduction/asyncAPI` | Stream 异步并发、cudaMemcpyAsync | "Stream 的作用是什么？" |
| **simpleIPC** | `0_Introduction/simpleIPC` | 进程间共享 GPU 内存 | "多进程如何共享 GPU 数据？" |
| **concurrentKernels** | `0_Introduction/concurrentKernels` | 多 Stream 并发执行 Kernel | "如何让多个 Kernel 同时执行？" |

### 第 2 优先级 — 内存管理（第 1 周后 3 天）

| 示例 | 路径 | 核心知识点 | 面试考点 |
|------|------|------------|----------|
| **matrixMul** | `0_Introduction/matrixMul` | 共享内存 Tiling、线程协作 | "矩阵乘法如何优化？" |
| **transpose** | `2_Concepts_and_Techniques/transpose` | 共享内存 Bank Conflict、Pad | "什么是 Bank Conflict？如何解决？" |
| **simpleAtomic** | `0_Introduction/simpleAtomic` | 原子操作 | "原子操作对性能的影响？" |
| **vectorAddDrv** | `0_Introduction/vectorAddDrv` | Driver API vs Runtime API | "Driver API 和 Runtime API 的区别？" |

### 第 3 优先级 — 性能优化（第 2 周）

| 示例 | 路径 | 核心知识点 | 面试考点 |
|------|------|------------|----------|
| **reduction** | `2_Concepts_and_Techniques/reduction` | 归约算法、Warp Shuffle、循环展开 | "如何实现高效的归约？" |
| **scan** | `2_Concepts_and_Techniques/scan` | 前缀和、Blelloch 算法 | "并行前缀和的实现？" |
| **histogram** | `2_Concepts_and_Techniques/histogram` | 直方图、原子操作优化 | "如何处理竞争写入？" |
| **sortingNetworks** | `2_Concepts_and_Techniques/sortingNetworks` | 排序网络、Bitonic Sort | "GPU 上如何排序？" |
| **shfl_scan** | `2_Concepts_and_Techniques/shfl_scan` | Warp Shuffle 指令 | "Warp Shuffle 有什么用？" |

### 第 4 优先级 — 高级特性（第 2 周）

| 示例 | 路径 | 核心知识点 | 面试考点 |
|------|------|------------|----------|
| **bf16TensorCoreGemm** | `3_CUDA_Features/bf16TensorCoreGemm` | Tensor Core 编程 | "Tensor Core 怎么用？" |
| **cudaGraphs** | `3_CUDA_Features/cudaGraphs` | CUDA Graph | "CUDA Graph 的优势？" |
| **simpleCudaGraphs** | `3_CUDA_Features/simpleCudaGraphs` | 最简单的 CUDA Graph 示例 | "什么场景适合用 CUDA Graph？" |
| **jacobiCudaGraphs** | `3_CUDA_Features/jacobiCudaGraphs` | 迭代算法中的 CUDA Graph | "CUDA Graph 的限制？" |
| **p2pBandwidthLatencyTest** | `5_Multi_GPU/p2pBandwidthLatencyTest` | 多 GPU 间通信 | "NVLink 带宽是多少？" |

## 📖 推荐学习路径

### 第 1 周：基础夯实

**Day 1-2：入门与编程模型**
1. 阅读 `helper_cuda.h` — 理解 CUDA 错误处理模式
2. 运行 `vectorAdd` — 理解 host/device 代码结构
3. 运行 `deviceQuery` — 了解你的 GPU 硬件参数
4. 修改 `vectorAdd`：改变 block/grid 大小，观察性能变化

**Day 3-4：内存与并发**
5. 运行 `asyncAPI` — 理解 Stream 和异步操作
6. 运行 `concurrentKernels` — 观察多 Stream 并发
7. 运行 `matrixMul` — 理解共享内存 Tiling
8. 运行 `transpose` — 理解 Bank Conflict
9. **动手**：自己写一个向量加法，对比你的实现与示例的性能

**Day 5-7：核心算法**
10. 运行 `reduction` — 理解 Warp Shuffle 归约
11. 运行 `scan` — 理解前缀和算法
12. 运行 `sortingNetworks` — 理解 GPU 排序
13. **动手**：用 CUDA 实现一个 LayerNorm Kernel

### 第 2 周：高级特性与实战

**Day 8-10：Tensor Core 与 CUDA Graph**
14. 运行 `bf16TensorCoreGemm` — 理解 Tensor Core 编程
15. 运行 `cudaGraphs` 系列 — 理解 CUDA Graph
16. **动手**：用 Tensor Core 实现一个简单的矩阵乘法

**Day 11-14：多 GPU 与综合练习**
17. 运行 `p2pBandwidthLatencyTest` — 理解 GPU 间通信
18. 运行 `simpleIPC` — 理解进程间 GPU 内存共享
19. **最终练习**：实现一个完整的 GEMM Kernel，从 naive 到优化版本，对比 cuBLAS 性能

## 🎤 面试考点关联

通过这个仓库，你应该能回答：

1. **CUDA 基础：** "线程层次结构？Block 和 Grid 的关系？"
2. **内存模型：** "全局内存 vs 共享内存？什么时候用共享内存？"
3. **性能优化：** "如何优化矩阵乘法？什么是 Bank Conflict？"
4. **并发：** "Stream 的作用？如何实现 Kernel 和 memcpy 的重叠？"
5. **高级特性：** "Tensor Core 是什么？CUDA Graph 适合什么场景？"

## 💡 学习技巧

1. **不要只看不跑** — 每个示例都编译运行，用 `nsys` 或 `ncu` 分析性能
2. **修改参数实验** — 改变 block size、grid size、数据大小，观察性能变化
3. **对比优化前后** — 比如 matrixMul 的 naive 版本 vs 共享内存版本
4. **写笔记** — 记录每个示例的核心知识点和你的理解
5. **关注 `helper_cuda.h`** — 这个文件包含了大量实用的 CUDA 工具函数

## 🔗 相关仓库

- [SGEMM_CUDA](./sgemm-cuda.md) — 从零实现 GEMM，深入理解矩阵乘法优化
- [cuda-course](./cuda-course.md) — CUDA 课程，系统学习
- [lectures](./lectures.md) — gpu-mode 讲座，补充 GPU 编程知识