---
title: "6月4日 · 今日技术精选"
date: 2026-06-04T07:00:00+09:00
draft: false
tags: ["digest", "2026-06", "microsoft-build", "anthropic", "vscode", "security", "codex", "windows"]
categories: ["daily"]
summary: "Microsoft Build 2026 第二天刷屏：七个自研 AI 模型、给 Agent 用的隔离运行时 MXC、WSL containers、Windows 原生 coreutils。VSCode 一个点击就能偷走 GitHub Token。Anthropic 把 Partner Network 扩到服务商，并发布一年的 AI 攻击数据。"
---

## 今日速览

今天基本是被 Microsoft Build 2026 承包了。Redmond 这次的姿态很明显，就是要把开发者从 Linux/macOS 工作流里慢慢拽回 Windows：七个自研 AI 模型一次发完、给 Agent 跑命令的沙箱运行时 MXC、WSL 上跑原生 Linux 容器、再加一个 Windows 原生的 GNU coreutils（`ls`、`cat`、`cp` 终于不再是别名）。安全方面 `ammaraskar` 那篇 VSCode 一键偷 GitHub Token 的拆解非常值得读，国内大厂里 VSCode 几乎是标配 IDE，CSO 们今天大概率要开会。Anthropic 这边动作也密集：合作伙伴体系开服务商通道、外加一份用 MITRE ATT&CK 框架梳理过去一年 AI 攻击数据的报告。

---

### 1. VSCode 一键偷走 GitHub Token 的漏洞 — `[Hacker News · 579 分]`
<https://blog.ammaraskar.com/github-token-stealing/>

利用 workspace trust 的绕过，恶意仓库可以触发一个一次点击就把用户 GitHub OAuth Token 外发出去的流程。作者把 URL handler 滥用、披露时间线讲得很清楚，没有水分。如果你日常用 VSCode + GitHub 插件并且经常 review 陌生 fork 的 PR，这是今天必读。微软已经修了，但很多公司因为合规原因把 VSCode 版本钉死，建议检查一下自己用的版本号。

### 2. 字节级性能优化：每个字节都要计较 — `[Hacker News · 166 分]`
<https://fzakaria.com/2026/06/01/every-byte-matters>

一篇很扎实的长文，讲一个被浪费掉的字节落在热路径上会让你多付什么代价：cache line、page fault、分支预测、还有现代 allocator 背着你把分配大小向上取整。作者全程跑了真实测量数据，不是凭感觉，所以结论可以迁移。看完顺手用 `perf stat` 跑一下自家服务，是一个很诚实的下午。

### 3. Simon Willison：用 Codex Desktop 一句话造了一个粘贴文件编辑器 — `[Simon Willison]`
<https://tools.simonwillison.net/pasted-file-editor>

Simon 这次发的工具本身不复杂——长文本粘贴进去自动转成文件附件预览，模仿了 Claude.ai 和 Claude 桌面端那个体验。亮点是 build story：他用 Codex Desktop 一条 prompt 让它把整个工具生成出来。"AI 一段话写个内部小工具"这件事已经从新奇变成日常，国内团队搭内部 dashboard、运营自助页之类的，思路完全可以借鉴。

### 4. 慎重升级 Codex 最新版（26.601.21317）— `[V2EX · 程序员]`
<https://www.v2ex.com/t/1217473>

最新版 Codex 桌面端在亚太用户里大面积出现登录鉴权问题，帖子里汇总了报错现象和几个可用的回退版本。如果你的 CI、或者 commit-on-save 流程依赖 codex 命令，这一两天别急着升，等修复了再说。

### 5. 手机上远程操作 Claude Code / Codex 的终端 App — `[V2EX · 分享创造]`
<https://www.v2ex.com/t/1217542>

`rwecho` 写了一个手机端的终端 App，背后接远端的 Claude Code 或 Codex 会话，交互更像聊天客户端而不是 ssh，对手指更友好。是不是真正"能干活"取决于你日常多少任务是一句 prompt 能搞定的；但作为"把 coding agent 当成可远程寻址的实体"这个范式，是一个干净的样例，国内通勤路上调 bug 党可以关注下。

### 6. Coreutils for Windows 正式公开 — `[Publickey · MS Build 2026]`
<https://www.publickey1.jp/blog/26/unixwindowscoreutils_for_window.html>

微软给 Windows 内置了一套用 Rust 重写的 GNU coreutils，`ls`、`cat`、`cp`、`mv`、`rm` 等命令以后是 Windows 11 自带组件。过去二十年 PowerShell 用别名糊出来的"差不多就行"终于可以扔掉了，跨平台 Makefile、shell 脚本风格的自动化在原版 Windows VM 上也能跑。Rust uutils 这个项目相当于被微软盖章背书了。

### 7. Microsoft Execution Containers (MXC) — `[Publickey · MS Build 2026]`
<https://www.publickey1.jp/blog/26/aimicrosoft_execution_containers_mxc.html>

微软发布了一个面向 AI Agent 的隔离运行时，专门解决"如果 Agent 跑了 rm -rf 怎么办"这类问题。MXC 可以按工具粒度自定义、支持策略门控，并且和 Agent Framework 集成。对比 Anthropic 的 Project Glasswing、以及目前各家 coding agent 用 Linux namespace 自己糊的沙箱，MXC 把这件事提到了"操作系统的一等概念"层面，思路差别不小。

### 8. 微软自研七个 AI 模型「Microsoft AI Models」一次性发布 — `[Microsoft AI Blog]`
<https://microsoft.ai/news/introducingmai-code-1-flash/>

Build 2026 上微软一口气发了七个自研模型，其中和工程师最相关的是 MAI-Code-1-Flash：小尺寸、低延迟的 coding 模型，定位是嵌在 VSCode 里以及配合新的 Windows Agent 使用。战略层面的解读其实直白——以前微软主要靠分发 OpenAI 模型撑 Copilot，现在自家有了一整条产品线。基准分不算炸裂，但深度集成的故事才是真正卖点。

### 9. Anthropic 服务商通道 + Partner Hub 上线 — `[Anthropic]`
<https://www.anthropic.com/news/services-track-partner-hub>

Anthropic 给 Partner Network 加了正式的服务商等级，并上线 Partner Hub 用来聚合实施合作伙伴、培训、认证。对咨询公司来说这是目前最接近"稳定渠道计划"的东西。对甲方工程负责人来说，这个 Hub 主要价值是当你需要"找人帮我把 Claude Code 在公司铺开但又不想直接招人"时的一份现成短名单。

### 10. 一年里 AI 驱动的网络威胁地图（MITRE ATT&CK 视角）— `[Anthropic · Policy]`
<https://www.anthropic.com/news/AI-enabled-cyber-threats-mitre-attack>

Anthropic 把过去一年观测到的 AI 加持型攻击模式映射到了 MITRE ATT&CK 框架里。关键结论：目前的 AI 加持主要发生在情报侦察、社工 payload 生成、初始访问工具链——不是创造了新的 exploit 类别。这份映射本身就是贡献，给蓝队提供了一套和现有词汇能对得上的"AI 威胁"描述方法。

---

## 编者按

今天属于微软。一半的条目都能追到 Build 2026，另外两条最有意思的非 Build 内容——VSCode Token 漏洞、Anthropic 的 MITRE 报告——本质上都在讲一件事：Agent 和开发工具的安全机制，正在追赶我们已经给它们开放的权限边界。如果只看两条：**#1（VSCode Token 漏洞）** 处理眼下风险，**#7（MXC）** 看一眼中期方向——Agent 沙箱往哪里走。

—— Dev Digest 编辑
