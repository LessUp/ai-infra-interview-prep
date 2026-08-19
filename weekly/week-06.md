# 第 6 周：TensorRT-LLM 与推理优化

> 📅 日期范围：YYYY-MM-DD ~ YYYY-MM-DD
> 🎯 本周目标：理解 TensorRT-LLM 的优化技术

## 学习内容

### 周一：TensorRT-LLM 整体架构
- [ ] 阅读 README + `docs/source/overview.md`
- [ ] 理解 TensorRT-LLM 的生态位置
- [ ] 阅读 `docs/source/developer-guide/overview.md` — PyExecutor 架构
- [ ] **核心概念：** Builder, Network, Runtime, PyExecutor

### 周二：图优化
- [ ] 理解 Layer Fusion 的原理
- [ ] 理解 Constant Folding
- [ ] 理解 Precision Calibration
- [ ] 阅读 `tensorrt_llm/builder.py`
- [ ] **面试题：** "TensorRT 做了哪些图优化？"

### 周三：In-Flight Batching
- [ ] 阅读 `docs/source/features/paged-attention-ifb-scheduler.md`
- [ ] 理解三个容量参数
- [ ] 理解调度可视化
- [ ] 对比 vLLM 的 Continuous Batching
- [ ] **面试题：** "In-Flight Batching 如何实现？"

### 周四：量化技术
- [ ] 阅读 `docs/source/features/quantization.md`
- [ ] 理解 INT8 SmoothQuant
- [ ] 理解 FP8（H100 原生支持）
- [ ] 理解 GPTQ/AWQ
- [ ] **面试题：** "INT8 量化的原理？FP8 的优势？"

### 周五：并行策略
- [ ] 阅读 `docs/source/features/parallel-strategy.md`
- [ ] 理解 TP/PP/DP/EP/CP 六种并行
- [ ] 理解不同并行的适用场景
- [ ] **面试题：** "TP 和 PP 的区别？什么时候用哪种？"

### 周六：动手实践
- [ ] 用 TensorRT-LLM 部署一个模型
- [ ] 运行 `trtllm-bench` 进行性能测试
- [ ] 对比 vLLM 的性能

### 周日：复习与总结
- [ ] 整理本周笔记
- [ ] 完成 progress-tracker 打卡

## 本周总结

### 收获
- 

### 问题
- 

### 下周计划
- 第 7 周：Triton 语言与编译器
