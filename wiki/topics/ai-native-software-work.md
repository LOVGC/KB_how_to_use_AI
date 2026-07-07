---
title: AI-Native Software Work
type: topic
status: living
updated: 2026-07-06
sources: [2026-07-06-boris-cherny-why-coding-is-solved]
related: [research-practice]
tags: [coding, agent, workflow, organization]
---

> 锚点主题页 / anchor。汇总"当 AI 大幅降低写代码成本后,软件工作如何重组"的方法论与预测。

## Summary
AI-native software work 的核心变化不是 IDE 里补全更快,而是人的角色从"亲手写代码"转向"定义目标、调度 agents、审结果、维护反馈循环、把领域判断转成可运行系统"。Boris Cherny 的访谈给出一个强判断:对部分团队和代码库来说,coding 已经接近被解决;接下来更稀缺的是 domain knowledge、product taste、组织流程和 agent orchestration 能力。

## Coding shifts from implementation to orchestration
在 Claude Code 团队的语境里,模型已经能承担 100% 的代码书写,人的吞吐量以 PR、agents、loops 来度量,而不是以手写行数来度量。Boris 的个人设置是手机里开 5-10 个 Claude Code sessions,每个 session 跑多个 agents,白天可能几百个 agents,晚上几千个 agents 做 deeper work。[来源](../sources/2026-07-06-boris-cherny-why-coding-is-solved.md)

这不意味着所有软件都已无条件解决。复杂巨型代码库、模型不熟悉的语言/框架仍然是边界条件。但趋势上,产品形态在从 type-ahead 转向 agent 写完整代码,再转向后台循环和多 agent 协作。

## Loops, routines, and multi-agent work
Boris 提到的 `/loop` 是很具体的操作方式:让 Claude 使用 cron 在未来某个时间调度重复任务,可以每分钟、每 5 分钟或每天运行。典型用途包括 babysit PRs、修 CI、auto-rebase、保持 CI 健康、处理 flaky tests、定期抓取 Twitter feedback 并聚类。[来源](../sources/2026-07-06-boris-cherny-why-coding-is-solved.md)

routines 是同一思路的 server-side 版本,即使关掉电脑也会继续跑。multi-agent 方面,他提到直接要求 Claude 使用 sub-agents,以及通过 prompting 让模型更自然地并行化;但长期看,模型应当自己判断何时开 loop、何时调用 Slack MCP、何时周期性汇报,而不是要求用户手动决定所有并行策略。

这套做法可以抽象成一个 operational ladder:

1. **Phone/app as control surface**:手机或 app 只是控制台,人不再需要坐在 IDE 前连续打字。
2. **Sessions as context containers**:同时开 5-10 个 sessions,每个 session 承载一个工作上下文。
3. **Agents/sub-agents as execution units**:每个 session 里跑多个 agents;复杂任务交给 sub-agents 分解和并行执行。
4. **Loops as recurring jobs**:`/loop` 让 Claude 用 cron 把任务变成重复作业,适合 CI、PR、反馈聚类等持续维护任务。
5. **Routines as persistent server loops**:routines 把 loop 搬到 server 侧,让工作在电脑关闭后继续运行。
6. **Slack/MCP as coordination fabric**:不同人的 Claudes 可以通过 Slack/MCP 交流 unknowns,把个体 agent workflow 扩展成组织级协作。

## Cross-disciplinary generalists
一个关键 insight 是:AI 让 coding 变成横向能力后,generalist 的含义会升级。过去说 generalist,常指工程内部的广度,例如同时做 iOS、web、server;Boris 预测未来更常见的是 cross-disciplinary generalists,例如工程 + 产品、工程 + 设计、工程 + 数据。Claude Code 团队里的 PM、designer、data scientist、finance、user researcher 都写代码。[来源](../sources/2026-07-06-boris-cherny-why-coding-is-solved.md)

这对个人能力结构的含义是:不要只把 AI coding 理解为"工程师更快写代码"。更大的机会是让懂业务、懂用户、懂研究、懂财务的人获得可执行的表达能力。

## Domain judgment becomes the scarce part
Boris 用 accounting software 的例子说明:最适合写会计软件的人可能不是工程师,而是优秀会计,因为他们真正懂 domain;coding 变成容易的部分,难的是知道问题本身。这条判断应当作为本 wiki 的重要原则:当 AI 降低实现成本,问题选择、领域知识、品味和验收标准会变得更有杠杆。[来源](../sources/2026-07-06-boris-cherny-why-coding-is-solved.md)

## Business and organization implications
SaaS 不一定会简单死亡,但护城河会重排。Boris 认为 switching costs 和 process power 会变弱,因为模型可以迁移系统、理解流程并对目标 hill climb;network effects、scale economies、cornered resources 等仍然重要。对 startup 来说,AI-native 从零构建会比大公司改造既有流程更轻,因此小团队颠覆大公司的机会变多。[来源](../sources/2026-07-06-boris-cherny-why-coding-is-solved.md)

组织层面,领先不只是模型访问权,而是流程是否被 agent-native 化。Anthropic 内部的例子是:SQL、CI、coding、Slack 协作都由模型参与;不同人的 Claudes 会在 loop 中通过 Slack 交流 unknowns。

## Contradictions & open questions
- **"Coding is solved" 的适用边界**:Boris 自己也承认大规模复杂代码库、模型不熟语言仍未完全解决。后续需要更多来源区分:哪些代码任务已经 agent-native,哪些仍需要强工程师直接介入。
- **质量控制如何规模化**:几百到几千 agents 并行后,人的验收、权限、安全、审计和产品一致性如何保持,本文只给出趋势,没有完整方法论。
- **domain experts 写软件的组织后果**:当 accountant / designer / PM 都能直接构建系统,传统工程团队如何重新分工,还需要更多案例。

## Sources
- [Anthropic's Boris Cherny Why Coding Is Solved, and What Comes Next](../sources/2026-07-06-boris-cherny-why-coding-is-solved.md)

## Related
- [Research Practice](research-practice.md)
