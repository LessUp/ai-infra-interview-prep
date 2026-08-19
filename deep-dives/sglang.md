# 🔬 SGLang 深度学习指南

> **上游：** [sgl-project/sglang](https://github.com/sgl-project/sglang)
> **你的 Fork：** [LessUp/sglang](https://github.com/LessUp/sglang)
> **语言：** Python / C++ / CUDA
> **建议学习时间：** 1 周
> **面试重要性：** ⭐⭐⭐⭐⭐

---

## 📌 这个仓库是什么？

SGLang 是一个高性能 LLM 服务框架，由 Stanford、UC Berkeley 等团队开发。它在 vLLM 的基础上做了大量改进，特别是在**调度策略**和**结构化生成**方面有独特优势。

## 🎯 为什么对 AI Infra 重要？

1. **与 vLLM 对比学习** — 理解不同设计选择的 trade-off
2. **RadixAttention** — 一种创新的前缀缓存技术
3. **结构化生成** — 支持 JSON/正则表达式约束的输出
4. **面试加分** — 展示你对推理引擎的广泛了解

## 🧬 架构分析

### 核心目录结构

```
sglang/
├── python/sglang/
│   ├── srt/                 # 🔥 SGLang Runtime (SGLang 的核心)
│   │   ├── server.py             # 服务入口
│   │   ├── manager.py            # 请求管理器
│   │   ├── scheduler.py          # 调度器
│   │   ├── model_executor/       # 模型执行器
│   │   │   ├── layers/           # 各类 Layer
│   │   │   └── models/           # 模型定义
│   │   ├── layers/               # 自定义 Layer
│   │   ├── configs/              # 模型配置
│   │   └── distributed/          # 分布式
│   │
│   ├── lang/                # 🔥 SGLang 编程语言（前端 DSL）
│   │   ├── api.py                # SGLang 编程接口
│   │   └── backend/              # 后端（使用 srt）
│   │
│   ├── kernels/             # 自定义 CUDA/Triton Kernel
│   └── cli/                 # 命令行工具
│
├── rust/                    # Rust 实现的部分组件
├── benchmark/               # 性能测试
└── test/                    # 测试
```

## 🔑 精髓：SGLang 的 4 个核心创新

### 1. RadixAttention（前缀缓存）

**问题：** 多个请求可能共享相同的前缀（如 system prompt），但传统方法会重复计算。

**RadixAttention 的解决方案：**
- 使用 Radix Tree（基数树）管理 KV Cache
- 自动识别共享前缀
- 共享前缀的 KV Cache 只计算一次，后续请求直接复用

**与 vLLM PagedAttention 的关系：**
- PagedAttention 解决的是**内存碎片**问题
- RadixAttention 解决的是**前缀共享**问题
- 两者互补：RadixAttention 基于 PagedAttention 的 Block 管理

**关键文件：**
- `python/sglang/srt/managers/` — 请求管理
- `python/sglang/srt/layers/radix_attention.py` — RadixAttention 实现

**面试考点：** "RadixAttention 和 PagedAttention 的区别？"

### 2. 调度策略

SGLang 的调度器比 vLLM 更灵活：
- 支持多种调度策略（FCFS, Priority, Preemption）
- 支持 prefill 和 decode 的分离调度
- 更精细的资源管理

**关键文件：**
- `python/sglang/srt/scheduler.py`
- `python/sglang/srt/manager.py`

### 3. 结构化生成 (Structured Generation)

**功能：** 强制 LLM 输出符合特定格式（JSON、正则表达式、EBNF 语法）

**实现：**
- 使用有限状态机（FSM）约束 token 生成
- 支持 JSON Schema、正则表达式、上下文无关文法

**关键文件：**
- `python/sglang/srt/constrained/`

**面试考点：** "如何实现 LLM 的结构化输出？"

### 4. SGLang DSL（前端编程语言）

**核心思想：** 提供一种声明式的编程语言来定义 LLM 调用流程

```python
# SGLang 编程示例
@function
def multi_turn_qa(s, question):
    s += system("You are a helpful assistant.")
    s += user(question)
    s += assistant(gen("answer", max_tokens=256))
```

**关键文件：**
- `python/sglang/lang/api.py`

## 📖 推荐学习路径

### Day 1-2：整体架构

1. 阅读 `README.md` — 了解 SGLang 的定位
2. 运行 `examples/` — 体验 SGLang 的基本功能
3. 阅读 `python/sglang/srt/server.py` — 理解服务启动流程
4. 追踪一个请求的完整生命周期

### Day 3-4：RadixAttention

5. 理解 Radix Tree 的数据结构
6. 阅读 RadixAttention 的实现
7. 对比 vLLM 的 PagedAttention
8. 画图：Radix Tree 如何管理共享前缀

### Day 5-7：高级特性

9. 阅读调度器实现
10. 阅读结构化生成实现
11. 阅读 SGLang DSL 设计
12. **动手**：部署 SGLang 并测试性能

## 🎤 面试考点关联

1. **对比：** "SGLang 和 vLLM 的主要区别？"
2. **前缀缓存：** "RadixAttention 的原理？"
3. **调度：** "如何设计推理引擎的调度策略？"
4. **结构化输出：** "如何实现 JSON 格式的输出约束？"
5. **系统设计：** "设计一个支持多轮对话的 LLM 推理服务"

## 💡 学习技巧

1. **对比学习** — 同时看 vLLM 和 SGLang 的源码，理解设计 trade-off
2. **关注 RadixAttention** — 这是 SGLang 最大的创新点
3. **跑 benchmark** — 用 SGLang 和 vLLM 跑同样的模型，对比性能
4. **读论文** — SGLang 的论文 "Efficiently Programming Large Language Models using SGLang"

## 🔗 相关仓库

- [vllm](./vllm.md) — 对比学习
- [mini-sglang](./mini-sglang.md) — 精简版 SGLang
- [flash-attention](./flash-attention.md) — Attention 优化基础
