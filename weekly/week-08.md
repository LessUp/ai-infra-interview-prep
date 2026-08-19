# 第 8 周：ML 编译器 (TVM)

> 📅 日期范围：YYYY-MM-DD ~ YYYY-MM-DD
> 🎯 本周目标：理解 ML 编译器的工作原理

## 学习内容

### 周一：TVM 整体架构
- [ ] 阅读 TVM 官方文档 Quick Start
- [ ] 理解 TVM 的 4 层抽象（Relay → TE → Schedule → Codegen）
- [ ] 运行一个简单的 TVM 编译示例
- [ ] **核心概念：** IR, Pass, Schedule, Codegen

### 周二：Tensor Expression
- [ ] 学习用 TE 定义算子
- [ ] 定义矩阵乘法、卷积等常见算子
- [ ] 理解 `te.placeholder`, `te.compute`, `te.reduce_axis`
- [ ] **动手：** 用 TE 定义 LayerNorm

### 周三：调度原语
- [ ] 学习 `split`, `fuse`, `reorder` — 基本循环变换
- [ ] 学习 `tile` — Tiling 是优化的核心
- [ ] 学习 `cache_read/cache_write` — 添加共享内存
- [ ] 学习 `bind` — 绑定到 GPU 线程
- [ ] **面试题：** "TVM 的调度原语有哪些？"

### 周四：自动调优
- [ ] 理解 AutoTVM 的工作原理（模板 + 搜索）
- [ ] 理解 AutoScheduler（无模板的自动搜索）
- [ ] 运行自动调优示例
- [ ] **面试题：** "AutoTVM 和 AutoScheduler 的区别？"

### 周五：代码生成
- [ ] 理解 TVM 如何生成 CUDA 代码
- [ ] 阅读 `src/target/cuda/` — CUDA 代码生成
- [ ] 对比 TVM 生成的代码和手写 CUDA
- [ ] **面试题：** "ML 编译器如何生成高效的 GPU 代码？"

### 周六：动手实践
- [ ] 用 TVM 编译一个完整的模型（如 ResNet）
- [ ] 对比 PyTorch 原生模型的性能
- [ ] 尝试不同的调度策略

### 周日：复习与总结
- [ ] 整理本周笔记
- [ ] 完成 progress-tracker 打卡

## 本周总结

### 收获
- 

### 问题
- 

### 下周计划
- 第 9 周：FlashInfer 与自定义 Kernel
