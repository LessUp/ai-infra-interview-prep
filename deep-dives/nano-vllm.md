# 🔬 Nano vLLM 学习指南

> **上游：** [GeeeekExplorer/nano-vllm](https://github.com/GeeeekExplorer/nano-vllm)
> **你的 Fork：** [LessUp/nano-vllm](https://github.com/LessUp/nano-vllm)
> **语言：** Python
> **建议学习时间：** 2 天
> **面试重要性：** ⭐⭐⭐

---

## 📌 这个仓库是什么？

vLLM 的最小化实现，用最少的代码展示 vLLM 的核心架构。

## 🎯 为什么对 AI Infra 重要？

1. **快速理解 vLLM** — 代码量少，容易理解核心思想
2. **学习 PagedAttention** — 简化的实现
3. **入门推理引擎** — 最好的起点

## 🔑 精髓：核心组件

- **PagedAttention 简化版** — 理解 Block Table 和 KV Cache 管理
- **Continuous Batching 简化版** — 理解动态批处理
- **调度器简化版** — 理解基本的调度逻辑

## 📖 推荐学习路径

1. 阅读完整代码
2. 理解 PagedAttention 的实现
3. 对比完整版 vLLM
4. **动手**：基于 nano-vllm 添加 GPU 支持

## 🔗 相关仓库
- [vllm](./vllm.md) — 完整版 vLLM
- [mini-sglang](./mini-sglang.md) — 另一个精简版推理引擎
