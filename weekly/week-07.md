# 第 7 周：Triton 语言与编译器

> 📅 日期范围：YYYY-MM-DD ~ YYYY-MM-DD
> 🎯 本周目标：能用 Triton 写高性能 Kernel

## 学习内容

### 周一：Triton 编程模型
- [ ] 阅读 Triton 官方文档
- [ ] 运行 `tutorials/01-vector-add.py` — 第一个 Triton 程序
- [ ] 理解 Block-based 编程模型
- [ ] **核心概念：** `tl.program_id`, `tl.load`, `tl.store`, `tl.arange`

### 周二：Triton 基础算子
- [ ] 运行 `tutorials/02-fused-softmax.py` — 理解算子融合
- [ ] 运行 `tutorials/04-low-memory-dropout.py`
- [ ] 运行 `tutorials/05-layer-norm.py`
- [ ] **动手：** 用 Triton 写一个 LayerNorm

### 周三：矩阵乘法
- [ ] 运行 `tutorials/03-matrix-multiplication.py` — 核心教程
- [ ] 理解 Tiling 参数的选择
- [ ] 理解 `tl.dot` 和 Tensor Core
- [ ] **动手：** 自己写一个矩阵乘法 Kernel

### 周四：Flash Attention in Triton
- [ ] 运行 `tutorials/06-fused-attention.py`
- [ ] 理解 Triton 如何实现 Flash Attention
- [ ] 对比 CUDA 实现的差异
- [ ] **面试题：** "用 Triton 实现 Flash Attention 的关键步骤？"

### 周五：Triton-Puzzles
- [ ] 完成 Puzzle 1-8（基础到中级）
- [ ] 理解每个 Puzzle 对应的 GPU 编程模式
- [ ] 对比你的解法和参考答案

### 周六：动手实践
- [ ] 用 Triton 实现一个完整的 Flash Attention Forward
- [ ] 用 `ncu` 分析性能
- [ ] 对比 `flash_attn_triton.py` 的实现

### 周日：复习与总结
- [ ] 整理本周笔记
- [ ] 完成 progress-tracker 打卡

## 本周总结

### 收获
- 

### 问题
- 

### 下周计划
- 第 8 周：ML 编译器 (TVM)
