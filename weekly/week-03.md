# 第 3 周：GPU 性能优化基础

> 📅 日期范围：YYYY-MM-DD ~ YYYY-MM-DD
> 🎯 本周目标：掌握 GPU 性能分析工具与方法论，理解 Roofline 模型

## 学习内容

### 周一：Nsight Systems 入门
- [ ] 安装 Nsight Systems
- [ ] 学习 `nsys profile` 的基本用法
- [ ] 分析一个 CUDA 程序的 timeline
- [ ] **核心概念：** Timeline, Kernel Duration, Memory Transfer

### 周二：Nsight Compute 入门
- [ ] 安装 Nsight Compute
- [ ] 学习 `ncu` 的基本用法
- [ ] 分析一个 Kernel 的详细性能指标
- [ ] **核心概念：** Occupancy, Memory Throughput, Compute Throughput, Roofline

### 周三：Roofline 模型
- [ ] 理解 Roofline 模型的理论
- [ ] 画出你的 GPU 的 Roofline 图
- [ ] 分析你的 Kernel 在 Roofline 上的位置
- [ ] **面试题：** "什么是 Roofline 模型？如何用它分析性能？"

### 周四：内存带宽优化
- [ ] 分析矩阵乘法的内存访问模式
- [ ] 理解 Arithmetic Intensity（算术强度）
- [ ] 优化 Kernel 的内存访问
- [ ] **核心概念：** Memory Bound vs Compute Bound

### 周五：Occupancy 与 Latency Hiding
- [ ] 理解 Occupancy 的概念
- [ ] 理解 Warp 调度和 Latency Hiding
- [ ] 用 `ncu` 分析 Occupancy
- [ ] **面试题：** "什么是 Occupancy？如何提升 Occupancy？"

### 周六：动手实践 — 性能分析
- [ ] 选择你之前写的一个 Kernel
- [ ] 用 `nsys` 和 `ncu` 进行完整分析
- [ ] 找出性能瓶颈
- [ ] 优化并对比前后性能

### 周日：复习与总结
- [ ] 整理本周笔记
- [ ] 完成 progress-tracker 打卡

## 本周总结

### 收获
- 

### 问题
- 

### 下周计划
- 第 4 周：Flash Attention 原理
