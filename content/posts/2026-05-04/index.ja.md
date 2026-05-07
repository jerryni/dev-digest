---
title: "5月4日 · 今日のテック厳選10本"
date: 2026-05-04T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "OpenAI", "GitHub", "Bun", "Edge"]
categories: ["daily"]
summary: "GameStopがeBayに555億ドルで買収提案、Microsoft Edgeが全パスワードを平文でメモリ保持、Bunの将来を懸念する記事、OpenAIが低遅延音声AIの基盤を解説、GitHub障害、EUが2027年からスマホ着脱式バッテリー義務化。"
---

## 本日のサマリー

連休中ですが、海外は通常運転。今日の中心話題は3つ。GameStopによる555億ドルでのeBay買収提案（冗談に見えますが本物）、Microsoft Edgeが保存パスワードをプロセスメモリに平文で常時保持していたという脆弱性レポート、そしてBunの将来を懸念する記事。OpenAIは久しぶりに音声AIの低遅延基盤について技術的な詳説を公開。GitHubもまた障害を起こし、「またGitHub」という日常会話が完全に固定化しつつあります。

---

## 1. GameStopがeBayに555億ドルで買収提案

ソース：[EN · HN Top]
リンク：<https://www.bbc.co.uk/news/articles/cn0p8yled1do>

エイプリルフールではありません。GameStopが大量の株式を発行してeBayの買収を提案。HNは「企業価値の逆転、しかし時価総額の差はどう埋めるのか」という現実的議論と、ジョーク混じりの反応が半々。中古ECに対しては大型再編の予兆になります。

## 2. Microsoft Edge、保存パスワードを使用していなくてもメモリに平文で保持

ソース：[EN · HN Top]
リンク：<https://twitter.com/L1v1ng0ffTh3L4N/status/2051308329880719730>

セキュリティリサーチャの発見。Edgeが保存パスワードをプロセス内に平文で常時保持しているため、プロセスメモリを読める任意のマルウェアが認証情報を抽出可能。社内でEdgeを標準ブラウザにしている日本企業は、情シス・SOCに即時共有が必要です。

## 3. 「Bunの将来が心配」

ソース：[EN · HN Top]
リンク：<https://wwj.dev/posts/i-am-worried-about-bun/>

長期Bunユーザーによる懸念表明。リリース頻度の不安定化、issueトリアージの遅れ、商業化の方針が見えない、など複数の運用シグナルを列挙。昨日のZig→Rust移行コミットと同じ週に出ているのは偶然ではない。Node.jsからの移行を検討中の日本企業はもう一段の慎重さが必要。

## 4. OpenAIによる低遅延音声AIの基盤解説

ソース：[EN · HN]
リンク：<https://openai.com/index/delivering-low-latency-voice-ai-at-scale/>

OpenAIにしては珍しい技術深堀り記事。ネットワーク層・モデル層・streaming最適化を全て見直し、人間が「自然」と感じる対話レイテンシ帯に押し込んだ話。日本のコンタクトセンターSaaS、車載音声、医療相談アプリなど、リアルタイム音声を扱うチームは目標値の参考になります。

## 5. GitHub Issues / Webhooks 障害

ソース：[EN · HN]
リンク：<https://www.githubstatus.com/incidents/72q3n8yxthcy>

本日もGitHub障害。Issues、Webhooksが同時影響でCI/CDが詰まる現象。日本のSI現場でも「またか」の空気が一般化し、Single Source of TruthをGitHubに置く設計の見直しを真剣に検討するチームが増えてきました。

## 6. EU、2027年からスマートフォン着脱式バッテリーを義務化

ソース：[EN · HN]
リンク：<https://www.ecopv-eu.com/en/blog-en/replaceable-smartphone-batteries-2027-eu-regulation/>

EU規制で「ユーザが交換可能なバッテリー」が必須化。2027年発効。日本メーカ（ソニーは欧州出荷比率高、Sharp/Fujitsuも一部）は背面構造の再設計が必要に。中古スマホの再生・修理ビジネスにとっては明確な追い風で、PSE認証絡みも含め日本国内政策とどう整合するかが注目点。

## 7. Agent Skills（Addy Osmani）

ソース：[EN · HN]
リンク：<https://addyosmani.com/blog/agent-skills/>

Claude / Cursor / Cline などが「スキル」をどう抽象化しているかの設計論。日本でAIアシスタントを社内開発しているチームは、最新の業界共通パターンを把握する材料に。

## 8. CARA 2.0 — 個人開発の四足ロボット

ソース：[EN · HN]
リンク：<https://www.aaedmusa.com/projects/cara2>

エンジニアリング・ブログ。個人開発者が改良した四足ロボット。日本のメーカーフェア・ロボコン勢、または週末工作派には嬉しい素材。BoMが公開されており、再現性が高い。

## 9. Trademark violation: Mac App Storeに偽Notepad++

ソース：[EN · HN]
リンク：<https://notepad-plus-plus.org/news/npp-trademark-infringement/>

Mac App Storeに登場した偽Notepad++に対する原作者の抗議。Appleの審査プロセスはOSS開発者の商標保護に対して非対称、という古くからの問題が再燃。

## 10. AWS中東UAEリージョン障害（継続）

ソース：[JA · Publickey]
リンク：<https://www.publickey1.jp/blog/26/awsuae2.html>

2か月ぶりの状況報告で復旧見込みは数か月先と判明。中東に拠点を持つ日系商社・物流・ECは、ME-SOUTH-1（バーレーン）またはEU-WEST-1への退避設計が現実的選択。BCP点検は連休明けに先送りせず今週やる話題。

---

## 編集後記

今日の必読は #4（OpenAI 音声AI基盤）でエンジニアリングの実用度が最も高く、#2 + #3 を組み合わせるとプラットフォームソフトウェアのガバナンスリスクが立体的に見えてきます。GitHub障害（#5）は日常雑音化していますが、CIへの影響時間を計測しておく価値があります。
