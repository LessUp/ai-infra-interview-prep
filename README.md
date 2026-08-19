# 🎯 AI Infra Interview Prep

> 12 周 AI Infra 转行准备：目标岗位、能力矩阵、周计划、面试与求职执行。
> **执行周期：2026-08-24 ～ 2026-11-15**（默认 24h/周，附 12h/18h 缩放档）。

## 定位与职责边界

- 本仓库：转行计划、学习 TODO、能力矩阵、项目策略、面试与投递执行。
- 仓库盘点/分类/深读：[github-repos-hub](https://github.com/LessUp/github-repos-hub)
  （deep-dives 唯一事实来源，本仓库不再保留副本）。
- 技术证据与项目讲述：[open-infra-ai/aicl-lab](https://github.com/open-infra-ai/aicl-lab)。
- Star 资源：[stars-index](https://github.com/LessUp/stars-index)。

## 文档地图

| 文档 | 内容 |
|------|------|
| [TARGET_ROLES.md](TARGET_ROLES.md) | 主/次/可选岗位方向与边界 |
| [JOB_MARKET_EVIDENCE.md](JOB_MARKET_EVIDENCE.md) | 2026-08-19 采样的 23 个岗位与技能频次 |
| [BASELINE.md](BASELINE.md) | 已有优势与真实短板 |
| [SKILL_MATRIX.md](SKILL_MATRIX.md) | 能力等级、目标、证据、差距行动 |
| [TOPIC_WEIGHTS.md](TOPIC_WEIGHTS.md) | 时间权重（合计 288h，可核对）与三档缩放 |
| [ROADMAP.md](ROADMAP.md) | 12 周主线与每周必须交付 |
| [study-plan.md](study-plan.md) | 每周节奏与执行方法 |
| [PROJECT_STRATEGY.md](PROJECT_STRATEGY.md) | 已定项目（推理系统 / Kernel / C++ 辅助） |
| [INTERVIEW_MATRIX.md](INTERVIEW_MATRIX.md) | 面试题五要素矩阵 |
| [APPLICATION_PLAN.md](APPLICATION_PLAN.md) | 简历版本、投递节奏、迭代规则 |
| [weekly/](weekly/) | 逐周文件（目标/预算/阅读/实验/交付/退出条件） |
| [progress-tracker.md](progress-tracker.md) | 进度打卡 |
| [interview-prep.md](interview-prep.md) / [knowledge-map.md](knowledge-map.md) / [resources.md](resources.md) | 主题知识索引与资源 |

## 核心事实（2026-08-19 审计）

- 目标：GPU Kernel / LLM Inference Performance Engineer（主）、Serving（次）、编译器（可选）。
- 项目已定：tiny-llm + paged-infer（推理）、cuda-foundations + cuflash-attn + triton-fused-ops（Kernel）、
  fq-compressor（C++ 辅助）。**没有"待定"项目，不新建仓库。**
- P2 大仓（vllm/sglang/TensorRT-LLM/triton/flashinfer/flash-attention/LightLLM）只做
  "五个一"目标导向阅读，不做全仓通读。
- 多 GPU 相关内容一律标注理论学习，不伪造实验数据。

## 快速开始

1. 从 [weekly/week-01.md](weekly/week-01.md) 开始执行。
2. 每周日在 [progress-tracker.md](progress-tracker.md) 打卡并更新 SKILL_MATRIX 自评。
3. 每两周复查一次 [JOB_MARKET_EVIDENCE.md](JOB_MARKET_EVIDENCE.md) 的链接有效性。
