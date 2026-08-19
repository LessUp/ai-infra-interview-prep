# 能力基线（BASELINE）

更新日期：2026-08-19。用于校准 SKILL_MATRIX 的"当前等级"，避免高估或低估。

## 已有优势（有可验证证据）

| 能力 | 证据 |
|------|------|
| CUDA 编程与 kernel 优化 | open-infra-ai/cuda-foundations（SGEMM 优化阶梯）、cuflash-attn（FlashAttention 前后向，WMMA，170+ 测试体系的相邻仓）；本机 RTX 3060 Laptop 6GB 可复现 |
| Triton 算子 | open-infra-ai/triton-fused-ops（RMSNorm+RoPE/SwiGLU/FlashAttention/SGEMM + torch.library 注册） |
| LLM 推理引擎 | open-infra-ai/tiny-llm：GGUF 加载、W8A16 量化、分页 KV；TPOT ≈ 6.1 ms/token（本机实测，指标口径见该仓 README/benchmark） |
| 推理调度与控制面 | open-infra-ai/paged-infer（Rust）：分页 KV + continuous batching + HTTP 控制面；3 并发 e2e 与 llama.cpp 对齐（差异已诚实记录） |
| C++ 工程质量 | open-genomics/fq-compressor：C++23、oneTBB、CI、Sanitizer、O(1) 随机访问；fastq-tools 零拷贝 I/O |
| 系统背景 | ZEGO 实时音视频（实时系统）、BGI 基因数据工程、Mindray 医疗影像 |

## 真实短板（当前无证据或未验证）

| 短板 | 现状 | 影响 |
|------|------|------|
| Nsight Systems/Compute 深度使用 | 仅基础使用；无系统性 flame graph / warp stall 分析产出 | Kernel 岗高频考点 |
| Linux 性能调优（perf、内存、NUMA、CPU 频率） | 经验零散，无文档化实验 | Serving 岗考察 |
| NCCL / NVLink / RDMA / Tensor Parallel | 纯理论，无多 GPU 实验（硬件限制） | 分布式话题只能谈原理与源码 |
| 推理服务压测与可观测性 | paged-infer 有基础 HTTP 面，但无系统压测报告（吞吐/尾延迟/容量曲线） | Serving 岗核心证据缺口 |
| torch.compile / PyTorch 内部机制 | 只写过 C++ extension，未深入 dispatch/inductor | 部分岗位必考 |
| 面试表达 | 项目证据充分但未经过有评分的完整模拟面试 | 最后一公里 |
| 算法/笔试 | 长期未系统刷题 | 国内岗位笔试门槛 |

## 环境约束

- 单卡 RTX 3060 Laptop 6GB：FP16 小模型可跑；任何多 GPU、TP/PP 实验均不可行，
  相关内容一律写成"理论学习 + 模拟"，不得声称实测。
