# 第 5 周：LLM 推理引擎 (vLLM / SGLang)

> 📅 日期范围：YYYY-MM-DD ~ YYYY-MM-DD
> 🎯 本周目标：理解 LLM 推理引擎的核心架构与优化技术

## 学习内容

### 周一：vLLM 整体架构
- [ ] 阅读 vLLM 论文 + README
- [ ] 运行 `vllm/examples/offline_inference.py` — 跑一个最简单的推理
- [ ] 阅读 `vllm/engine/llm_engine.py` — 理解引擎的整体流程
- [ ] 追踪一个请求的完整生命周期
- [ ] **核心概念：** LLM Engine, Request, Generation

### 周二：PagedAttention（核心！）
- [ ] 阅读 PagedAttention 论文
- [ ] 阅读 `vllm/model_executor/layers/attention.py`
- [ ] 理解 Block Table 和 KV Cache 管理
- [ ] 画图：Block Table 的结构和映射关系
- [ ] **面试题：** "PagedAttention 的原理？为什么能提升吞吐量？"

### 周三：Continuous Batching
- [ ] 阅读 `vllm/model_executor/scheduler.py` — 理解调度逻辑
- [ ] 理解 prefill 和 decode 阶段的区别
- [ ] 理解动态加入和移除请求的机制
- [ ] **面试题：** "Continuous Batching 和 Static Batching 的区别？"

### 周四：SGLang 对比学习
- [ ] 阅读 SGLang 论文 + README
- [ ] 运行 SGLang 的示例
- [ ] 理解 RadixAttention 的原理
- [ ] 对比 vLLM 和 SGLang 的设计差异
- [ ] **面试题：** "SGLang 和 vLLM 的主要区别？"

### 周五：mini 版本辅助理解
- [ ] 阅读 `nano-vllm` 的完整代码
- [ ] 阅读 `mini-sglang` 的完整代码
- [ ] 理解精简版如何展示核心架构
- [ ] 对比完整版和精简版

### 周六：动手实践
- [ ] 部署 vLLM 或 SGLang
- [ ] 用 benchmark 测试在不同 batch size 下的吞吐量
- [ ] 观察 KV Cache 的使用情况

### 周日：复习与总结
- [ ] 整理本周笔记
- [ ] 完成 progress-tracker 打卡

## 本周总结

### 收获
- 

### 问题
- 

### 下周计划
- 第 6 周：TensorRT-LLM 与推理优化
