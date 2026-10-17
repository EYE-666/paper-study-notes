# 正常的agent数学模型

```math
\text{Agent System}=(\pi_\theta,s_t,E)
```

这里：

| 符号           | 含义                             |
| ------------ | ------------------------------ |
| $`\pi_\theta`$ | Agent 的核心 LLM Policy，负责选择下一步行动 |
| $`s_t`$        | 第 t 次交互时的持久状态                  |
| $`E`$          | 外部环境，负责执行工具动作并返回观察结果           |
| $`x_t`$        | 第 t 次交互的用户请求                   |
| $`a_{t,i}`$    | 第 t 次交互中的第 i 个动作               |
| $`o_{t,i}`$    | 动作 $`a_{t,i}`$ 得到的观察结果            |
| $`g_t`$        | 本次交互的完整动作—观察轨迹                 |
| $`h_t`$        | 包含用户请求、状态与执行轨迹的交互历史            |

进一步定义：

```math
h_t=(x_t,s_t,g_t)
```

**Agent的下一步动作怎么产生**

```math
{a_{t,i}\sim \pi_\theta\left( \cdot\mid h_{\lt t},x_t,s_t,g_{t,\lt i} \right)}
```

```math
o_{t,i}=E(a_{t,i})
```

该公式说明：Agent 选择下一步行动时，不只是**根据用户当前的请求，还会受到🔴历史交互、🔵当前持久状态以及🟢当前执行过程中观察到的信息影响。**

**持久状态的更新**

```math
s_{t+1}=f(s_t,h_t)
```

**传统的单次交互攻击**

```math
o_{t,i}\longrightarrow o^{adv}_{t,i}
```

也就是说攻击者让agent看到了恶意内容

下一步动作变为：

```math
{a_{t,i+1}\sim \pi_\theta\left( \cdot\mid h_{\lt t},x_t,s_t,g_{t,\lt i},a_{t,i},o^{adv}_{t,i} \right)}
```

单次传统攻击成功：

```math
U(h^{adv}_t)=1
```

# Sleeper Attack

## 第一阶段：Plant

第t次交互第i步让agent看到了恶意内容

```math
o_{t,i}\longrightarrow o^{adv}_{t,i}
```

希望该内容写入持久状态

```math
s^{adv}_{t+1}=f(s_t,h^{adv}_t)
```

但有一个约束条件就是：

```math
U(h^{adv}_t)=0
```

**也就是说植入阶段本身不能已经完成指定的攻击目标**

## 第二阶段：Trigger

经过 $`k`$ 次交互间隔，在第 $`t+k`$ 次交互，用户提出新的请求 $`x_{t+k}`$

此时 Agent 可能受到已经污染的状态影响：

```math
{ a_{t+k,j}\sim \pi_\theta\left( \cdot\mid h_{\lt t+k},x_{t+k}, s_{t+k}^{adv},g_{t+k,\lt j} \right) }
```

达到攻击目标

```math
U(h^{adv}_{t+k})=1
```

# 三种攻击策略

## LIP:Latent Instruction Planting

也就是**潜伏指令植入**

过程如下:

```math
\text{外部指令} \rightarrow \text{持久记录} \rightarrow \text{被当作有效任务执行}
```

## PIE:Proactive Information Elicitation

也就是**主动信息诱取**

它研究一个更微妙的问题：

**如果攻击者不知道执行恶意操作所需的具体参数，Agent 会不会在未来主动找用户索取这些信息？**

过程如下:

```math
\text{恶意指令缺参数} \rightarrow \text{Agent 主动询问} \rightarrow \text{用户提供数据} \rightarrow \text{Agent 执行恶意操作}
```

## PIC：Persistent Information Corruption

也就是**持久信息污染**

PIC 的重点是：**让 Agent 执行用户原本要求的操作，但使用错误的、被污染的参数。**

过程如下：

```math
\text{恶意内容} \rightarrow \text{污染已保存事实} \rightarrow \text{正常用户任务} \rightarrow \text{使用错误参数} \rightarrow \text{错误结果}
```

## 三种攻击策略的本质区别

| 维度           | LIP       | PIE           | PIC            |
| ------------ | --------- | ------------- | -------------- |
| 核心攻击对象       | 待执行指令     | 缺少参数的待执行指令    | 已保存事实或参数       |
| 后续 Agent 行为  | 执行潜伏恶意任务  | 先询问信息，再执行恶意任务 | 执行正常任务，但使用错误信息 |
| 是否需要用户再次提供信息 | 不一定       | 需要            | 通常不需要          |
| 主要错误         | 错误地接受指令   | 错误地诱取并使用信息    | 错误地信任事实        |
| 安全失效机制       | 指令来源与授权混淆 | 信息提供与操作授权混淆   | 数据完整性与可信来源混淆   |

# 三种持久状态：Session,Memory,Skill

## Session

即session context 会话上下文

根据刚刚的数学模型可知：

模型当前的持久状态会收到历史交互的影响，因此把恶意内容Plant到Session可以实现攻击目标

跨session 可能丢失之前攻击植入的恶意内容

## Memory

即Agent的长期记忆

通过MemoryUpdate(),MemoryRetrieve()等工具

把恶意内容植入到Agent的Memory中 然后在未来进行检索和使用，达到Attack的目的

因此，Memory Attack 不能只看“**🟠恶意内容有没有写入**”，还要看“**🟢未来有没有检索到、是否被使用以及如何使用**”

## Skill

攻击者则可以尝试诱导 Agent 将恶意内容追加到 Skill 中。

为什么这种方式可能更危险？

一个原因是，普通事实型 Memory 往往只在相关问题出现时使用，而 Skill 是指导任务执行的程序性知识（Procedural Knowledge）。

如果某条恶意规则进入了常用的 Skill，就有机会在多次不同任务中重新影响执行流程。

# BenchMark的构建

## 论文采用的结构

**Agent 执行框架**

负责Agent 推理、工具调用与执行流程

**ToolEmu 模拟工具环境**

DeepSeek-V3.2 模拟工具执行结果

**状态模块**

Memory 存储与检索

BIG/SMALL Skill 读写

**用户模拟回答**

PIE中模拟用户的回答，同样使用DeepSeek-V3.2

**结构化评估器**

检查 Agent 的工具调用顺序、参数和攻击目标完成情况，计算 ASR

# 如何评估攻击真的成功？

**三个 LLM 来审查和完善 eval_config**

## **输入**：**攻击案例 + 工具定义 + 初始评估规则**

## Proposer

根据已有草稿，提出一套足以判断攻击成功的结构化规则

## Critic

检查规则是否遗漏关键步骤、参数名称是否错误、条件是否过宽或过严

## Arbiter

综合前两个模型的输出，决定接受规则，还是修改后进入下一轮。

## 输出：最终版本 eval_config

## 由 Python 对工具调用轨迹进行确定性的规则匹配

# 局限性

局限一：主实验的长程程度有限。

局限二：模拟环境会影响真实风险估计。

局限三：PIE 使用较为合作的用户模拟机制。

局限四：状态之间的比较不能完全解释为状态类型本身的因果效应。
