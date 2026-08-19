# 🎤 面试准备

## 常见面试题

### CUDA / GPU 编程
1. 解释 CUDA 的线程层次结构（Thread, Warp, Block, Grid）
2. 什么是 Warp Divergence？如何避免？
3. 共享内存的 Bank Conflict 是什么？如何解决？
4. 如何优化一个矩阵乘法 Kernel？
5. 什么是 Coalesced Memory Access？
6. 解释 Occupancy 的概念及其对性能的影响
7. 如何隐藏内存延迟？
8. Tensor Core 是什么？如何使用？

### Flash Attention
1. 标准 Attention 的内存瓶颈是什么？
2. Flash Attention 如何通过 Tiling 减少内存访问？
3. 解释 Online Softmax 的原理
4. Flash Attention 2 相比 1 做了哪些改进？
5. 为什么 Flash Attention 在长序列上优势更大？

### LLM 推理
1. 什么是 KV Cache？为什么需要它？
2. 解释 PagedAttention 的原理
3. Continuous Batching 与 Static Batching 的区别？
4. Prefill 阶段和 Decode 阶段的计算特点有何不同？
5. 如何评估 LLM 推理系统的性能？（TTFT, TPOT, Throughput）
6. 模型量化有哪些方法？各自优缺点？
7. Tensor Parallelism 和 Pipeline Parallelism 的区别？

### Triton
1. Triton 的编程模型与 CUDA 有何不同？
2. 用 Triton 写一个矩阵乘法 Kernel
3. Triton 编译器做了哪些优化？

### 系统设计
1. 设计一个支持 1000 QPS 的 LLM 推理服务
2. 设计一个分布式训练框架
3. 如何设计一个支持多种 GPU 后端的 ML 编译器？

## 模拟面试计划

| 周次 | 主题 | 方式 |
|------|------|------|
| 第 4 周 | CUDA + Flash Attention | 自问自答 |
| 第 8 周 | 推理引擎 + Triton | 结对面试 |
| 第 10 周 | 系统设计 | 模拟面试 |
| 第 12 周 | 全面模拟 | 真实面试 |
