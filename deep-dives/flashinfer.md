# 🔬 FlashInfer 深度学习指南

> **上游：** [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)
> **你的 Fork：** [LessUp/flashinfer](https://github.com/LessUp/flashinfer)
> **语言：** Python / CUDA
> **建议学习时间：** 1 周
> **面试重要性：** ⭐⭐⭐⭐

---

## 📌 这个仓库是什么？

FlashInfer 是一个专门为 LLM 推理优化的 **Kernel 库**，由 FlashInfer AI 团队开发。它提供了 LLM 推理中最常用的高性能 Kernel 实现，被 vLLM、SGLang 等主流推理引擎集成。

## 🎯 为什么对 AI Infra 重要？

1. **理解 LLM 推理 Kernel** — 这是理解推理引擎底层的基础
2. **高性能实现参考** — 学习如何写出接近硬件极限的 Kernel
3. **与 vLLM/SGLang 配套** — 理解推理引擎如何调用底层 Kernel

## 🔑 精髓：核心 Kernel 类型

### 1. Attention Kernel
- **Flash Attention** — 标准 Flash Attention
- **Paged Attention** — 支持 PagedAttention 的 Attention Kernel
- **Prefill/Decode Attention** — 针对不同阶段的优化

### 2. 采样 Kernel
- Top-K / Top-P 采样
- 拒绝采样
- 惩罚（Frequency / Presence Penalty）

### 3. 量化 Kernel
- INT8/FP8 量化
- 反量化

### 4. 辅助 Kernel
- LayerNorm / RMSNorm
- Rotary Embedding (RoPE)
- Activation 函数

## 📖 推荐学习路径

1. 阅读 README，了解提供的 Kernel 类型
2. 阅读 Attention Kernel 实现（核心）
3. 阅读 PagedAttention 相关 Kernel
4. 对比 vLLM 的 Kernel 实现
5. **动手**：尝试为 FlashInfer 添加一个新的 Kernel

## 🎤 面试考点

1. "LLM 推理中哪些 Kernel 最关键？"
2. "PagedAttention 的 Kernel 如何实现？"
3. "如何优化 Attention Kernel？"

## 🔗 相关仓库
- [vllm](./vllm.md) — 使用 FlashInfer 的推理引擎
- [flash-attention](./flash-attention.md) — Attention 优化基础
