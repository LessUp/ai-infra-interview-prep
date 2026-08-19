# 🔬 minGPT 学习指南

> **上游：** [karpathy/minGPT](https://github.com/karpathy/minGPT)
> **你的 Fork：** [LessUp/minGPT](https://github.com/LessUp/minGPT)
> **语言：** Python
> **建议学习时间：** 1 天
> **面试重要性：** ⭐⭐

---

## 📌 这个仓库是什么？

Andrej Karpathy 写的 GPT 最小化实现，用于教学目的。用最少的代码展示 GPT 训练的核心原理。

## 🎯 为什么对 AI Infra 重要？

1. **理解 GPT 结构** — 这是推理引擎需要服务的模型
2. **理解训练流程** — 推理引擎需要理解训练产生的模型
3. **代码清晰** — 经典的教学代码

## 🔑 精髓：核心组件

- **Transformer Block** — Multi-Head Attention + FFN
- **GPT Model** — 完整的 GPT 模型定义
- **Training Loop** — 简单的训练循环
- **Generation** — 自回归生成

## 📖 推荐学习路径

1. 阅读 `mingpt/model.py` — 模型定义
2. 阅读 `mingpt/trainer.py` — 训练逻辑
3. 运行训练示例
4. 理解 GPT 生成的过程

## 🔗 相关仓库
- [vllm](./vllm.md) — 推理引擎（服务 GPT 模型）
- [LLM-Workshop](./llm-workshop.md) — 更多 LLM 实战
