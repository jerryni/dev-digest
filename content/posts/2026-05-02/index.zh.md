---
title: "5月2日 · 今日技术精选"
date: 2026-05-02T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "VSCode", "Copilot", "NetHack", "Ladybird", "Ask"]
categories: ["daily"]
summary: "VSCode 把 Copilot 写进 commit 作者引爆 1500+ 评论，dav2d 给开源世界一个 AV2 解码器选项，NetHack 5.0 时隔多年发布，Ladybird 浏览器进展报告，Ask.com 关停，Russia poisons Wikipedia 引发审稿信任讨论。"
---

## 今日速览

今天 HN 头条是 VSCode 不论用没用都把 "Co-Authored-by: Copilot" 塞进 commit——评论 1500+，开发者社区炸锅。其次 dav2d（VLC/VideoLAN 的 AV2 解码器）开源给视频生态一个新选项。NetHack 5.0 时隔多年发布是经典 roguelike 圈的节日。Ladybird 浏览器月度进展报告也上了首页——这是 2026 年开源浏览器最值得长期关注的项目。

---

## 1. VSCode 不论你用没用都把 "Co-Authored-by Copilot" 写进 commit

来源标签：[EN · HN Top]
链接：<https://github.com/microsoft/vscode/pull/310226>

VSCode 一个 PR 默认在所有 commit 加上 "Co-Authored-by: Copilot"——即使你没启用 Copilot。HN 1500+ 评论一致认为这是产品决策的越界。法律上还有个角度：在 GPL 等强 copyleft 许可下，污染作者归属可能引发版权争议。这条值得国内做开发工具产品的团队记入"产品红线"清单。

## 2. dav2d — 开源 AV2 解码器

来源标签：[EN · HN Top]
链接：<https://code.videolan.org/videolan/dav2d>

VideoLAN 团队发布的 AV2（AV1 的下一代）开源解码器，对应 dav1d 的传承。视频压缩技术每代提升 30%+，做视频/直播的国内团队（B 站、抖音、视频号）都在等这个生态成熟。

## 3. Do_not_track

来源标签：[EN · HN Top]
链接：<https://donottrack.sh/>

把"不要追踪我"这件事做成命令行工具的开源项目——把日常使用的 cookie 同意、第三方追踪等设置自动化。简单直接，有点黑客文化的纯粹感。

## 4. NetHack 5.0.0 发布

来源标签：[EN · HN Top]
链接：<https://nethack.org/v500/release.html>

时隔多年的大版本更新。NetHack 是 roguelike 的活化石——这个项目用社区开发的方式持续了 35+ 年。新版本带来一系列玩法和平衡调整。

## 5. Ladybird 浏览器 4 月进展报告

来源标签：[EN · HN Top]
链接：<https://ladybird.org/newsletter/2026-04-30/>

独立浏览器项目 Ladybird 的月度进展。从零开始重写浏览器引擎，目标 2026 年 alpha——这是当前唯一一个非 Chromium、非 Firefox/Gecko、非 WebKit 的真正能用的开源浏览器实验。生态垄断的反作用力。

## 6. Ask.com 关停

来源标签：[EN · HN Top]
链接：<https://www.ask.com/>

90 年代搜索引擎活到 2026 年终于关闭。一个时代的尾声。HN 评论里有不少老开发者的回忆。

## 7. Russia Poisons Wikipedia

来源标签：[EN · HN Top]
链接：<https://www.bettedangerous.com/p/russia-poisons-wikipedia>

调查报告。俄罗斯有组织地通过 Wikipedia 编辑战术污染条目。对国内做内容产品的团队启示——任何"中立信息源"都会成为意识形态战场，编辑流程的可靠性比信息本身更关键。

## 8. NetHack 5.0 + Ladybird + dav2d：开源世界今天三连发

来源标签：[EN · HN]
链接：<https://nethack.org/v500/release.html>

把今天三条开源大事件串起来读：经典软件长期维护（NetHack）、独立基础设施（Ladybird）、开源音视频生态（dav2d）。这种"非 Big Tech 主导"的工程文化在 2026 年依然在延续，是值得珍视的对照面。

## 9. macOS VM 速度和大小研究

来源标签：[EN · HN]
链接：<https://eclecticlight.co/2026/05/02/how-fast-is-a-macos-vm-and-how-small-could-it-be/>

实测文章——macOS VM 在 Apple Silicon 上能跑多快，能压缩到多小。对国内做 CI/CD 的团队（特别是 iOS 开发）是直接的工程参考。

## 10. 自动驾驶车违章，加州开始开罚单

来源标签：[EN · HN]
链接：<https://www.bbc.com/news/articles/clypjx3rg2go>

加州把自动驾驶汽车纳入交通违法处罚体系。HN 评论很多在讨论"罚金该开给制造商还是车主"。对国内 Robotaxi 团队（百度、小马、文远）也是迟早面对的法律问题。

---

## 编者按

今天的优先阅读：#1（VSCode/Copilot 越界）。这是产品越界的典型案例，所有做 IDE / 编辑器的团队都该把它当一面镜子。Ladybird (#5) 是少有值得长期跟踪的开源项目。今天 NetHack 5.0 / dav2d 这类发布提醒我们：开源生态没死，只是不那么吵闹。
