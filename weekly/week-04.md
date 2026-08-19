# 第 4 周：Flash Attention 原理

> 📅 日期范围：YYYY-MM-DD ~ YYYY-MM-DD
> 🎯 本周目标：深入理解 Flash Attention 的算法原理与实现

## 学习内容

### 周一：Attention 基础回顾
- [ ] 复习标准 Attention 的计算流程
- [ ] 计算 Attention 的内存访问量（HBM reads/writes）
- [ ] 理解标准 Attention 的内存瓶颈
- [ ] **核心公式：** O = softmax(QK^T/√d)V

### 周二：Flash Attention 算法（一）
- [ ] 阅读 Flash Attention 论文 Section 1-3
- [ ] 理解 Tiling 策略
- [ ] 理解 Online Softmax 的数学推导
- [ ] **面试题：** "Flash Attention 为什么比标准 Attention 快？"

### 周三：Flash Attention 算法（二）
- [ ] 阅读 `flash_attn/flash_attn_triton.py` — Triton 实现
- [ ] 理解 Forward Pass 的完整流程
- [ ] 理解 Backward Pass 的 Recomputation 策略
- [ ] **面试题：** "Flash Attention 如何减少内存访问？"

### 周四：Flash Attention 2
- [ ] 阅读 Flash Attention 2 论文
- [ ] 理解改进点：减少非 matmul FLOPs
- [ ] 理解更好的并行策略
- [ ] **面试题：** "Flash Attention 2 相比 1 做了哪些改进？"

### 周五：Flash Attention 3
- [ ] 阅读 Flash Attention 3 论文/博客
- [ ] 理解 Hopper 架构的新特性（TMA, FP8）
- [ ] 理解异步执行和低精度
- [ ] **面试题：** "Flash Attention 3 利用了 Hopper 架构的哪些特性？"

### 周六：动手实践
- [ ] 用 Triton 实现一个简化版 Flash Attention
- [ ] 对比标准 Attention 的性能
- [ ] 用 `ncu` 分析你的实现

### 周日：复习与总结
- [ ] 整理本周笔记
- [ ] 完成 progress-tracker 打卡

## 本周总结

### 收获
- 

### 问题
- 

### 下周计划
- 第 5 周：LLM 推理引擎 (vLLM / SGLang)
