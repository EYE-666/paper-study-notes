# 论文学习笔记

集中整理论文阅读笔记、学习总结、文献汇报和研究方向阅读计划。

## 论文笔记

| 主题 | 入口 | 材料 |
| --- | --- | --- |
| GCG | [论文学习与文献汇报](gcg/) | [学习总结](gcg/GCG学习总结.md)、[文献汇报 PPT](gcg/GCG文献汇报.pptx)、论文与官方代码链接 |
| Sleeper Attack | [学习笔记](sleeper-attack/) | Agent 数学模型、Plant / Trigger、LIP / PIE / PIC、持久状态与评估方法 |
| Governance Decay | [学习笔记](governance-decay/) | 上下文压缩与规则丢失、ConstraintRot、Compaction-Eviction Attack、Constraint Pinning |

## 阅读计划

- [Long-horizon Agent Safety 阅读计划](reading-plans/long-horizon-agent-safety/)：按阶段组织的论文与资料阅读路线。

## 代码复现

实验命令、环境、日志和结果统一放在 [code-reproductions](https://github.com/EYE-666/code-reproductions)。

- [GCG Algorithm 1：单行为实验](https://github.com/EYE-666/code-reproductions/tree/main/gcg/algorithm1-single-behavior)
- [GCG Individual Attack：250 条行为实验](https://github.com/EYE-666/code-reproductions/tree/main/gcg/individual-250)

## 新笔记的整理方式

每篇论文使用独立目录，以 README 作为阅读入口，相关图片、附件和汇报材料保存在同一目录。阅读计划放在 `reading-plans/` 下，并更新上方目录。

## 来源与历史

2026-10-17 按类别合并整理。各子目录保留原文件内容与提交历史；下列旧仓库作为归档入口保留。后续更新集中在本仓库。

| 当前目录 | 原仓库 | 迁入版本 |
| --- | --- | --- |
| [gcg](gcg/) | [GCG-paper-study-notes](https://github.com/EYE-666/GCG-paper-study-notes) | [03a64e5](https://github.com/EYE-666/GCG-paper-study-notes/commit/03a64e5720035cbb21b8314551accbcc5fd774b7) |
| [sleeper-attack](sleeper-attack/) | [Sleeper-Attack-study-notes](https://github.com/EYE-666/Sleeper-Attack-study-notes) | [52ae5e6](https://github.com/EYE-666/Sleeper-Attack-study-notes/commit/52ae5e6a36049d514bb0cec6bf6c4db67204b3d0) |
| [reading-plans/long-horizon-agent-safety](reading-plans/long-horizon-agent-safety/) | [Long-horizon-Agent-safety-reading-plan](https://github.com/EYE-666/Long-horizon-Agent-safety-reading-plan) | [32ffb36](https://github.com/EYE-666/Long-horizon-Agent-safety-reading-plan/commit/32ffb3622ce4e420b445a57a7093af479e9b749f) |
