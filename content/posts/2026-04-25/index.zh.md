---
title: "4月25日 · 今日技术精选"
date: 2026-04-25T07:00:00+09:00
draft: false
tags: ["digest", "2026-04", "ai", "anthropic", "deepseek", "openai", "开源", "ruby"]
categories: ["daily"]
summary: "今天的 AI 圈上下两半对撞：一边是 Google 据传要给 Anthropic 注资高达 400 亿美元、OpenAI 把 GPT-5.5 正式送进 API；一边是'我注销了 Claude'长文 695 分上 HN 头条，Simon Willison 连夜回应质量质疑。DeepSeek v4 悄悄上线，1757 分拿下全天最高票。另外：Matz 给 Ruby 做了 AOT 原生编译器。"
---

## 🌏 今日速览

24 小时内三股力量同时出现：**资本继续集中**（Google 据报要再砸 400 亿美元进 Anthropic）、**质量抱怨集中爆发**（"我注销了 Claude"一篇长文冲到 HN 第一，Simon Willison 当天回应）、**开源反击继续加码**（DeepSeek v4 1757 分登顶全天最高票）。OpenAI 顺便把 GPT-5.5 挪到正式 API。V2EX 今天最热的讨论是"AI 带来的革命性改变，为何还没发生"——国内开发者的判断普遍冷静。场外：Matz 给 Ruby 做了 AOT 原生编译器。

---

## 🔥 今日 10 条

### 1. [DeepSeek] DeepSeek v4 API 文档上线
**链接：** https://api-docs.deepseek.com/
HN 全天第一，1757 分——几乎没发公告就把发布给"完成"了。v4 在代码、推理、长上下文上都看到了预期的台阶；更关键的是价格——DeepSeek 一贯比前沿闭源便宜大约一个数量级的位置还在。对国内团队来说这意义更直接：DeepSeek 是少数在合规链路上不需要额外解释的前沿模型，今天开始它也是**"同价位能力最强"的参考点**。拿 Claude/GPT-5.5 做成本测算的，今天起基线要换了。

### 2. [Bloomberg via HN] Google 据报将向 Anthropic 追加投资至多 400 亿美元
**链接：** https://www.bloomberg.com/news/articles/2026-04-24/google-plans-to-invest-up-to-40-billion-in-anthropic
叠加在上周 Google ↔ Anthropic ↔ Broadcom 的 TPU 产业链协作之上。对 Anthropic 来说算理简单：训练算力不再是瓶颈。对 Google 来说是对"Gemini 独苗"的对冲。对市场来说，隐含估值把 Anthropic 抬到 OpenAI 同一重量级——"创业小而美"的定位彻底翻篇了。对国内从业者来说更重要的引申：美国前沿大模型的资本密度还在加厚，追赶不靠钱已经不现实。

### 3. [HN / nickyreinert.de] 我注销了 Claude——额度问题、质量下滑、支持糟糕
**链接：** https://nickyreinert.de/en/2026/2026-04-24-claude-critics/
HN 695 分 405 评论——单个用户发牢骚能打到这个量级，本身就是信号。具体抱怨不特别（套餐额度混乱、感觉质量下降、客服冷漠），但共鸣面很广。配合 Simon Willison 当天的回应（[An update on recent Claude Code quality reports](https://simonwillison.net/2026/Apr/24/recent-claude-code-quality-reports/)）一起读。对重度依赖 Claude 的团队来说：本周建议把 fallback 路径写进文档。

### 4. [HN / developers.openai.com] OpenAI 把 GPT-5.5 / GPT-5.5 Pro 放进正式 API
**链接：** https://developers.openai.com/api/docs/changelog
昨天的发布日产品今天就进了正式 changelog——没有特殊灰度、常规定价、Codex CLI 可直接对上。对国内走 API 中转的团队：这一步意味着"稳定可做大规模"，而不是"需要排队抢"。与 #3 的 Claude 抱怨潮结合看：OpenAI 有底气让所有人一起压——技术侧对自己当前的吞吐有信心。

### 5. [GitHub / HN] Spinel：Ruby 的 AOT 原生编译器，作者是 Matz
**链接：** https://github.com/matz/spinel
HN 287 分。Ruby 之父亲自下场做 AOT——不是 transpile、不是 mruby，是真正把 Ruby 编译成原生二进制的路径。目前还早，支持的子集不完整，但信号本身很关键："Ruby 能不能做成单文件发布"这个讨论，主线维护者第一次认真回应了。对国内曾经因为启动速度放弃 Ruby 的服务端团队，值得做个 POC 看看。

### 6. [kevinlynagh.com] 用"过度思考、范围蔓延、结构性 diffing"毁掉自己的项目
**链接：** https://kevinlynagh.com/newsletter/2026_04_overthinking/
HN 326 分。作者复盘自己把好几个项目做砸的三种具体失败模式——每一种都带着自己真实的事后剖析。其中"结构性 diffing"作为一种拖延症的提法最精彩——你在"该不该重写"这个决策前读一遍，省下来的时间远不止一个下午。推荐给任何一个最近一直在改架构 PPT 的 Tech Lead。

### 7. [Simon Willison] Bluesky "For You" 信息流是怎么服务的
**链接：** https://simonwillison.net/2026/Apr/24/serving-the-for-you-feed/
Simon 转了 Bluesky/ATProto 官方的一篇纯工程博客——排序模型、特征管线、缓存层、延迟预算全都摊开讲。他给的评价是"当前能找到的开源 For You 参考实现里最完整的一个"。对国内做短视频/社区推荐的同学：这是可以直接拿来对标的开源样本，过去只能靠抖音/小红书论文逆向猜的问题，现在有了正面文本。

### 8. [V2EX] "AI 带来的革命性改变，为何还没发生"
**链接：** https://www.v2ex.com/t/1207970
今天 V2EX 最热的一条。国内开发者集体冷静复盘：两年多的 AI 叙事是否真带来了"工作流革命"。主流结论是——**"AI 成了不错的初级贡献者，但 10x 生产力的故事只在定义清晰、测试齐全的代码库里成立"**。对正在做 PR 说自己"100% AI 原生"的团队来说，是一次外部校准。

### 9. [V2EX] 做了一个自己的 AI 中转站，球球 Token，现支持 CodeX 和 Claude Code
**链接：** https://www.v2ex.com/t/1207949
今天的 V2EX 热帖，作为产品不算惊艳，作为"市场切片"很有价值。国内开发者靠中转站/代充来绕前沿模型的区域限制——灰色、但规模和技术成熟度都真实存在。这种生态的存在感越大，反推的结论是："在正规渠道里，国内用户其实买不到 Claude Max / Codex 的全功能"。OpenAI / Anthropic 的亚太策略，需要解决这件事。

### 10. [Publickey] Vercel 开源 wterm——WebAssembly 实现的浏览器终端模拟器
**链接：** https://www.publickey1.jp/blog/26/vercelwebwtermwebassemblyweb.html
Vercel 发布 wterm（念"dub-term"），核心用 Zig 写、编译成 WebAssembly，但画面仍用 DOM 渲染——所以浏览器的选中、复制粘贴、Ctrl+F 都能原生工作。定位不贪大：给 Web IDE、文档站、交互教程提供可嵌入的终端。一直拿 xterm.js 做教程/沙盒的团队可以认真评估一下——Zig + WASM 的组合在同类里算是少见但合理。

---

## ✍️ 编者按

今天的格局几乎是小说式的：**顶层的故事**（Google 400 亿、OpenAI API 上架、DeepSeek 登顶）和**底层的故事**（用户注销 Claude、质量投诉发酵）在同一天平行发生，互不相让。这中间的落差，就是未来半年到一年里"建在 API 上的产品"的工作空间。

**必读两条：**
1. **DeepSeek v4（#1）**——今天最值钱的能力/价格组合事件，也是对闭源定价最直接的压力阀。
2. **"我注销了 Claude" + Simon Willison 回应（#3）**——两篇对照着看，是目前关于"开发者对 Agent 工具信任度"最清晰的一次读数。

— Dev Digest 编辑
