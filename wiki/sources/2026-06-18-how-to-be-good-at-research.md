---
title: "how to be good at research"
type: source
url: unknown
author: unknown
published: unknown
ingested: 2026-06-18
topics: [research-practice]
tags: [meta, research]
---

## TL;DR
一篇讲"如何把 (ML/AI) 研究做好"的随笔。核心论点:研究不是天赋,而是一摞可以刻意训练的小技能——自己挑问题、升级输入、把一切写下来、收紧实验循环、亲手盯输出、有目的地拓宽领域、与人连接。这些日常小优势会像利息一样复利,几年后产生"从外面看像运气"的产出。

## Key points
- **自己挑问题,别被动吸收**:吸收来的问题你"只有结论没有推理",大厂转向你一年后才知道,且热门方向上你在和上千人抢算力。Schulman 的两种研究模式里,推荐从"你真心想要存在的结果"倒推实验,以此制造原创性。Taste 可训练:跑实验前先预测结果、遮住论文结果区猜数字、预测哪些发布两年后还重要,再核对命中率。
- **升级输入**:共享阅读清单 → 共享结论(≈没价值)。老材料被严重低估(MoE 1991、LSTM 1997、backprop 1986、Sutton 的 Bitter Lesson、Shannon 1952 创造性思考:把问题缩到平凡→解决→再逐步加回难度)。广度与深度一样重要。读论文本身而非转述——appendix 藏尸,limitations 最诚实。
- **把一切写下来**:写作会暴露脑中被掩盖的漏洞(Paul Graham);第一个不能骗的是你自己(Feynman);反对自己理论的事实当场记下(Darwin);记结构化 log(假设/设置/预期/结果/更新后的信念);再公开一部分(Olah & Carter 的 research debt——清晰解释本身是贡献,公开写作是不可伪造的简历)。
- **收紧循环**:研究速度 ≈ 你发现自己错了的速度(Radford 靠 volume 而非灵光一现);tooling 是一等研究活动(一条命令起跑/画图、从 config 完全可复现);先在单 batch 上过拟合(Karpathy,30 秒干掉一半 bug);工程与研究在前沿已融合。
- **盯着输出看**:下降的 loss 曲线是安慰不是分析;写训练代码前先手工看几小时原始数据(大多数 bug 在数据里且静默失败);拉 100 个失败案例全读、分堆、攻击最大的堆(Andrew Ng)——对 model 和 eval 都成立。
- **有目的地游荡**:第一个子领域只是时间的意外;先跑一次性版本让多数想法夭折;把 baseline 调到痛;ablate 到知道是哪个组件扛起结果(通常不是标题里那个);广度是抗饱和的保险。
- **找到你的人**:开门(可被打断)的人做出重要工作,因为中断携带"世界真正需要什么"的信息;慷慨在研究里复利最猛;公开抛半成品(时间线上犯错比出版物上便宜);早早说你想法烂的合作者比算力值钱。
- **长期游戏**:知识与生产力像利息一样复利,比你觉得必要的时间更早开始。

## Notable quotes
> "research speed is mostly the speed at which you discover you're wrong."

> "a descending loss curve is not analysis, it's reassurance."

> "the appendix is where the bodies are buried, and the limitations section is usually the most honest paragraph in the document."

## Connections
- 锚点主题:[Research Practice](../topics/research-practice.md) —— 本文是该主题页的第一篇来源,其 7 个板块即源自本文的结构。

## Emphasis & notes
- 摄入视角:**忠实原文**——当作 ML 研究方法论记录,暂不向"如何用好 AI"迁移(后续若想做迁移,可在 topic 页另起一节)。
- 出处未在原文件中标注,`author` / `url` / `published` 暂记 `unknown`;需要的话可联网检索补全。
