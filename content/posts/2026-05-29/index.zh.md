---
title: "5月29日 · 今日技术精选"
date: 2026-05-29T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "anthropic", "claude", "postgres", "code-agent"]
categories: ["daily"]
summary: "Anthropic 一天放两连发：Claude Opus 4.8 和 650 亿美金 H 轮；Postgres 重新被推到工作流编排的 C 位；V2EX 在讨论国产 Code Agent 到底打不打得过 Claude Code。"
---

## 今日速览

今天的主旋律仍然是"AI 编码代理"——Anthropic 同一天发布 Claude Opus 4.8 并宣布完成 650 亿美金 H 轮（投后估值 9650 亿美金），Claude Code 也上了 Dynamic Workflows。与此同时，工程圈把目光转回到一个老朋友：Postgres——DBOS 写了篇文章直接喊"durable workflow，用 Postgres 就够了"。中文圈则在 V2EX 上集体追问：国产 Code Agent 到底有没有能打的。三件事拼起来，可以理解为一句话：**模型在变强，编排在变薄，护城河在重新被分配。**

## 今日 10 条

### 1. Claude Opus 4.8 发布
**Source: Anthropic · Product**
<https://www.anthropic.com/news/claude-opus-4-8>

Opus 系列再升一个小版本，主打编码、Agent 任务、长任务一致性。在 HN 首页冲到 1000+ 分，评论区主要争论两点：上下文行为是否更稳、长 session 是否还会"中途松手"。对中国/日本的开发者，最实际的变化大概是：Claude Code 端侧的 Plan / Edit 行为会再"稳一点"。

### 2. Anthropic 完成 650 亿美元 H 轮，投后估值 9650 亿美元
**Source: Anthropic · Announcements**
<https://www.anthropic.com/news/series-h>

数字大到有点超现实——但更值得读的是它对 Anthropic 战略的隐含信号：算力、企业市场、政府合规三条线全都要继续重投。对国内开发者来说，短期意味着 API 价格不会突然便宜；长期意味着 Claude 在企业渠道（KPMG、PwC 这些大客户）会越扎越深，绕开它的方案越来越少。

### 3. Claude Code 推出 Dynamic Workflows
**Source: Anthropic · Claude blog（经 HN 推荐）**
<https://claude.com/blog/introducing-dynamic-workflows-in-claude-code>

简单说就是把 "/command + skill" 抽象做得更连贯：让 agent 在执行中按需切换工作流，而不是一开始就锁死路径。这一步动作不性感，但意义不小——这是 IDE 端"Agentic 编排"从静态脚本走向动态调度的关键一跳，国内类 Agent 工具（包括下面 V2EX 在讨论的那些）几乎肯定要跟进。

### 4. Just Use Postgres for Durable Workflows
**Source: DBOS Blog（经 HN #3）**
<https://www.dbos.dev/blog/postgres-is-all-you-need-for-durable-execution>

文章核心论点：你不需要 Temporal、不需要 Airflow、不需要专门的工作流引擎——一张 Postgres 表 + 一个事务，就能拿到 exactly-once 的 durable execution。HN 上 200 分上下，吵得最凶的是"那高并发场景下呢"。对国内做后端的同学，这是一个值得当周末实验玩一玩的方向，尤其是已经把 Postgres 当主库的团队。

### 5. Various LLM Smells
**Source: shvbsle.in（经 HN #4）**
<https://shvbsle.in/various-llm-smells/>

类似"code smell"的 LLM 版本——作者把日常用 LLM 工具时遇到的反复出现的坏味道做了清单：过度道歉、"装作 grep 实际靠猜"、跨段落丢失上下文等等。读起来像在照镜子，但作者也给了不少可操作的对策（如怎么写更结构化的提示、怎么强制 grounding）。

### 6. SQLite 仓库里出现了 AGENTS.md
**Source: Simon Willison · Weblog**
<https://github.com/sqlite/sqlite/blob/master/AGENTS.md>

SQLite 团队在 5 月 22 日提交了一份 AGENTS.md，并不是给自己用，而是写给那些把 Agent 指向 SQLite 代码库的人。第一句话就是劝退："SQLite 不接受 GitHub Pull Request"。这是一个有趣的信号——上游项目正在专门写"给 AI 看的 README"，反过来约束 agent 的行为。

### 7. AWS 发布 Kiro Web：浏览器里就能用的 AI 编码代理
**Source: Publickey**
<https://www.publickey1.jp/blog/26/awswebaikiro_web.html>

不用本地安装，浏览器打开就能用——AWS 的策略很清楚：把入门门槛拉到几乎为零。对企业内部已经标准化在 AWS 上的团队，这意味着 Cursor / Claude Code 这类需要本地权限的工具突然多了一个不需要"打通安全策略"的同事。

### 8. VS Code 推出 Agent Window 预览
**Source: Publickey（5/15）**
<https://www.publickey1.jp/blog/26/vs_codeaiagent_window.html>

VS Code 这一版给"多 Agent 并行"做了原生 UI：一个窗口里同时挂多个 agent 任务，各自跑各自的分支。本周日本圈很多团队博客都在跟进这个用法（包括 Zenn 上"Cursor 3 的 Agent Window 心得"），算是 IDE 端的事实标准在被重新定义。

### 9. V2EX 热议：国产 Code Agent 到底有没有能打的？
**Source: V2EX · 程序员节点**
<https://www.v2ex.com/t/1215881>

帖子下面的回复算是一份小型国产 Agent 实测清单：通义、智谱 Coding、MiniMax、阿里 Lingma 等都有人晒。结论比较一致——单点对比 Claude Code 还差一截，但在"中文文档+国内云生态"的场景里已经基本可用。值得收藏，因为这种横向对比在国内一手社区其实不太常见。

### 10. V2EX 讨论：用命令行提取 macOS 核心软件 Top 30
**Source: V2EX · macOS 节点**
<https://www.v2ex.com/t/1215916>

楼主用一行 `find /Applications` + `mdls` 组合，按打开次数 + 文件大小做了排序。技术含量不算特别高，但评论区相当于一场"程序员都在用什么 Mac 工具"的社区调研——Raycast、Orbstack、Ghostty、Warp、Cursor 出现频率最高，对刚换 Mac 的同学是很实用的参考。

## 编者按

如果今天只挑两条读，推荐 **#4（Just Use Postgres）** 和 **#3（Dynamic Workflows）**。一个代表"基础设施被 LLM 推着回到更朴素的形态"，一个代表"工具链正在向动态调度演进"——两件事看似无关，其实都是在说同一件事：复杂度正在从"系统"流向"模型上下文"。今天 GitHub Trending 抓取超过单次响应大小限制、Zenn 当日 Trending 时间戳偏旧，相关条目用 Publickey 顶替了。
