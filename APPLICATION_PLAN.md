# 求职执行计划（APPLICATION_PLAN）

更新日期：2026-08-19。12 周计划见 [ROADMAP.md](ROADMAP.md)；岗位样本见
[JOB_MARKET_EVIDENCE.md](JOB_MARKET_EVIDENCE.md)。

## 简历版本

| 版本 | 定位 | 主打项目顺序 |
|------|------|-------------|
| v-kernel | GPU Kernel / Inference Performance | cuflash-attn + triton-fused-ops + cuda-foundations → tiny-llm → fq-compressor |
| v-serving | LLM 推理运行时与 Serving | tiny-llm + paged-infer → cuflash-attn → fq-compressor |

- 每个条目必须含：量化结果 + 硬件/口径 + 可点击的仓库链接（规范地址）。
- Fork 与 AI 翻译成果不得写入项目经历。
- W10 完成两版初稿，W11 模拟面试后修订，W12 冻结。

## 投递节奏（W10 起启动，W12 全力）

- W10：建立跟踪表（公司/岗位/渠道/状态/复盘），投 3–5 家练手（非首选公司）。
- W11–W12：每周 10–15 个有效投递；大陆岗位走内推优先（脉脉/朋友/猎头），全球岗位
  LinkedIn + 官网直投。
- 反馈闭环：每次笔试/面试后 24h 内写复盘（挂在 `notes/`），更新 SKILL_MATRIX 与
  INTERVIEW_MATRIX 的自评。

## 迭代规则

- 简历投出 20 份无面试邀请 → 重写项目条目的量化表述，检查关键词覆盖。
- 一面通过率 < 30% → 增加 W11 式有评分模拟面试频次（每周 1 次）。
- 笔试挂 → 每日加 30min 算法题（从 8% 基础桶内调配，不动 P0 桶）。

## 手动事项（需用户本人完成）

- GitHub Profile 手动 Pin 六个仓库：cuflash-attn、tiny-llm、paged-infer、
  cuda-foundations、triton-fused-ops、fq-compressor（Pinned items 无法用当前
  token 的 API 修改）。
- 内推请求与投递邮件由本人发送。
