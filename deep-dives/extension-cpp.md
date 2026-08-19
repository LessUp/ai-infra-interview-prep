# 🔬 PyTorch C++ Extension 学习指南

> **上游：** [pytorch/extension-cpp](https://github.com/pytorch/extension-cpp)
> **你的 Fork：** [LessUp/extension-cpp](https://github.com/LessUp/extension-cpp)
> **语言：** Python / C++ / CUDA
> **建议学习时间：** 3 天
> **面试重要性：** ⭐⭐⭐⭐

---

## 📌 这个仓库是什么？

PyTorch 官方提供的 C++ 扩展教程，教你如何用 C++/CUDA 编写自定义算子并注册到 PyTorch 中。

## 🎯 为什么对 AI Infra 重要？

1. **自定义算子** — AI Infra 工程师的核心工作之一
2. **PyTorch 内部理解** — 理解 PyTorch 的 dispatch 机制
3. **面试必考** — "如何为 PyTorch 写一个自定义算子？"

## 🔑 精髓：3 个核心知识点

### 1. ATen 库
- PyTorch 的 C++ Tensor 库
- 提供了与 Python 相同的 Tensor 操作
- 关键文件：`aten/src/ATen/`

### 2. C++ Extension 编写流程
```cpp
// 1. 定义算子
torch::Tensor my_op(torch::Tensor input) {
    return input * 2;
}

// 2. 注册算子
TORCH_LIBRARY(my_ops, m) {
    m.def("my_op", my_op);
}

// 3. Python 调用
import torch; torch.ops.my_ops.my_op(x)
```

### 3. CUDA Extension
- 用 CUDA 写 Kernel
- 通过 PyBind11 绑定到 Python
- 关键：`setup.py` 中的 `CUDAExtension`

## 📖 推荐学习路径

1. 运行 `extension-cpp` 中的示例
2. 理解 `setup.py` 的配置
3. 写一个简单的 CUDA 算子（如 LayerNorm）
4. 理解 PyTorch 的 dispatch 机制

## 🎤 面试考点

1. "如何为 PyTorch 写一个自定义 CUDA 算子？"
2. "PyTorch 的 dispatch 机制是怎样的？"
3. "ATen 和 c10 的区别？"

## 🔗 相关仓库
- [cuda-samples](./cuda-samples.md) — CUDA 编程基础
