# 项目策略（PROJECT_STRATEGY）

更新日期：2026-08-19。**不再新建项目，不再有"待定"。** 全部选用已冻结、
有测试与 benchmark 的现有仓库（盘点见 [github-repos-hub](https://github.com/LessUp/github-repos-hub)）。

## 项目 1：推理系统主项目 = open-infra-ai/tiny-llm + paged-infer

- **一句话**：从 GGUF 权重加载到 W8A16 量化推理、分页 KV Cache 与 continuous
  batching 调度、HTTP serving 的端到端推理系统（C++ + Rust）。
- **展示能力**：模型加载与量化、KV Cache 内存管理、调度状态机、端到端验证方法论。
- **关键证据**（口径详见各仓 README 与 aicl-lab 证据包）：
  - tiny-llm：W8A16 端到端可用，TPOT ≈ 6.1 ms/token（本机实测），170 tests，
    分页 KV 与连续 KV 逐 token 差分一致。
  - paged-infer：3 并发分页请求 e2e 与 llama.cpp greedy 对齐（量化差异诚实记录）。
- **12 周内增量**（证据补强，不加新功能）：W6 补 CUDA Graph 对照实验；
  W8 补系统压测报告（TTFT/TPOT/吞吐/p99 尾延迟、容量曲线）。

## 项目 2：Kernel 主项目 = open-infra-ai/cuda-foundations + cuflash-attn + triton-fused-ops

- **一句话**：同一批核心算子（SGEMM、RMSNorm+RoPE、SwiGLU、FlashAttention）的
  CUDA 与 Triton 双实现，含 WMMA、差分测试、benchmark 与 torch.library 集成。
- **展示能力**：CUDA/Triton 编程、算法理解（online softmax、量化）、
  工程化验证（差分测试）、性能对比方法论。
- **关键证据**：cuflash-attn 前后向 FP32/FP16/BF16 + WMMA + 越界修复回归测试；
  triton-fused-ops 与 vLLM/SGLang 相同的 custom op 接入模式。
- **12 周内增量**：W2–W4 补 Nsight Compute 的量化分析报告（当前最大缺口是
  profiling 证据，不是新 kernel）。

## 项目 3：C++ 工程质量辅助 = open-genomics/fq-compressor

- **一句话**：C++23 高性能 FASTQ 压缩（3.97x 压缩比、O(1) 随机访问、oneTBB 并发
  流水线、CI + Sanitizer）。
- **用途**：证明 C++/并发/工程质量；面试谈内存布局、流水线与测试文化。

## 明确不做

- 不再新建两个功能重叠的大项目（原 project-ideas.md 的"迷你推理引擎/KV Cache 管理器"
  想法已被 tiny-llm/paged-infer 覆盖，该文件已归档删除）。
- 不向 vLLM/SGLang 等上游提交 PR 作为计划依赖（若顺路修复 bug 可作为加分项，不计入关键路径）。
- Fork 与 AI 翻译仓库不写入项目经历，只在"学习记录"中提及。

## STAR 条目模板（W10 产出）

每个项目一条 STAR：S 背景 → T 目标与指标口径 → A 我的实现与取舍 → R 量化结果
（硬件/版本/日期/命令）。数字必须能溯源到仓库 benchmark 脚本。
