“PDF 编号”对应原 PDF 参考文献的编号，“阅读序号”是我建议你实际阅读的顺序。

# Long-horizon Agent Safety 论文阅读计划

## 第一阶段：基础知识与研究背景（3 篇）

目标： 理解 LLM Agent 的工作机制、Prompt Injection 的基本原理，以及传统安全防御为什么可能无法解决长程安全问题。

### 01. AgentDojo

完整标题： AgentDojo: A Dynamic Environment to Evaluate Prompt Injection Attacks and Defenses for LLM Agents

- 作者：Debenedetti et al.
- 会议：NeurIPS 2024（Datasets and Benchmarks）
- PDF 参考文献编号：#16
- 阅读要求：精读
- 阅读重点：Agent 环境、工具调用、Prompt Injection 攻击、攻击与防御的评测方法。

### 02. The Instruction Hierarchy

完整标题： The Instruction Hierarchy: Training LLMs to Prioritize Privileged Instructions

- 作者：Wallace et al.
- 年份：2024
- PDF 参考文献编号：#12
- 阅读要求：精读
- 阅读重点：指令优先级、可信与不可信内容的区分、Instruction Hierarchy Training。

### 03. Sleeper Attack

完整标题： Plant, Persist, Trigger: Sleeper Attack on Large Language Model Agents

- 作者：Li et al.
- 年份：2026
- arXiv：2605.28201
- PDF 参考文献编号：#1
- 阅读要求：精读
- 阅读重点：潜伏攻击、Plant-Persist-Trigger 攻击生命周期、长程 Agent 安全评测。

## 第二阶段：Long-horizon Agent Safety 核心安全问题（7 项）

目标： 理解上下文压缩、记忆写入、技能提炼、自进化等机制如何引入新的安全风险。这是整份研究计划最核心的文献部分。

### 04. Governance Decay

完整标题： Governance Decay: How Context Compaction Silently Erases Safety Constraints in Long-Horizon LLM Agents

- 作者：Chen
- 年份：2026
- arXiv：2606.22528
- PDF 参考文献编号：#2
- 阅读要求：精读
- 阅读重点：Context Compaction、长程安全约束丢失、上下文压缩对 Agent 安全性的影响。

### 05. MemPoison

完整标题： MemPoison: Uncovering Persistent Memory Threats and Structural Blind Spots in LLM Agents

- 年份：2026
- arXiv：2607.14651
- PDF 参考文献编号：#5
- 阅读要求：精读
- 阅读重点：Memory Poisoning、持久化记忆的安全风险、跨会话潜伏攻击。

### 06. SkillJack

完整标题： SkillJack: Persistent Skill Backdoors in Self-Evolving Agents

- 作者：Ying et al.
- 年份：2026
- arXiv：2608.03509
- PDF 参考文献编号：#6
- 阅读要求：精读
- 阅读重点：Skill Extraction、技能后门、恶意行为在技能提炼和复用过程中的持久化。

### 07. AgentSys

完整标题： AgentSys: Secure and Dynamic LLM Agents Through Explicit Hierarchical Memory Management

- 年份：2026
- arXiv：2602.07398
- PDF 参考文献编号：#4
- 阅读要求：通读
- 阅读重点：Agent Memory Management、上下文长度与安全风险、层级化记忆管理。

### 08. Practice Makes Unsafe

完整标题： Practice Makes Unsafe: Skill Misevolution in Self-Improving LLM Agents

- 作者：Mao et al.
- 年份：2026
- arXiv：2608.12851
- PDF 参考文献编号：#7
- 阅读要求：精读
- 阅读重点：Skill Misevolution、自我改进中的安全退化、技能学习过程中的风险积累。

### 09. Your Agent May Misevolve

完整标题： Your Agent May Misevolve: Emergent Risks in Self-evolving LLM Agents

- 会议：ICLR 2026
- PDF 参考文献编号：#8
- 阅读要求：精读
- 阅读重点：Self-evolving Agents、经验驱动的自进化、持续学习中的安全风险。

### 10. OpenAI 对齐事故报告

PDF 列出的标题： Self-generated prompt injections in compaction summaries

- 发布机构：OpenAI
- 时间：2026 年 9 月
- 类型：Misalignment Report
- PDF 参考文献编号：#3
- 阅读要求：通读
- 阅读重点：模型在上下文压缩摘要中自行产生类似提示注入的内容，以及这种现象对 Agent 安全的启示。

注意：这一项是研究报告，不是常规学术论文。

## 第三阶段：已有安全防御方法与模型训练（6 篇）

目标： 了解目前研究者如何防御 Prompt Injection、保护 Agent 的记忆与技能，以及如何通过模型训练提高安全性。

### 11. SecAlign

完整标题： SecAlign: Defending Against Prompt Injection with Preference Optimization

- 作者：Chen et al.
- arXiv：2410.05451
- PDF 参考文献编号：#13
- 阅读要求：精读
- 阅读重点：Preference Optimization、模型侧 Prompt Injection 防御、对齐训练目标。

### 12. ISE

PDF 列出的名称： Instructional Segment Embedding (ISE)

- 作者：Wu et al.
- 会议：ICLR 2025
- PDF 参考文献编号：#18
- 阅读要求：通读
- 阅读重点：Instruction/Data Separation、Segment Embedding、通过表示区分指令与数据。

注：PDF 仅提供上述名称，没有列出更长的论文标题。

### 13. ASIDE

完整标题： ASIDE: Architectural Separation of Instructions and Data in Language Models

- 作者：Zverev et al.
- 年份：2025
- PDF 参考文献编号：#19
- 阅读要求：通读
- 阅读重点：模型架构层面的指令与数据分离、安全边界的结构化设计。

### 14. A-MemGuard

完整标题： A-MemGuard: A Proactive Defense Framework for LLM-Based Agent Memory

- 会议：ICML 2026
- PDF 参考文献编号：#10
- 阅读要求：精读
- 阅读重点：Agent Memory Defense、异常记忆检测、多条记忆的可信度与一致性。

### 15. SafeEvolve

完整标题： SafeEvolve: Harness-Policy Co-Evolution from Agent Experience for Safety Alignment

- 作者：Mao et al.
- 年份：2026
- arXiv：2609.02786
- PDF 参考文献编号：#9
- 阅读要求：精读
- 阅读重点：Harness-Policy Co-Evolution、经验驱动的安全对齐、SFT 和强化学习。

### 16. ARLAS

完整标题： Adversarial Reinforcement Learning for Large Language Model Agent Safety

- 作者：Wang et al.
- arXiv：2510.05442
- PDF 参考文献编号：#14
- 阅读要求：通读
- 阅读重点：Adversarial Reinforcement Learning、Agent Safety Training、对抗式安全优化。

## 第四阶段：Agent 经验学习、攻击评测与补充技术（7 项）

目标： 理解 Agent 如何从历史任务中提取可复用经验，了解已有攻击评测体系以及自适应攻击方法。

### 17. Agent Workflow Memory

PDF 列出的名称： Agent Workflow Memory

- 作者：Wang et al.
- 年份：2024
- PDF 参考文献编号：#20
- 阅读要求：通读
- 阅读重点：Agent Workflow、工作流记忆、从历史任务中抽取可复用操作流程。

注：PDF 没有提供更完整的论文标题。

### 18. ExpeL

完整标题： ExpeL: LLM Agents Are Experiential Learners

- 作者：Zhao et al.
- 会议：AAAI 2024
- PDF 参考文献编号：#22
- 阅读要求：通读
- 阅读重点：Experiential Learning、从成功和失败轨迹中总结经验、经验复用。

### 19. Voyager

完整标题： Voyager: An Open-Ended Embodied Agent with Large Language Models

- 作者：Wang et al.
- 年份：2023
- PDF 参考文献编号：#21
- 阅读要求：通读
- 阅读重点：Skill Library、自动技能积累、技能检索与持续学习。

### 20. InjecAgent

完整标题： InjecAgent: Benchmarking Indirect Prompt Injections in Tool-Integrated LLM Agents

- 作者：Zhan et al.
- 年份：2024
- PDF 参考文献编号：#17
- 阅读要求：通读
- 阅读重点：Indirect Prompt Injection、工具集成 Agent 的攻击评测、Benchmark 设计。

### 21. The Attacker Moves Second

完整标题： The Attacker Moves Second: Stronger Adaptive Attacks Bypass Defenses Against LLM Jailbreaks and Prompt Injections

- 作者：Nasr, Carlini et al.
- 年份：2025
- arXiv：2510.09023
- PDF 参考文献编号：#11
- 阅读要求：精读
- 阅读重点：Adaptive Attacks、攻击者针对防御策略进行优化、攻击和防御的动态博弈。

### 22. AdvSim2Real

完整标题： AdvSim2Real: Training Web Agents Against Adaptive Prompt Injection in a Web World Model

- 作者：Hashmi et al.
- 年份：2026
- arXiv：2610.08773
- PDF 参考文献编号：#15
- 阅读要求：通读
- 阅读重点：Web Agents、Adaptive Prompt Injection、模拟环境中的安全训练。

### 23. 各 Agent 上下文压缩机制对比

PDF 列出的资料： 各 agent 压缩机制的第三方对比

- 类型：第三方技术分析网页
- PDF 参考文献编号：#23
- 阅读要求：辅助阅读
- 阅读重点：Codex CLI、Claude Code、Gemini CLI、OpenHands 等 Agent 的上下文压缩策略与触发机制。
- 资料链接：Context Compaction Showdown

这一项不是学术论文。

## 最终阅读计划汇总

| 阶段           | 阅读序号  | 数量   | 重点             |
| ------------ | ----- | ---- | -------------- |
| 第一阶段：基础知识    | 01–03 | 3    | 全部精读           |
| 第二阶段：长程安全风险  | 04–10 | 7    | 04、05、06、08、09 |
| 第三阶段：安全防御方法  | 11–16 | 6    | 11、14、15       |
| 第四阶段：技术与评测补充 | 17–23 | 7    | 21，其他按需深入      |
| 合计           | 01–23 | 23 项 |                |
