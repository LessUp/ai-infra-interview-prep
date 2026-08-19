# 💡 项目想法

## 推荐项目（按难度）

### 入门级
1. **用 Triton 实现 Flash Attention** — 理解算法 + 实践 Triton
2. **CUDA GEMM 优化** — 从 naive 到接近 cuBLAS 性能
3. **PyTorch 自定义算子** — 用 CUDA 写一个 LayerNorm 并注册到 PyTorch

### 进阶级
4. **Mini LLM 推理引擎** — 从加载模型权重到生成 token
5. **KV Cache 管理器** — 实现 PagedAttention 的内存管理
6. **简单的 ML 编译器** — 将 ONNX 子图编译为 CUDA Kernel

### 挑战级
7. **给 vLLM 贡献功能** — 修复 bug 或添加新特性
8. **用 Triton 实现 Flash Attention 2** — 完整复现
9. **多 GPU 推理引擎** — 实现 Tensor Parallelism

## 项目选择建议

- 至少完成 1 个入门级 + 1 个进阶级
- 项目代码放在 GitHub 上，写好 README 和 benchmark
- 写博客记录项目过程
