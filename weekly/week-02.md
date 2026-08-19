# 第 2 周：PyTorch 内部机制与 C++ 扩展

> 📅 日期范围：YYYY-MM-DD ~ YYYY-MM-DD
> 🎯 本周目标：理解 PyTorch 的 C++ 后端，能写自定义 CUDA 算子

## 学习内容

### 周一：PyTorch 架构概览
- [ ] 阅读 PyTorch 官方博客 "A Tour of PyTorch Internals"
- [ ] 理解 PyTorch 的分层架构：Python → C++ (ATen) → CUDA
- [ ] 理解 Tensor 的存储结构（Storage, Stride, Layout）
- [ ] **核心概念：** ATen, Autograd, Dispatch, Backend

### 周二：C++ Extension 基础
- [ ] 运行 `extension-cpp` 中的 C++ 扩展示例
- [ ] 理解 `setup.py` + `CUDAExtension` 的配置
- [ ] 理解 PyBind11 的基本用法
- [ ] 写一个简单的 C++ 算子（如 element-wise add）

### 周三：CUDA Extension
- [ ] 运行 `extension-cpp` 中的 CUDA 扩展示例
- [ ] 理解 `.cu` 文件和 `.cpp` 文件的组织
- [ ] 写一个 CUDA 算子（如 vector add）
- [ ] **核心概念：** kernel launch, grid/block 配置, 错误处理

### 周四：Autograd 与自定义 Function
- [ ] 理解 PyTorch 的 Autograd 机制
- [ ] 实现 `torch.autograd.Function` 的 forward 和 backward
- [ ] 为你的 CUDA 算子添加反向传播
- [ ] **面试题：** "PyTorch 的 Autograd 是如何工作的？"

### 周五：Dispatch 机制
- [ ] 理解 PyTorch 的 dispatch 机制
- [ ] 理解 `TORCH_LIBRARY` 和 `TORCH_LIBRARY_IMPL`
- [ ] 注册你的算子到 PyTorch
- [ ] **核心概念：** Dispatcher, Kernel, Dispatch Key

### 周六：动手实践 — 实现 LayerNorm
- [ ] 用 CUDA 实现 LayerNorm 的前向传播
- [ ] 实现反向传播
- [ ] 注册到 PyTorch
- [ ] 对比 PyTorch 原生 LayerNorm 的性能

### 周日：复习与总结
- [ ] 整理本周笔记
- [ ] 完成 progress-tracker 打卡
- [ ] 列出本周遇到的问题

## 本周总结

### 收获
- 

### 问题
- 

### 下周计划
- 第 3 周：GPU 性能优化基础
