# 🔬 Triton 深度学习指南

> **上游：** [triton-lang/triton](https://github.com/triton-lang/triton)
> **你的 Fork：** [LessUp/triton](https://github.com/LessUp/triton)
> **语言：** MLIR / Python / C++
> **建议学习时间：** 1.5 周
> **面试重要性：** ⭐⭐⭐⭐⭐

---

## 📌 这个仓库是什么？

Triton 是 OpenAI 开发的开源 GPU 编程语言和编译器。它允许开发者用 Python 风格编写 GPU Kernel，由编译器自动优化为高效的 CUDA 代码。Triton 已经成为 AI Infra 领域**最重要的 GPU 编程工具之一**。

## 🎯 为什么对 AI Infra 重要？

1. **降低 GPU 编程门槛** — 不需要手写复杂的 CUDA 代码
2. **自动优化** — 编译器自动处理 Tiling、Coalescing、Bank Conflict 等
3. **工业标准** — PyTorch 2.0 的 `torch.compile` 使用 Triton 作为 GPU 后端
4. **面试必考** — 越来越多的 AI Infra 岗位要求 Triton 编程能力

## 🧬 架构分析

### 核心目录结构

```
triton/
├── python/
│   ├── triton/              # Triton Python API
│   │   ├── language/        # 🔥 Triton 编程语言前端
│   │   │   ├── core.py           # Triton 语言核心（@triton.jit, triton.language）
│   │   │   └── semantic.py       # 语义分析
│   │   ├── compiler/        # 编译器
│   │   │   ├── compiler.py       # 编译入口
│   │   │   └── code_generator.py # 代码生成
│   │   ├── runtime/         # 运行时
│   │   │   ├── driver.py         # CUDA Driver 封装
│   │   │   └── jit.py            # JIT 编译
│   │   └── testing.py       # 测试工具
│   └── tutorials/           # 🔥 官方教程（必读！）
│       ├── 01-vector-add.py
│       ├── 02-fused-softmax.py
│       ├── 03-matrix-multiplication.py
│       ├── 04-low-memory-dropout.py
│       ├── 05-layer-norm.py
│       └── 06-fused-attention.py
│
├── lib/                     # 🔥 编译器核心（C++/MLIR）
│   ├── Analysis/            # 分析 passes
│   ├── Conversion/          # IR 转换
│   ├── Dialect/             # Triton IR 方言定义
│   └── Target/              # 目标代码生成（CUDA/ROCm）
│
├── include/                 # 头文件
│   └── triton/              # Triton IR 定义
│
├── test/                    # 测试
│   └── Triton/              # Triton 语言测试
│
└── third_party/             # 第三方依赖
    └── nvidia/              # NVIDIA 后端相关
```

## 🔑 精髓：必须掌握的 3 个核心概念

### 1. Block-based 编程模型

**与 CUDA 的区别：**
- CUDA：手动管理 Thread Block 和 Grid
- Triton：只需指定 Block 大小，编译器自动处理 Thread 映射

**核心思想：**
```python
@triton.jit
def kernel(x_ptr, y_ptr, output_ptr, N, BLOCK_SIZE: tl.constexpr):
    # 每个 program instance 处理一个 block
    pid = tl.program_id(0)
    offsets = pid * BLOCK_SIZE + tl.arange(0, BLOCK_SIZE)
    mask = offsets < N
    x = tl.load(x_ptr + offsets, mask=mask)
    y = tl.load(y_ptr + offsets, mask=mask)
    output = x + y
    tl.store(output_ptr + offsets, output, mask=mask)
```

**关键文件：**
- `python/triton/language/core.py` — `tl.program_id`, `tl.load`, `tl.store` 等

### 2. 编译器优化流程

**Triton 编译流程：**
1. Python AST → Triton IR（MLIR 方言）
2. Triton IR → Triton GPU IR（添加内存层次）
3. Triton GPU IR → LLVM IR / PTX
4. PTX → 可执行二进制

**关键文件：**
- `lib/Conversion/` — 各种 IR 转换 pass
- `lib/Target/` — 目标代码生成
- `python/triton/compiler/` — 编译入口

**面试考点：** "Triton 编译器做了哪些优化？"

### 3. 自动 Tiling 与内存优化

**核心优势：**
- 自动将大矩阵划分为小块（Tiling）
- 自动管理共享内存
- 自动处理 Bank Conflict
- 自动优化内存访问模式（Coalescing）

**关键文件：**
- `lib/Analysis/` — 内存分析
- `lib/Dialect/` — Triton GPU IR 的内存操作

## 📖 推荐学习路径

### 第 1 周：Triton 编程

**Day 1-2：入门**
1. 阅读 `README.md` — 了解 Triton 的设计理念
2. 运行 `tutorials/01-vector-add.py` — 第一个 Triton 程序
3. 运行 `tutorials/02-fused-softmax.py` — 理解算子融合
4. 阅读 `python/triton/language/core.py` — 理解 Triton 语言 API

**Day 3-4：矩阵乘法**
5. 运行 `tutorials/03-matrix-multiplication.py` — 核心教程
6. **动手**：自己写一个矩阵乘法 Kernel
7. 对比 naive 实现和优化实现
8. 理解 Tiling 参数对性能的影响

**Day 5-7：高级算子**
9. 运行 `tutorials/04-low-memory-dropout.py`
10. 运行 `tutorials/05-layer-norm.py`
11. 运行 `tutorials/06-fused-attention.py` — **Flash Attention 的 Triton 实现**
12. **动手**：用 Triton 实现一个 Flash Attention Kernel

### 第 2 周（3 天）：编译器

**Day 8-10：编译器内部**
13. 阅读 `python/triton/compiler/compiler.py` — 理解编译流程
14. 阅读 `lib/Dialect/` — 理解 Triton IR
15. 用 `TRITON_DEBUG=1` 环境变量查看中间 IR
16. 理解 `tl.constexpr` 和 `tl.autotune` 的工作原理

## 🎤 面试考点关联

1. **编程模型：** "Triton 和 CUDA 的编程模型有什么区别？"
2. **编译器：** "Triton 编译器做了哪些优化？"
3. **实践：** "用 Triton 写一个矩阵乘法 Kernel"
4. **Flash Attention：** "用 Triton 实现 Flash Attention 的关键步骤？"
5. **自动调优：** "Triton 的 autotune 机制是如何工作的？"

## 💡 学习技巧

1. **从 tutorial 开始** — 6 个官方教程覆盖了所有核心概念
2. **对比 CUDA** — 同一个算法用 CUDA 和 Triton 分别实现，理解差异
3. **看 IR** — 用 `TRITON_DEBUG=1` 查看中间表示，理解编译器做了什么
4. **做 Triton-Puzzles** — 配套练习巩固理解
5. **读 Flash Attention 的 Triton 实现** — 这是 Triton 的最佳实践案例

## 🔗 相关仓库

- [Triton-Puzzles](./triton-puzzles.md) — Triton 编程练习
- [flash-attention](./flash-attention.md) — Flash Attention 实现（含 Triton 版本）
- [tvm](./tvm.md) — 另一个 ML 编译器，对比学习
- [cuda-samples](./cuda-samples.md) — CUDA 编程基础