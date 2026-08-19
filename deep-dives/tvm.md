# 🔬 TVM 深度学习指南

> **上游：** [apache/tvm](https://github.com/apache/tvm)
> **你的 Fork：** [LessUp/tvm](https://github.com/LessUp/tvm)
> **语言：** Python / C++
> **建议学习时间：** 1.5 周
> **面试重要性：** ⭐⭐⭐⭐

---

## 📌 这个仓库是什么？

Apache TVM 是一个开源的**端到端 ML 编译器框架**。它可以将深度学习模型从各种框架（PyTorch, TensorFlow, ONNX 等）编译为优化的机器代码，部署到各种硬件（CPU, GPU, FPGA, 专用加速器）上。

TVM 是 ML 编译器领域的**奠基性项目**，理解 TVM 就理解了 ML 编译器的核心思想。

## 🎯 为什么对 AI Infra 重要？

1. **理解编译器思想** — ML 编译器的核心概念（IR, Pass, Schedule, Codegen）
2. **算子自动优化** — AutoTVM/AutoScheduler 是自动调优的经典实现
3. **代码生成** — 理解如何生成高效的 CUDA/ROCm 代码
4. **面试加分** — 展示你对编译器的理解

## 🧬 架构分析

### 核心目录结构

```
tvm/
├── src/                     # 🔥 C++ 核心实现
│   ├── ir/                      # IR 定义（Expr, Stmt, Type）
│   ├── tir/                     # Tensor IR（底层循环优化 IR）
│   │   ├── analysis/            # 分析 passes
│   │   ├── transform/           # 变换 passes
│   │   └── schedule/            # 调度原语
│   ├── relax/                   # Relax IR（高层图 IR）
│   ├── relay/                   # Relay IR（传统高层 IR）
│   ├── te/                      # Tensor Expression（算子定义 DSL）
│   ├── topi/                    # 标准算子库（类似 NumPy）
│   ├── target/                  # 目标代码生成
│   │   ├── llvm/                # LLVM 后端
│   │   ├── cuda/                # CUDA 后端
│   │   └── rocm/                # ROCm 后端
│   ├── auto_scheduler/          # 自动调度器
│   └── runtime/                 # 运行时
│
├── python/tvm/              # Python 接口
│   ├── tir/                     # TIR Python API
│   ├── relay/                   # Relay Python API
│   ├── relax/                   # Relax Python API
│   ├── topi/                    # 算子库 Python API
│   ├── auto_scheduler/          # 自动调度 Python API
│   └── contrib/                 # 第三方集成
│
├── apps/                    # 应用示例
├── tests/                   # 测试
└── docs/                    # 文档
```

## 🔑 精髓：TVM 的 4 层抽象

### 第 1 层：Relay/Relax（高层图 IR）

**作用：** 表示深度学习模型的计算图

**核心概念：**
- 计算图（Graph）：节点是算子，边是数据流
- 算子融合（Fusion）：将多个算子合并为一个
- 常量折叠（Constant Folding）：编译时计算常量
- 死代码消除（Dead Code Elimination）

**关键文件：**
- `src/relay/` — Relay IR 实现
- `src/relax/` — Relax IR（新一代）

### 第 2 层：Tensor Expression（算子定义）

**作用：** 用类似 NumPy 的语法定义算子

```python
# 定义矩阵乘法
A = te.placeholder((M, K), name='A')
B = te.placeholder((K, N), name='B')
k = te.reduce_axis((0, K), name='k')
C = te.compute((M, N), lambda i, j: te.sum(A[i, k] * B[k, j], axis=k))
```

**关键文件：**
- `src/te/` — Tensor Expression 实现
- `python/tvm/te/` — Python API

### 第 3 层：Schedule（调度原语）

**作用：** 指定如何优化算子的执行

**核心调度原语：**
- `split` — 将循环轴分割为多个
- `fuse` — 将多个循环轴合并
- `reorder` — 重新排列循环顺序
- `bind` — 将循环绑定到线程/Block
- `tile` — split + reorder 的组合（Tiling）
- `cache_read/cache_write` — 添加缓存（共享内存）
- `vectorize` — 向量化
- `unroll` — 循环展开

**关键文件：**
- `src/tir/schedule/` — 调度原语实现

**面试考点：** "TVM 的调度原语有哪些？Tiling 如何实现？"

### 第 4 层：Codegen（代码生成）

**作用：** 将优化后的 IR 生成目标代码

**支持的 target：**
- CUDA (PTX)
- ROCm (AMD GPU)
- LLVM (CPU)
- OpenCL
- Metal
- Vulkan
- 自定义加速器

**关键文件：**
- `src/target/` — 各 target 的代码生成

## 📖 推荐学习路径

### Day 1-3：理解核心概念

1. 阅读 `README.md` — 了解 TVM 的设计理念
2. 运行 TVM 的 Quick Start 教程
3. 理解 TVM 的 4 层抽象（Relay → TE → Schedule → Codegen）
4. 用 TVM 编译一个简单的矩阵乘法并对比性能

### Day 4-5：调度原语

5. 学习 `split`, `fuse`, `reorder` — 基本循环变换
6. 学习 `tile` — Tiling 是优化的核心
7. 学习 `cache_read/cache_write` — 添加共享内存
8. 学习 `bind` — 绑定到 GPU 线程
9. **动手**：优化一个矩阵乘法，对比不同调度策略的性能

### Day 6-8：自动调优

10. 理解 AutoTVM 的工作原理（模板 + 搜索）
11. 理解 AutoScheduler（无模板的自动搜索）
12. 运行自动调优示例
13. **动手**：用 AutoTVM 调优一个算子

### Day 9-10：代码生成

14. 阅读 `src/target/cuda/` — 理解 CUDA 代码生成
15. 理解如何生成高效的 PTX 代码
16. 对比 TVM 生成的代码和手写 CUDA 的差异

## 🎤 面试考点关联

1. **编译器：** "ML 编译器的核心组件？"
2. **IR：** "为什么需要多层 IR？"
3. **调度：** "TVM 的调度原语有哪些？"
4. **自动调优：** "AutoTVM 和 AutoScheduler 的区别？"
5. **代码生成：** "如何生成高效的 CUDA 代码？"

## 💡 学习技巧

1. **从 Tutorial 开始** — TVM 的官方教程非常详细
2. **理解分层设计** — 每一层解决不同的问题
3. **动手实践** — 编译一个真实模型（如 ResNet）并部署
4. **对比 Triton** — 理解 TVM（显式调度）和 Triton（编译器自动优化）的不同哲学

## 🔗 相关仓库

- [triton](./triton.md) — 另一个 ML 编译器，对比学习
- [cuda-samples](./cuda-samples.md) — 理解 GPU 底层优化
