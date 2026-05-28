---
title: "5月29日 · 今日のテック厳選10本"
date: 2026-05-29T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "anthropic", "claude", "postgres", "aws-kiro"]
categories: ["daily"]
summary: "Anthropicが同日にOpus 4.8とシリーズH 650億ドル調達を発表。AWSはブラウザ完結型のコーディングエージェント「Kiro Web」を投入。ワークフローはまたPostgresに戻ってきました。"
---

## 本日のサマリー

今日のテーマは引き続き「コーディングエージェント」と「ワークフロー基盤の単純化」の2つです。Anthropicが同日にClaude Opus 4.8とシリーズH（投後評価額9650億ドル）を発表、Claude CodeにはDynamic Workflowsが入りました。一方でAWSはブラウザだけで動くKiro Webをリリース。地味なところではDBOSが「durable workflowはPostgresで十分」という記事を出し、HNでも上位に。日本企業の文脈で言えば、社内ガバナンスとAIエージェントの導線設計がいよいよ「製品単位」ではなく「ワークフロー単位」で語られる段階に入った印象です。

## 今日の10本

### 1. Claude Opus 4.8 リリース
**Source: Anthropic · Product**
<https://www.anthropic.com/news/claude-opus-4-8>

Opusクラスのマイナーアップデート。コーディング、エージェント、長時間タスクの一貫性が改善されたとのこと。HN首位（1000+ points）まで上がっており、ロングセッションでの「途中で集中力が切れる」現象が減ったかが論点。日本のSIer・受託系でClaude Codeを業務に組み込み始めているチームには、まず今週中に触ってリグレッションを確認しておきたい変更です。

### 2. Anthropic、シリーズH で650億ドル調達（投後評価額9650億ドル）
**Source: Anthropic · Announcements**
<https://www.anthropic.com/news/series-h>

桁が大きすぎて感覚が麻痺しますが、戦略の読みどころは「計算資源、エンタープライズ、政府領域への継続投資」の三本柱。KPMG・PwCとの提携記事と並べて読むと、日本の大手SIer・コンサル経由でのClaude導入がさらに加速する未来が見えます。逆に言えば、API直接契約のスタートアップにとっては値下げの可能性は短期では薄そう。

### 3. Claude Code に Dynamic Workflows
**Source: Anthropic · Claude blog（via HN）**
<https://claude.com/blog/introducing-dynamic-workflows-in-claude-code>

固定の「/command + skill」を、エージェントが実行中に動的に切り替える設計。要するに「最初にレールを敷く」のではなく「走りながらレールを生やす」モデルです。これはIDE側のAgentic自動化が静的スクリプトから動的オーケストレーションに進化する明確な節目で、CursorやWindsurf、国産勢も追随必至。

### 4. Durable WorkflowはPostgresで十分、というDBOSの主張
**Source: DBOS Blog（via HN #3）**
<https://www.dbos.dev/blog/postgres-is-all-you-need-for-durable-execution>

Temporal、Airflow、Step Functions を持ち出さなくても、Postgresの1テーブル+トランザクションでexactly-once durable executionは成立する、という記事。社内基盤の選定をしている方は一度目を通しておきたい内容。コメント欄では「同時実行性で破綻するのでは」という反論が中心ですが、議論自体が良質です。

### 5. Various LLM Smells
**Source: shvbsle.in（via HN #4）**
<https://shvbsle.in/various-llm-smells/>

「code smell」のLLM版。日々LLMツールを使う中で繰り返し遭遇する"におい"——過剰な謝罪、grepしているふりをして実は推測している、長いコンテキストで前提を忘れる、など——をカタログ化した記事です。読みながらClaude / Cursor / Codexの自分の使い方を点検できる、実務寄りの良コンテンツ。

### 6. SQLite リポジトリに AGENTS.md が現れた
**Source: Simon Willison · Weblog**
<https://github.com/sqlite/sqlite/blob/master/AGENTS.md>

SQLite開発チーム自身が書いたわけではなく、「SQLiteにエージェントを向ける側の人」向けに用意されたAGENTS.md。冒頭から「SQLiteはGitHub Pull Requestを受け付けません」と書いてあるのが象徴的で、上流プロジェクトが"AI向けREADME"でエージェント挙動を抑制しに来た、という新しい潮流です。

### 7. AWS、ブラウザ完結のコーディングエージェント「Kiro Web」発表
**Source: Publickey**
<https://www.publickey1.jp/blog/26/awswebaikiro_web.html>

インストール不要・ブラウザだけで動くAIコーディングエージェント。AWSアカウントがあれば即試せます。社内端末にローカルツールを入れにくい日本企業（特に金融・公共）にとって、Cursor / Claude Codeとは別軸の選択肢が増えた格好。社内PoCの台数を稼ぐ用途には向きそうです。

### 8. VS Code、Agent Window プレビュー
**Source: Publickey（5/15）**
<https://www.publickey1.jp/blog/26/vs_codeaiagent_window.html>

複数のAIエージェントを1つのWindowで並列実行できる機能。今週のZennでも「Cursor 3のAgent Windowを2週間使った所感」が上位にきていて、UI側の事実上の標準が「マルチエージェント前提」に動いていることがよく分かります。チーム内ガイドラインを更新しておきたい段階。

### 9. .NET MAUI、ついにMonoランタイムを脱却しCoreCLRへ
**Source: Publickey**
<https://www.publickey1.jp/blog/26/mononet_mauixamarinmonocoreclr.html>

Xamarinから続いてきたMonoランタイムが.NET MAUIから外れ、CoreCLRに移行。地味ですが、長らく.NETモバイル界隈の足を引っ張ってきたデバッグ・パフォーマンス問題が一段解消される見込み。社内に.NET / MAUI資産がある会社は、移行計画を早めに引いておくと吉。

### 10. Docker専用AIエージェント「Gordon」が正式リリース
**Source: Publickey**
<https://www.publickey1.jp/blog/26/dockeraigordondocker.html>

Docker社が出した、Dockerに関することなら何でも答え、エラー修正までしてくれるエージェント。無料アカウントでも使えます。Dockerfileの最適化や謎のbuild失敗の調査など、これまで`docker logs`と睨めっこしていた時間を圧縮してくれそう。日本の現場でも採用は早そうな印象。

## 編集後記

今日のテーマを一言でまとめるなら、「モデルが強くなり、編成が薄くなる」。**#4（Postgres durable workflow）** と **#3（Dynamic Workflows in Claude Code）** の2本は、別レイヤーの話ですが、どちらも「特化基盤よりも単純な土台＋動的な制御」へ寄せていく流れの一部です。今日はGitHub Trendingが応答サイズで取り切れず、ZennトレンドAPIも当日新鮮なトップ記事を返さなかったため、JA枠はPublickey中心に組みました。
