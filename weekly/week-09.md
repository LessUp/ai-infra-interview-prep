# 第 9 周：FlashInfer 与自定义 Kernel

> 📅 日期范围：YYYY-MM-DD ~ YYYY-MM-DD
> 🎯 本周目标：理解 LLM 推理中的核心 Kernel 实现

## 学习内容

### 周一：FlashInfer 整体架构
- [ ] 阅读 FlashInfer README
- [ ] 理解 FlashInfer 提供的 Kernel 类型
- [ ] 理解 FlashInfer 与 vLLM/SGLang 的关系
- [ ] **核心概念：** Attention Kernel, Sampling Kernel, Quantization Kernel

### 周二：Attention Kernel
- [ ] 阅读 FlashInfer 的 Attention Kernel 实现
- [ ] 理解 PagedAttention 的 Kernel 实现
- [ ] 理解 Prefill 和 Decode 的不同优化策略
- [ ] **面试题：** "PagedAttention 的 Kernel 如何实现？"

### 周三：采样 Kernel
- [ ] 阅读 Top-K / Top-P 采样 Kernel
- [ ] 理解拒绝采样
- [ ] 理解惩罚（Frequency / Presence Penalty）
- [ ] **面试题：** "GPU 上如何实现高效的采样？"

### 周四：辅助 Kernel
- [ ] 阅读 LayerNorm / RMSNorm Kernel
- [ ] 阅读 Rotary Embedding (RoPE) Kernel
- [ ] 阅读 Activation 函数 Kernel
- [ ] **面试题：** "如何优化 LayerNorm Kernel？"

### 周五：Kernel 优化技巧
- [ ] 学习 FlashInfer 中的优化技巧
- [ ] 理解 Warp Specialization
- [ ] 理解 Persistent Kernel
- [ ] 理解 Cooperative Groups

### 周六：动手实践
- [ ] 为 FlashInfer 贡献一个简单的 Kernel
- [ ] 或者写一个自己的 LLM 推理 Kernel
- [ ] 用 `ncu` 分析性能

### 周日：复习与总结
- [ ] 整理本周笔记
- [ ] 完成 progress-tracker 打卡

## 本周总结

### 收获
- 

### 问题
- 

### 下周计划
- 第 10 周：个人项目
