# 🔬 vLLM 深度学习指南

> **上游：** [vllm-project/vllm](https://github.com/vllm-project/vllm)
> **你的 Fork：** [LessUp/vllm](https://github.com/LessUp/vllm)
> **语言：** Python / C++ / CUDA
> **建议学习时间：** 2 周
> **面试重要性：** ⭐⭐⭐⭐⭐

---

## 📌 这个仓库是什么？

vLLM 是目前最流行的开源 LLM 推理引擎，由 UC Berkeley 开发。它引入了 **PagedAttention** 这一革命性的 KV Cache 管理技术，将 LLM 推理的吞吐量提升了 10-20 倍。

## 🎯 为什么对 AI Infra 重要？

vLLM 是 LLM 推理引擎的**事实标准**，几乎所有 AI Infra 岗位的面试都会问到：
1. PagedAttention 的原理
2. Continuous Batching 的实现
3. KV Cache 管理策略
4. 调度算法

理解了 vLLM，你就理解了现代 LLM 推理系统的核心设计。

## 🧬 架构分析

### 核心目录结构

```
vllm/
├── vllm/
│   ├── engine/              # 🔥 推理引擎核心
│   │   ├── llm_engine.py         # 离线推理引擎
│   │   ├── async_llm_engine.py   # 在线异步推理引擎
│   │   ├── arg_utils.py          # 引擎参数配置
│   │   └── protocol.py           # 引擎协议定义
│   │
│   ├── model_executor/      # 🔥 模型执行器
│   │   ├── model_loader/         # 模型加载
│   │   ├── layers/              # 各类 Layer 实现（Attention, MLP, Norm）
│   │   ├── models/              # 模型定义（LLaMA, GPT, Qwen 等）
│   │   └── kernels/             # 自定义 CUDA Kernel
│   │
│   ├── kernels/             # 🔥 CUDA/Triton Kernel
│   │   ├── triton/              # Triton 实现的 Kernel
│   │   └── vllm_c.py           # C++/CUDA Kernel 的 Python 绑定
│   │
│   ├── distributed/         # 分布式推理
│   │   ├── parallel_state.py    # 并行状态管理
│   │   └── communication_op.py  # 通信操作
│   │
│   ├── lora/                # LoRA 适配器
│   ├── config.py            # 配置系统
│   └── entrypoints/         # API 入口（OpenAI 兼容）
│
├── csrc/                    # C++/CUDA 源码
│   ├── cache_kernels.cu        # KV Cache 相关 Kernel
│   ├── attention_kernels.cu     # Attention Kernel
│   ├── activation_kernels.cu    # 激活函数 Kernel
│   └── quantization/            # 量化相关 Kernel
│
└── benchmarks/              # 性能基准测试
```

## 🔑 精髓：必须理解的 5 个核心概念

### 1. PagedAttention（最核心！）

**问题：** 传统 KV Cache 管理使用连续内存分配，导致严重的内存碎片和浪费。

**解决方案：** PagedAttention 借鉴操作系统的虚拟内存分页机制：
- 将 KV Cache 划分为固定大小的 **Block**（类似内存页）
- 通过 **Block Table** 进行逻辑到物理的映射
- 允许非连续的物理存储

**关键文件：**
- `vllm/model_executor/layers/attention.py` — Attention 层实现
- `csrc/cache_kernels.cu` — KV Cache 的 CUDA Kernel
- `vllm/kernels/triton/attention.py` — Triton 实现的 Attention

**面试考点：** "PagedAttention 的原理？为什么能提升吞吐量？"

### 2. Continuous Batching

**问题：** 传统 Static Batching 需要等一个 batch 中所有请求完成才能加入新请求。

**解决方案：** Continuous Batching（也叫 In-flight Batching）：
- 每个 step 都可以动态加入新请求
- 完成的请求立即移出，释放资源
- 最大化 GPU 利用率

**关键文件：**
- `vllm/engine/llm_engine.py` — `step()` 方法
- `vllm/model_executor/scheduler.py` — 调度器

**面试考点：** "Continuous Batching 和 Static Batching 的区别？"

### 3. KV Cache 管理

**关键文件：**
- `vllm/model_executor/layers/kv_cache.py` — KV Cache 分配与回收
- `csrc/cache_kernels.cu` — 底层 CUDA 实现

**面试考点：** "KV Cache 的生命周期？如何管理内存？"

### 4. 调度器 (Scheduler)

**关键文件：**
- `vllm/model_executor/scheduler.py` — 核心调度逻辑

**调度流程：**
1. 从等待队列选择请求
2. 分配 KV Cache Block
3. 构建 Batch
4. 执行推理
5. 释放完成的请求

**面试考点：** "如何设计一个 LLM 推理调度器？"

### 5. 模型并行

**关键文件：**
- `vllm/distributed/parallel_state.py`
- `vllm/model_executor/layers/linear.py` — 包含 Tensor Parallelism 的 Linear

**面试考点：** "Tensor Parallelism 和 Pipeline Parallelism 的区别？"

## 📖 推荐学习路径

### 第 1 周：理解核心机制

**Day 1-2：整体架构**
1. 阅读 `README.md` — 了解项目全貌
2. 运行 `examples/offline_inference.py` — 跑一个最简单的推理
3. 阅读 `vllm/engine/llm_engine.py` — 理解引擎的整体流程
4. 追踪一个请求的完整生命周期：`add_request()` → `step()` → `output`

**Day 3-4：PagedAttention**
5. 阅读论文 "Efficient Memory Management for Large Language Model Serving with PagedAttention"
6. 阅读 `vllm/model_executor/layers/attention.py` — 理解 PagedAttention 实现
7. 阅读 `csrc/cache_kernels.cu` — 理解底层 CUDA 实现
8. 画图：画出 Block Table 的结构和映射关系

**Day 5-7：调度与 KV Cache**
9. 阅读 `vllm/model_executor/scheduler.py` — 理解调度逻辑
10. 阅读 `vllm/model_executor/layers/kv_cache.py` — 理解 KV Cache 管理
11. 阅读 `vllm/model_executor/models/llama.py` — 理解一个完整模型的实现

### 第 2 周：深入细节与扩展

**Day 8-10：Kernel 与优化**
12. 阅读 `vllm/kernels/triton/` — 理解 Triton Kernel 实现
13. 阅读 `csrc/attention_kernels.cu` — 理解 Attention Kernel
14. 对比 Flash Attention 和 vLLM 的 Attention 实现

**Day 11-14：分布式与高级特性**
15. 阅读 `vllm/distributed/` — 理解分布式推理
16. 阅读 `vllm/lora/` — 理解 LoRA 支持
17. 阅读 `vllm/entrypoints/openai/` — 理解 OpenAI 兼容 API

## 🎤 面试考点关联

1. **PagedAttention：** "为什么需要 PagedAttention？它解决了什么问题？"
2. **Continuous Batching：** "如何实现动态批处理？"
3. **KV Cache：** "KV Cache 的内存管理策略？"
4. **调度：** "如何设计调度策略来最大化吞吐量？"
5. **系统设计：** "设计一个支持 1000 QPS 的 LLM 推理服务"

## 💡 学习技巧

1. **先读论文再读代码** — PagedAttention 论文是理解代码的前提
2. **画架构图** — 画出请求的生命周期、KV Cache 的分配流程
3. **对比阅读** — 同时看 vLLM 和 SGLang，理解不同的设计选择
4. **跑起来** — 实际部署 vLLM，用 benchmark 测试性能
5. **关注 PR** — vLLM 的 PR 讨论非常有价值，展示了设计决策的过程

## 🔗 相关仓库

- [sglang](./sglang.md) — 另一个主流推理框架，对比学习
- [nano-vllm](./nano-vllm.md) — 精简版 vLLM，快速理解核心
- [flash-attention](./flash-attention.md) — Attention 优化的基础
- [flashinfer](./flashinfer.md) — LLM 推理 Kernel 库