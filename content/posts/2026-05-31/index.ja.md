---
title: "5月31日 · 今日のテック厳選10本"
date: 2026-05-31T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "anthropic", "sqlite", "zig", "ai-agent", "mcp", "dotnet"]
categories: ["daily"]
summary: "Anthropic が 9650 億ドルの評価額で Series H を完了し Opus 4.8 も投入。コミュニティでは MCP の終焉論と SQLite による永続ワークフロー論が並行進行。AWS Kiro Web、.NET MAUI の CoreCLR 移行も。"
---

## 本日のサマリー

週末でも資本と工程の話題は止まりません。Anthropic は一夜にして 9650 億ドルの評価額に達し、Opus 4.8 もリリース。AWS は「ブラウザだけで動くコーディング AI エージェント Kiro Web」を出し、日本国内で需要が大きい .NET MAUI もついに Mono ランタイムを脱却して CoreCLR に統一されます。MCP の有効性や SQLite による永続ワークフローの妥当性も再評価されはじめ、エージェント基盤の再構築フェーズに入ってきた感覚です。

## 今日の10本

### 1. Anthropic が Series H で 650 億ドル調達、評価額 9650 億ドルに

ソース：Anthropic Newsroom · [リンク](https://www.anthropic.com/news/series-h)

OpenAI 以外で初の 1 兆ドル接近です。日本企業視点で見ると、KPMG・PwC との大型提携が立て続けに来ている流れの延長線上にある資金調達で、来期は国内エンタープライズ営業がさらに強化されるはず。社内導入を検討しているなら、日本リージョンの SLA とサポート体制の更新情報も追っておくのが良いでしょう。

### 2. Claude Opus 4.8 リリース

ソース：Anthropic Newsroom · [リンク](https://www.anthropic.com/news/claude-opus-4-8)

「コーディング、エージェントタスク、長期ワークの一貫性」を強化したとのこと。Opus 系のアップグレードは Claude Code を業務で常用しているチームほど体感差が大きいので、明日月曜に普段のリファクタリングタスクで一度ベンチマークを取ってみるのを推奨。料金体系は据え置きの模様です。

### 3. SQLite is all you need for durable workflows

ソース：obeli.sk via Hacker News · [リンク](https://obeli.sk/blog/sqlite-is-all-you-need-for-durable-workflows/)

Temporal や Cadence といった重量級のワークフローエンジンを使わずに、SQLite をイベントログとして使えば十分という主張。HN で本日 630 ポイント。日本の SaaS スタートアップ規模だと正直この構成で大半カバーできてしまうことが多く、運用心理コストの低さは無視できません。Inngest や Temporal の導入を社内で検討中のチームは目を通しておきたい記事です。

### 4. Zig: Build System 大幅再設計

ソース：ziglang.org via Hacker News · [リンク](https://ziglang.org/devlog/2026/#2026-05-26)

Zig のビルドシステムは長らく賛否両論でしたが、今回 graph を first-class にした再設計が入りました。C/C++ の置き換え候補として Zig を評価している組み込み系・ゲーム開発系では地味に重要なアップデートです。

### 5. The Last Technical Interview (Steve Yegge)

ソース：Steve Yegge on Medium via Hacker News · [リンク](https://steve-yegge.medium.com/the-last-technical-interview-bc13ddcf4564)

ホワイトボードでのアルゴリズム面接はもう機能していない、AI 支援のペアコーディング型に移行すべきという議論。日本企業の中途採用ではコーディング試験を Track Test や HackerRank に丸投げするパターンが定着していますが、「Copilot 使っていいですよ」と言える面接が今後どこまで広がるか、エンジニア側からも先に問うていくべきテーマです。

### 6. MCP is dead?

ソース：quandri.io via Hacker News · [リンク](https://www.quandri.io/engineering-blog/mcp-is-dead)

煽り気味のタイトルですが論点は真っ当で、MCP（Model Context Protocol）の進化速度に対して、Agent Skills や native function calling 拡張といった代替が先に普及しているのではという指摘。日本のスタートアップで MCP サーバを社内向けに整備中のところは、設計判断の前に一読の価値あり。

### 7. AWS Kiro Web 発表：ブラウザから使えるコーディング AI エージェント

ソース：Publickey · [リンク](https://www.publickey1.jp/blog/26/awswebaikiro_web.html)

インストール不要というのが効きどころで、社用 PC の権限が厳しい大企業環境ではこのフォームファクタが響きそうです。Claude Code や Cursor の代替候補として、AWS アカウントを既に持っている組織は試してみる価値あり。

### 8. .NET MAUI、ついに Mono を脱却して CoreCLR へ

ソース：Publickey · [リンク](https://www.publickey1.jp/blog/26/mononet_mauixamarinmonocoreclr.html)

Xamarin 時代から引き継がれた Mono ランタイムが終わり、CoreCLR に統一。.NET MAUI でクロスプラットフォームのモバイルアプリを保守しているチームには、起動時間・GC 挙動・AOT 関連の挙動が変わるという意味でかなりインパクトのある変更です。早めに dev branch で互換性確認したい。

### 9. ブラウザで動く Android システム（V2EX 自薦）

ソース：V2EX · [リンク](https://www.v2ex.com/t/1216344)

「数百億トークン燃やして作った」とのこと。Vibe coding で従来工数なら数四半期かかるものが個人プロジェクトとして成立しはじめている、という事例として観察する価値あり。技術的なアプローチ自体は投稿元の議論を見ながら判断を。

### 10. AI に飼い慣らされた話：月 0 円から 1200 元（約 24,000 円）に

ソース：V2EX · [リンク](https://www.v2ex.com/t/1216578)

中国の個人開発者の AI 課金推移の生々しい記録。日本の個人エンジニア視点でも、Claude Max + Cursor + ChatGPT Plus のフルスタック契約はだいたい月 3 万円前後に収束する人が増えている感覚で、コメント欄で議論されている「この支出が何の作業を肩代わりしたか」が読みどころです。

## 編集後記

今日の裏テーマは「基盤層のシャッフル」です。SQLite で永続ワークフロー、MCP の存在意義、Zig のビルドシステム再設計、.NET MAUI の Mono 脱却——どれも下層インフラの再配置。Anthropic の資金調達はその速度をさらに上げる燃料です。一本だけ読むなら **SQLite is all you need for durable workflows** — 自社のワークフロー基盤がオーバーエンジニアリングになっていないか、見直すきっかけとして秀逸です。次点は **MCP is dead?**。
