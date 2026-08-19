# 📖 详细学习计划

## 每周时间分配（总计 20-25 小时/周）

| 时间段 | 周一-周五 | 周六 | 周日 |
|--------|-----------|------|------|
| 上午 (2h) | 阅读源码/论文 | 动手实践 | 复习总结 |
| 下午 (2h) | 写代码/笔记 | 项目开发 | 计划下周 |
| 晚上 (1h) | 复习 | 自由探索 | 休息 |

## 课题权重与面试重要性

| 课题 | 总时间 | 面试重要度 | 难度 | 对应仓库 | 备注 |
|------|--------|------------|------|----------|------|
| CUDA/GPU 编程 | 60h | ⭐⭐⭐⭐⭐ | 中高 | cuda-samples, SGEMM_CUDA, cuda-course | 重中之重，面试必考 |
| Flash Attention | 30h | ⭐⭐⭐⭐⭐ | 高 | flash-attention | 高频考点，必须深入理解 |
| LLM 推理引擎 | 30h | ⭐⭐⭐⭐⭐ | 中 | vllm, sglang, TensorRT-LLM | 核心技能，工业界标配 |
| Triton 语言 | 20h | ⭐⭐⭐⭐⭐ | 中 | triton, Triton-Puzzles | 必备技能，面试常考 |
| PyTorch 内部机制 | 20h | ⭐⭐⭐⭐ | 中 | extension-cpp | 基础能力 |
| TensorRT 优化 | 15h | ⭐⭐⭐⭐ | 中高 | TensorRT-LLM | 加分项 |
| TVM/ML 编译器 | 15h | ⭐⭐⭐⭐ | 高 | tvm | 加分项，理解编译器思想 |
| FlashInfer/Kernel | 15h | ⭐⭐⭐⭐ | 高 | flashinfer | 深入 Kernel 实现 |
| 项目实战 | 40h | ⭐⭐⭐⭐ | 中高 | - | 简历亮点 |
| 系统设计 | 20h | ⭐⭐⭐ | 中 | - | 面试必考 |
| C++ 复习 | 10h | ⭐⭐⭐ | 低 | cpp-high-performance-guide | 基础 |

## 每日 Routine

1. **早上 30min** — 阅读 AI Infra 领域最新动态（论文、博客、GitHub trending）
2. **核心学习 2h** — 当日主题的源码阅读或视频学习
3. **动手实践 1.5h** — 写代码、运行示例、调试
4. **笔记整理 30min** — 记录当天学习内容，写博客

## 学习方法论

### 源码阅读技巧
1. **先读 README 和架构文档** — 建立全局认知
2. **从入口函数开始** — 追踪调用链
3. **画图** — 画出模块关系和调用流程
4. **关注核心数据结构** — 数据结构决定了架构
5. **忽略细节** — 第一遍只看主流程，第二遍再看细节

### 知识内化方法
1. **费曼学习法** — 用简单的话解释复杂概念
2. **写博客** — 输出是最好的输入
3. **做 PPT** — 假设你要给别人讲这个主题
4. **面试自问自答** — 模拟面试场景

### 代码实践原则
1. **每个主题至少写一个 Demo**
2. **对比性能** — 优化前后、不同实现
3. **读别人的代码** — 阅读优秀开源项目的代码
4. **Code Review** — 给自己提 PR，自我审查

## 学习资源优先级

### 必读论文（按阅读顺序）
1. "FlashAttention: Fast and Memory-Efficient Exact Attention" (NeurIPS 2022)
2. "Efficient Memory Management for Large Language Model Serving with PagedAttention" (SOSP 2023)
3. "FlashAttention-2: Faster Attention with Better Parallelism" (2023)
4. "FlashAttention-3: Fast and Accurate Attention with Asynchrony and Low-precision" (2024)
5. "TensorRT-LLM: A Flexible and Easy-to-Use Library for Large Language Model Inference" (2024)

### 必读博客
1. [CUDA C++ Programming Guide](https://docs.nvidia.com/cuda/cuda-c-programming-guide/)
2. [Triton Language Documentation](https://triton-lang.org/)
3. [Simon Boehm's CUDA GEMM](https://siboehm.com/articles/22/CUDA-MMM)
4. [Lei Mao's CUDA Notes](https://leimao.github.io/)

### 视频课程
1. GPU Mode 讲座系列（[lectures 仓库](https://github.com/LessUp/lectures)）
2. NVIDIA Deep Learning Institute
3. CUDA Mode YouTube 频道

## 进度追踪

- 每日完成情况在 [progress-tracker.md](./progress-tracker.md) 中记录
- 每周总结在 [weekly/](./weekly/) 目录中
- 学习笔记在 [notes/](./notes/) 目录中
