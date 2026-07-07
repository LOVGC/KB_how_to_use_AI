---
title: "Anthropic's Boris Cherny Why Coding Is Solved, and What Comes Next"
type: source
url: unknown
author: Boris Cherny
published: unknown
ingested: 2026-07-06
topics: [ai-native-software-work]
tags: [coding, agent, workflow, organization, startups]
---

## TL;DR
这是一场围绕 Claude Code、agentic coding、软件团队未来和创业机会的访谈。Boris Cherny 的核心判断是:对他和 Claude Code 团队来说, coding 已经接近"被解决",人的工作正在从亲手写语法转向设定目标、调度 agents、审阅结果、重塑组织流程。最值得记录的 insight 是:当 coding 变便宜后,稀缺性从"会不会写代码"转向"有没有足够好的领域判断"。

## Key points
- **Claude Code 是为下一个模型做的产品**:Boris 说 Claude Code 起源于 Anthropic Labs,一开始是看到 coding 上有 product overhang:模型能力已经超过当时只做 type-ahead 的产品形态。前 6 个月体验并不强,真正爆发从 Opus 4 开始;这说明他们是在 PMF 到来前,押注下一代模型能力。
- **"Coding is solved" 是有边界的**:对 Boris 自己而言,模型写 100% 的代码,他一天能推进几十个 PR,极端时一天 150 个 PR。但他也明确说这不适用于所有地方:超大复杂代码库、模型不熟的奇怪语言仍然没完全解决,只是趋势上在靠下一代模型逼近。
- **个人工作流已经从 coding 变成 agent orchestration**:他主要在手机上工作,同时开 5-10 个 Claude Code sessions;每个 session 有多个 agents,当前可能有几百个 agents 在跑,晚上还会有几千个 agents 做 deeper work。管理方式包括让 Claude 使用 sub-agents,以及越来越多使用 `/loop`。
- **Loops / routines 是最具体的机制**:`/loop` 的做法是让 Claude 用 cron 在未来某个时间调度一个重复任务,频率可以是每分钟、每 5 分钟或每天。Boris 的例子包括:babysit PRs、修 CI、auto-rebase、保持 CI 健康、处理 flaky tests、每 30 分钟抓 Twitter feedback 并聚类。routines 是 server 侧版本,即使关掉电脑也能继续跑。
- **可复用的操作链条**:这套方法可以概括为 phone/app 作为控制台 -> 多个 sessions 承载上下文 -> 每个 session 里跑多个 agents/sub-agents -> `/loop` 把任务变成 cron-based repeat jobs -> routines 把循环迁到 server 侧持续运行 -> Slack/MCP 让不同 agents 互相协调 unknowns。
- **Multi-agent 的产品层主要靠 prompting,但责任会逐渐转给模型**:当被问到如何让模型更会并行化时,Boris 说产品侧现在主要是 prompt tweak,让模型更自然地并行做事。但随着模型变强,它会自己发现应当启动 loop、调用 Slack MCP、定期报告;用户不该承担"什么时候并行化"的主要心智负担。
- **工程师会变成跨学科 generalist**:Boris 预测未来会有更多 cross-disciplinary generalists,不是只会 iOS/web/server 的工程内 generalist,而是工程 + 产品 + 设计 + 数据等跨域组合。他说 Claude Code 团队里 PM、designer、data scientist、finance、user researcher 都写代码。
- **真正稀缺的是领域判断**:Boris 用 accounting software 举例:最适合写会计软件的人可能不是工程师,而是优秀会计,因为他们懂 domain,而 coding 变成容易的部分。这是本篇对"如何用 AI"最重要的迁移:AI 把表达/实现成本降下来,domain taste 和问题判断变得更值钱。
- **软件会像读写能力一样民主化**:他用欧洲印刷术类比:书籍成本下降后,识字率长期上升;软件也会成为普通人能做的能力,同时仍然会存在专业软件工作者,就像今天仍然有专业作家。
- **SaaS 护城河会重排,但不是简单死亡**:他借 Hamilton 的 Seven Powers 框架判断,AI 会削弱 switching costs 和 process power,因为模型能迁移系统、理解流程、hill climb 目标;但 network effects、scale economies、cornered resources 等仍然重要。更大的变化是 startup 数量和颠覆能力可能 10x 增长。
- **Anthropic 的领先更多是组织流程,不是模型特权**:Boris 说内部基本用外部也能用到的模型;真正领先的是组织已经把 coding、SQL、CI、Slack 协作等流程改造成 agent-native,包括自己的 Claudes 在 loop 中通过 Slack 与别人的 Claudes 协调 unknowns。

## Notable quotes
> "generalists that are cross-disciplinary"

> "Everyone on our team codes."

> "coding is the easy part. It's knowing the domain that's the hard part."

> "loops are the future at this point."

## Connections
- [AI-Native Software Work](../topics/ai-native-software-work.md) —— 本文是该主题页的锚点来源,提供了从个人 coding workflow 到组织流程、职业结构、SaaS 护城河变化的一整套预测。
- [Research Practice](../topics/research-practice.md) —— 与其中的 feedback loops / tooling 观念相邻:研究里强调缩短发现错误的循环,本文则把这种循环推进到后台 agent、CI、PR、用户反馈的自动化层。

## Emphasis & notes
- 摄入重点:**跨学科 generalist 与领域判断**。这篇访谈最值得沉淀的 insight 是:当 AI 让 coding 变便宜,软件构建的瓶颈会从语法实现迁移到 domain knowledge、taste、目标设定和结果判断。
- 同时记录 Boris 对 loops / routines / multi-agent 的具体做法,因为这不是泛泛而谈"用很多 agent",而是已经有清晰操作形态:phone/app 控制台 -> sessions -> agents/sub-agents -> cron-based loops -> server-side routines -> Slack/MCP 协作。
- 来源是 raw transcript,未附 url / published date;后续可补元数据。
