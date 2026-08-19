# 🔬 LightLLM 学习指南

> **上游：** [ModelTC/LightLLM](https://github.com/ModelTC/LightLLM)
> **你的 Fork：** [LessUp/LightLLM](https://github.com/LessUp/LightLLM)
> **语言：** Python
> **建议学习时间：** 3 天
> **面试重要性：** ⭐⭐⭐

---

## 📌 这个仓库是什么？

LightLLM 是一个轻量级的 LLM 推理框架，设计简洁、易扩展。它提供了与 vLLM/SGLang 不同的设计选择，适合对比学习。

## 🎯 为什么对 AI Infra 重要？

1. **理解不同的设计选择** — 对比 vLLM/SGLang
2. **轻量级代码** — 比 vLLM 更容易理解
3. **学习推理引擎的完整实现**

## 🔑 精髓：与 vLLM 的对比

| 特性 | vLLM | LightLLM |
|------|------|----------|
| KV Cache | PagedAttention | 自有实现 |
| 调度 | Continuous Batching | 自有策略 |
| 代码量 | 大（~30 万行） | 较小 |
| 易读性 | 中 | 较高 |

## 📖 推荐学习路径

1. 阅读架构文档
2. 理解请求处理流程
3. 对比 vLLM 的实现
4. 理解其设计选择的原因

## 🔗 相关仓库
- [vllm](./vllm.md) — 对比学习
- [sglang](./sglang.md) — 对比学习
