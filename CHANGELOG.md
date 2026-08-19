# Changelog

遵循 [Keep a Changelog](https://keepachangelog.com/) 格式。

## [Unreleased] — 2026-08-19

### Added

- 岗位与能力模型五件套：`TARGET_ROLES.md`（岗位方向与边界）、
  `JOB_MARKET_EVIDENCE.md`（2026-08-19 实时采样 23 个岗位 + 技能频次）、
  `BASELINE.md`（优势与短板）、`SKILL_MATRIX.md`（等级/证据/差距行动）、
  `TOPIC_WEIGHTS.md`（288h 权重表，含 12/18/24h 三档缩放，合计可核对）。
- `PROJECT_STRATEGY.md`：项目从"待定"改为已定组合——
  tiny-llm + paged-infer（推理系统）、cuda-foundations + cuflash-attn +
  triton-fused-ops（Kernel）、fq-compressor（C++ 辅助）。
- `INTERVIEW_MATRIX.md`：面试题五要素矩阵（答案要点/追问树/代码定位/实验证据/评分标准）。
- `APPLICATION_PLAN.md`：简历版本、投递节奏、迭代规则与手动事项。

### Changed

- `README.md` 重写：修正过期事实（旧 README 写"29 个仓库/21 deep-dives 在本仓库"），
  deep-dives 指向 github-repos-hub。
- `ROADMAP.md` 重写：12 周主线带真实日期（2026-08-24 ～ 2026-11-15），
  每周必须交付明确；大型仓库改为"五个一"目标导向阅读，不再安排全仓通读。
- `study-plan.md` 重写：周节奏与三档时间预算，与 TOPIC_WEIGHTS 数字一致。
- `weekly/week-01..12.md` 全部重写：统一结构（目标/先修/时间预算/阅读范围/实验/
  交付物/面试题/退出条件/降级规则）。
- `resources.md`：deep-dive 链接保持指向 github-repos-hub，周次映射更新为新路线。

### Removed

- `deep-dives/`（21 个文件）与 `repo-index.md`：与 github-repos-hub 逐字节相同
  （diff 验证），deep-dives 唯一事实来源移回 github-repos-hub，Git 历史保留。
- `projects/project-ideas.md`（想法已被 PROJECT_STRATEGY 的现有项目覆盖）与
  `projects/personal-projects.md`（"项目待定"文件，已被 PROJECT_STRATEGY.md 取代）。
