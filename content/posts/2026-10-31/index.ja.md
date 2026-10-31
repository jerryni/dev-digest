---
title: "10月31日 · 今日のテック厳選10本"
date: 2026-10-31T07:00:00+09:00
draft: false
tags: ["digest", "2026-10", "ai", "security", "devtools"]
categories: ["daily"]
summary: "AI を開発現場へ入れるときに見える、拡張機能の信頼、記憶、データ基盤、権限設計を追います。"
---

## 本日のサマリー

今日はモデルの性能競争より、その周囲の運用設計が主役です。拡張機能の供給網、エージェントの記憶、データ処理の配置、そしてユーザーに代わって動く仕組みの境界を、各地域の話題から拾いました。

## ピックアップ

### 1. [Cursor Marketplace で Claude Code を装う拡張機能にバックドア](https://phorion.io/blog/offical-claude-code-vsx-compromise/)
`HN · EN`

見た目が公式らしいことは、もはやインストール判断の根拠になりません。開発ツールの拡張機能はソース確認、発行者の検証、バージョン固定、通信先の監視まで含めて扱うべきです。コーディングエージェントを使う組織ほど、まずこの入口を棚卸ししたいところです。

### 2. [claude-mem：Claude Code の会話をまたいだ記憶](https://github.com/thedotmack/claude-mem)
`GitHub Trending · EN`

作業を再開するたびに背景を説明し直す問題に、観測・圧縮・検索で対応するプロジェクトです。便利さの裏では、コードや判断の断片が新しい保存対象になります。導入時は品質だけでなく、保持期間、秘匿情報、共有範囲を先に決めておくと安心です。

### 3. [GitHub Octoverse 2026 を読む](https://simonwillison.net/2026/Oct/28/github-octoverse-2026/)
`Simon Willison · EN`

Simon Willison の読み解きは、エージェント開発を印象論から少し離して考える材料になります。統計がそのまま現場の生産性を示すわけではありませんが、採用やプラットフォーム選定には影響します。自社では、任せる工程と人がレビューする責任を分けて測るのが先決です。

### 4. [Apple Intelligence の中国展開をめぐる議論](https://www.v2ex.com/t/1253336)
`V2EX · ZH`

端末側の機能、クラウド処理、地域ごとのサービス条件がどこで分かれるかが焦点です。利用者向けアプリを作る側は、提供開始のニュースだけでなく、機能検出とフォールバックを確認したいです。地域差を後付けの例外にしない設計が効きます。

### 5. [時刻境界を扱うバイリンガル MCP ツール](https://www.v2ex.com/t/1253340)
`V2EX · ZH`

夏時間などの面倒な境界条件を MCP 経由で利用可能にした個人開発です。小さなツールほど、入力と出力の契約を明確にする練習になります。個人データや重要な判断につながる用途では、呼び出し前の確認と監査可能な記録を残したいです。

### 6. [Bun の Prettier 互換フォーマッタ](https://www.publickey1.jp/blog/26/javascriptbunprettier300prettier.html)
`Publickey · JA`

既存設定を使いつつ高速化できる点は、巨大リポジトリや保存時フォーマットで魅力的です。ただし速度の数字だけで置き換えると、出力差やプラグイン、CI とのずれで困ります。まずは一つのパッケージで差分を検証するのがよさそうです。

### 7. [DuckDB 2.0 LTS 正式リリース](https://www.publickey1.jp/blog/26/duckdb_20_ltsquack.html)
`Publickey · JA`

クライアント/サーバ機能や非同期処理の話は、DuckDB の使い方が広がる兆しです。組み込み分析として使うのか、共有サービスとして置くのかで、障害対応とデータ管理の責任は大きく変わります。LTS を機に、接続境界と同時実行の前提を見直す価値があります。

### 8. [Claude による創薬加速の初期事例](https://www.anthropic.com/research/early-progress-drug-development)
`Anthropic News · wildcard`

公式記事は、研究者の検索や仮説整理を短くする支援として位置付けています。モデルが結論を代替する、というより検証可能な途中成果を増やす使い方です。専門領域のエージェントを作る際にも、根拠と引き継ぎを残す設計の参考になります。

### 9. [Agent Skills を Agentic AI Foundation へ寄贈](https://www.anthropic.com/news/donating-agent-skills-to-the-agentic-ai-foundation)
`Anthropic News · wildcard`

エージェントの作業単位が、個別のプロンプトから共有可能な部品へ移ろうとしています。互換性が高まるほど、スキルが要求する権限と来歴の確認は重要です。採用時には、機能数よりも権限宣言と実行ログを確認したいです。

### 10. [Claude 運用のマーケットプレイス実験](https://www.anthropic.com/features/project-deal)
`Anthropic News · wildcard`

代理で取引や運用を行う仕組みでは、生成品質よりも上限、取消、例外時の扱いが難所になります。実験の事例は、その境界を設計するヒントとして読めます。ユーザーの代わりに操作する機能には、人の承認と追跡可能な履歴を最初から組み込みましょう。

## 編集後記

本日の共通項は、AI を使うことではなく、安全に使い続けるための境界です。特に拡張機能の供給網と DuckDB 2.0 LTS は、今週の実務に持ち帰りやすい二本です。Zenn は取得できたトップページから記事カードを識別できなかったため、無理に選出していません。
