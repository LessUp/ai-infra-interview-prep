# 🔬 TensorRT-LLM 深度学习指南

> **上游：** [NVIDIA/TensorRT-LLM](https://github.com/NVIDIA/TensorRT-LLM)
> **你的 Fork：** [LessUp/TensorRT-LLM](https://github.com/LessUp/TensorRT-LLM)
> **语言：** Python / C++
> **建议学习时间：** 1.5 周
> **面试重要性：** ⭐⭐⭐⭐

---

## 📌 这个仓库是什么？

TensorRT-LLM 是 NVIDIA 官方推出的 LLM 推理优化框架，基于 TensorRT 深度学习推理引擎构建。它提供了：
- 图级别的优化（算子融合、常量折叠）
- 量化支持（INT8/FP8/INT4）
- 多种并行策略（TP/PP/DP/EP）
- 先进的调度算法（In-Flight Batching）

## 🎯 为什么对 AI Infra 重要？

1. **NVIDIA 官方出品** — 代表了 NVIDIA GPU 上的最佳推理实践
2. **工业级优化** — 理解图优化、量化、并行等核心技术
3. **与 vLLM 互补** — vLLM 侧重调度，TensorRT-LLM 侧重算子优化
4. **面试加分** — 展示你对 NVIDIA 生态的了解

## 🧬 架构分析

### 核心目录结构

```
TensorRT-LLM/
├── tensorrt_llm/           # 🔥 Python 核心
│   ├── builder.py              # 模型构建器（图优化）
│   ├── network.py              # 网络定义
│   ├── functional.py           # 函数式 API（类似 PyTorch nn.functional）
│   ├── module.py               # 模块定义
│   ├── models/                 # 预定义模型（GPT, LLaMA, BLOOM 等）
│   ├── layers/                 # 预定义 Layer
│   ├── quantization/           # 量化支持
│   │   ├── functional.py       # 量化算子
│   │   └── mode.py             # 量化模式
│   ├── runtime/                # 运行时
│   │   ├── generation.py       # 生成逻辑
│   │   └── model_runner.py     # 模型运行器
│   └── plugin/                 # 自定义插件
│
├── cpp/                     # 🔥 C++ 核心
│   ├── tensorrt_llm/           # C++ 运行时
│   │   ├── batch_manager/      # 批处理管理
│   │   │   ├── capacityScheduler.cpp    # 调度器
│   │   │   ├── kvCacheManager.cpp       # KV Cache 管理
│   │   │   └── kv_cache_manager_v2/     # V2 KV Cache 管理器
│   │   ├── plugins/            # 自定义插件
│   │   └── runtime/            # 运行时
│   └── kernels/                # CUDA Kernel
│
├── triton_backend/          # Triton Inference Server 集成
├── triton_kernels/           # Triton 语言 Kernel
├── examples/                # 示例（包含模型部署完整流程）
└── docs/                    # 文档
```

## 🔑 精髓：TensorRT-LLM 的 5 个核心特性

### 1. 图优化 (Graph Optimization)

**核心优化技术：**
- **Layer Fusion** — 将多个 Layer 融合为一个（如 Attention + LayerNorm）
- **Constant Folding** — 编译时计算常量
- **Dead Code Elimination** — 移除无用代码
- **Precision Calibration** — 自动选择最优精度

**关键文件：**
- `tensorrt_llm/builder.py`
- `tensorrt_llm/functional.py`

### 2. In-Flight Batching

**与 vLLM 的 Continuous Batching 类似：**
- 动态加入新请求
- 完成的请求立即释放资源
- 最大化 GPU 利用率

**关键文件：**
- `cpp/tensorrt_llm/batch_manager/capacityScheduler.cpp`
- `docs/source/features/paged-attention-ifb-scheduler.md`

### 3. 量化 (Quantization)

**支持的量化方法：**
- INT8 SmoothQuant
- INT4/Float4 GPTQ / AWQ
- FP8（H100 原生支持）
- Weight-only 量化

**关键文件：**
- `tensorrt_llm/quantization/`

### 4. 并行策略

**支持的并行：**
- Tensor Parallelism (TP)
- Pipeline Parallelism (PP)
- Data Parallelism (DP)
- Expert Parallelism (EP) — MoE 模型
- Context Parallelism (CP) — 长序列

**关键文件：**
- `docs/source/features/parallel-strategy.md`

### 5. 分离式服务 (Disaggregated Serving)

**核心思想：** 将 Prefill 和 Decode 分配到不同的 GPU 上
- Prefill GPU：计算密集型，适合高算力 GPU
- Decode GPU：内存密集型，适合大显存 GPU
- 通过 KV Cache 传输连接两者

**关键文件：**
- `docs/source/features/disagg-serving.md`
- `cpp/tensorrt_llm/batch_manager/kvCacheTransferManager.cpp`

## 📖 推荐学习路径

### Day 1-3：整体认识

1. 阅读 `README.md` — 了解项目全貌
2. 阅读 `docs/source/overview.md` — 核心能力清单
3. 阅读 `docs/source/quick-start-guide.md` — 在线服务 vs 离线推理
4. 阅读 `docs/source/developer-guide/overview.md` — PyExecutor 架构

### Day 4-6：核心机制

5. 阅读 `docs/source/features/kvcache.md` — KV Cache 原理
6. 阅读 `docs/source/features/paged-attention-ifb-scheduler.md` — **核心中的核心**
7. 阅读 `docs/source/features/attention.md` — 注意力后端
8. 阅读 `docs/source/features/overlap-scheduler.md` — CPU/GPU 重叠

### Day 7-9：性能与扩展

9. 阅读 `docs/source/features/parallel-strategy.md` — 六种并行
10. 阅读 `docs/source/features/quantization.md` — 量化支持
11. 阅读 `docs/source/features/speculative-decoding.md` — 投机解码
12. 阅读 `docs/source/developer-guide/perf-overview.md` — 性能指标

### Day 10-12：源码深入

13. 阅读 `tensorrt_llm/builder.py` — 理解图优化
14. 阅读 `cpp/tensorrt_llm/batch_manager/capacityScheduler.cpp` — 调度器
15. 阅读 `cpp/tensorrt_llm/batch_manager/kvCacheManager.cpp` — KV Cache 管理

## 🎤 面试考点关联

1. **图优化：** "TensorRT 做了哪些图优化？"
2. **量化：** "INT8 量化的原理？FP8 的优势？"
3. **并行：** "TP 和 PP 的区别？什么时候用哪种？"
4. **调度：** "In-Flight Batching 如何实现？"
5. **性能：** "如何评估 LLM 推理的性能？"

## 💡 学习技巧

1. **注意仓库中已有中文文档** — TensorRT-LLM 已经翻译了 25 篇核心文档，包含 220+ 处 "AI Infra 视角" 讲解块
2. **按阶段顺序读** — 中文文档已按 5 个阶段组织
3. **关注讲解块** — `💡 AI Infra 视角` 块总结了面试考点
4. **对照 C++ 源码** — 理解 Python API 背后的 C++ 实现

## 🔗 相关仓库

- [vllm](./vllm.md) — 对比学习推理引擎设计
- [sglang](./sglang.md) — 另一个推理框架
- [cuda-samples](./cuda-samples.md) — CUDA 基础
