# 🔬 Mini SGLang 学习指南

> **上游：** [sgl-project/mini-sglang](https://github.com/sgl-project/mini-sglang)
> **你的 Fork：** [LessUp/mini-sglang](https://github.com/LessUp/mini-sglang)
> **语言：** Python
> **建议学习时间：** 2 天
> **面试重要性：** ⭐⭐⭐

---

## 📌 这个仓库是什么？

SGLang 的精简实现，旨在解开 LLM 服务系统的复杂性。通过最少的代码展示推理引擎的核心原理。

## 🎯 为什么对 AI Infra 重要？

1. **快速理解推理引擎** — 代码量少，容易理解
2. **学习核心架构** — 去掉优化细节，保留核心逻辑
3. **入门 SGLang** — 先看 mini 版再看完整版

## 🔑 精髓：核心组件

- **请求管理** — 如何接收和排队请求
- **KV Cache** — 简化的 KV Cache 管理
- **调度器** — 简化的调度策略
- **模型执行** — 简化的推理流程

## 📖 推荐学习路径

1. 阅读完整代码（约几千行）
2. 理解请求的完整生命周期
3. 对比完整版 SGLang
4. **动手**：基于 mini-sglang 添加一个特性

## 🔗 相关仓库
- [sglang](./sglang.md) — 完整版 SGLang
- [nano-vllm](./nano-vllm.md) — 另一个精简版推理引擎
