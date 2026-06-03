---
title: "6月4日 · 今日のテック厳選10本"
date: 2026-06-04T07:00:00+09:00
draft: false
tags: ["digest", "2026-06", "microsoft-build", "anthropic", "vscode", "security", "codex", "windows"]
categories: ["daily"]
summary: "Microsoft Build 2026 二日目が大暴れ。自社製AIモデル7種、エージェント用サンドボックスMXC、WSL containers、Windows標準のcoreutilsまで一気に発表。VSCodeのワンクリックでGitHubトークンが抜かれる脆弱性も。Anthropicはパートナー網を拡張、AI攻撃の年次レポートも公開。"
---

## 本日のサマリー

本日のフィードは Microsoft Build 2026 がほぼ独占しています。Redmond は今回、Linux/macOS に流れた開発者を Windows 側に取り戻しに来ている印象です。自社製 AI モデル7本、エージェント単位の隔離ランタイム MXC、WSL 上で動く本物の Linux コンテナ、そして Windows 11 標準搭載となる Rust 製の GNU coreutils（`ls`・`cat`・`cp` がエイリアスではなく本物になる）。セキュリティ面では `ammaraskar` 氏による VSCode のワンクリック GitHub トークン窃取の解説が秀逸で、社内 IDE 標準が VSCode の企業はセキュリティ担当が午後に動き出すかもしれません。Anthropic 側もパートナーネットワークにサービストラックを新設し、AI 関与型サイバー攻撃を MITRE ATT&CK で分類した報告書を公開しています。

---

### 1. VSCodeのワンクリックでGitHubトークンが盗まれる — `[Hacker News · 579 pts]`
<https://blog.ammaraskar.com/github-token-stealing/>

workspace trust の回避を悪用し、悪意あるリポジトリを開くとワンクリックで GitHub OAuth トークンが外部へ送信される脆弱性です。URL ハンドラ悪用の流れと開示タイムラインを丁寧に解説しており、技術的ハッタリがありません。VSCode + GitHub 拡張で外部 fork の PR レビューを日常的に行っているなら、本日の必読です。Microsoft は修正済みですが、コンプライアンス都合でバージョン固定している組織は多いので、社内のバージョン確認をおすすめします。

### 2. Every Byte Matters — `[Hacker News · 166 pts]`
<https://fzakaria.com/2026/06/01/every-byte-matters>

ホットパス上で 1 バイトの無駄がもたらすコストを、キャッシュライン・ページフォルト・分岐予測・現代アロケータの暗黙のアラインメントといった観点で丁寧に検証する長文記事です。著者は実測値で議論を組み立てているので、結論をそのまま自社サービスに持ち帰りやすいのが良いところです。読み終わったら `perf stat` で自分の現場を測ってみると、なかなか正直な午後になります。

### 3. Simon Willison：Codex Desktop で「ペースト→ファイル化」エディタを一発生成 — `[Simon Willison]`
<https://tools.simonwillison.net/pasted-file-editor>

長文をペーストするとファイル添付に変換してくれるエディタを Simon が公開しました。Claude.ai および Claude デスクトップアプリの「長文ペーストを自動でファイル化する」挙動を再現したツールです。注目すべきは制作プロセスで、Codex Desktop に 1 つのプロンプトを渡しただけで全体が出来上がっています。「AI に社内向け小ツールを 1 段落で作らせる」というワークフローは、いよいよ標準的な開発スタイルとして根付いてきました。

### 4. Codex 最新版（26.601.21317）アップグレード注意 — `[V2EX · 程序員]`
<https://www.v2ex.com/t/1217473>

最新版 Codex デスクトップでアジア圏ユーザーの認証フローが壊れる事象が多発しており、スレッドには症状と動作確認済みのダウングレード手順が集まっています。CI や commit-on-save で `codex` に依存している場合は、修正版が出るまで数日待つ方が安全です。

### 5. スマホから Claude Code / Codex を遠隔操作するターミナル App — `[V2EX · 分享创造]`
<https://www.v2ex.com/t/1217542>

`rwecho` 氏がモバイル端末用のターミナル App を公開しました。リモートの Claude Code または Codex セッションへのプロキシとして動作し、UI は ssh というよりチャットクライアントに近い設計です。1 プロンプトで完結する作業がどれだけ占めるかで実用度は変わりますが、「コーディングエージェントを IDE の中ではなく、独立してアドレス可能な実体として扱う」という発想の良いサンプルです。通勤電車での軽い修正には向きそうです。

### 6. Coreutils for Windows 一般公開 — `[Publickey · MS Build 2026]`
<https://www.publickey1.jp/blog/26/unixwindowscoreutils_for_window.html>

Microsoft が GNU coreutils を Rust で再実装したものを Windows 11 標準コンポーネントとして提供します。`ls`、`cat`、`cp`、`mv`、`rm` などが OS 標準で使えるようになり、PowerShell の alias による「だいたい同じ」運用から解放されます。クロスプラットフォーム Makefile や shell スクリプト系の自動化を素の Windows VM 上で素直に動かせる意味は大きく、Rust uutils プロジェクトには大きな追い風となります。

### 7. Microsoft Execution Containers（MXC）— `[Publickey · MS Build 2026]`
<https://www.publickey1.jp/blog/26/aimicrosoft_execution_containers_mxc.html>

「エージェントが `rm -rf` を実行したらどうする問題」に正面から向き合った、AI エージェント専用の隔離ランタイムです。ツール単位でカスタマイズ可能、ポリシーゲートあり、Agent Framework と統合済みという構成。Anthropic の Project Glasswing や、各社が Linux namespace で手作りしているサンドボックスと比較すると、MXC は「OS の一等概念」としてサンドボックスを再定義してきた点が際立ちます。

### 8. Microsoft 自社製 AI モデル「Microsoft AI Models」7 種一斉発表 — `[Microsoft AI Blog]`
<https://microsoft.ai/news/introducingmai-code-1-flash/>

Build 2026 で Microsoft が自社開発の AI モデル 7 種を一気に公開しました。エンジニア視点で最も関係するのは MAI-Code-1-Flash で、低遅延・小サイズのコーディング特化モデルです。VSCode 組み込みおよび新しい Windows Agent との統合を想定しています。戦略的には明快で、OpenAI モデルの再販に頼ってきた Microsoft が自社の本格的なモデルファミリーを持つに至ったということです。ベンチマーク自体は派手ではありませんが、深い統合こそが本当のプロダクトです。

### 9. Anthropic Services Track と Partner Hub — `[Anthropic]`
<https://www.anthropic.com/news/services-track-partner-hub>

Anthropic が Partner Network 内にサービス事業者向けの正式なトラックを新設し、実装パートナー・トレーニング・認定をまとめた Partner Hub を公開しました。コンサル・SI 各社にとっては、これまでで最も「チャネルプログラムらしいチャネルプログラム」です。事業会社側からは、Claude Code を社内展開する際の SI 候補リストとしての価値が大きいと言えます。

### 10. Anthropic：AI 関与型サイバー脅威を MITRE ATT&CK で整理した 1 年分の知見 — `[Anthropic · Policy]`
<https://www.anthropic.com/news/AI-enabled-cyber-threats-mitre-attack>

Anthropic が過去 1 年間に観測した AI 関与型脅威パターンを MITRE ATT&CK フレームワークにマッピングしたレポートを公開しました。主要な所見は、現状の AI による底上げは偵察・ソーシャルエンジニアリング向けペイロード生成・初期侵入ツール周辺に集中しており、新規の exploit カテゴリを生み出してはいないという点です。マッピング自体が貢献であり、ブルーチームが既存の語彙のまま AI 脅威を議論できるようになります。

---

## 編集後記

本日は Microsoft の日でした。掲載項目の半数が Build 2026 由来であり、Build 以外の 2 本（VSCode トークン脆弱性、Anthropic の MITRE マッピング）も「エージェントや開発ツールに与えてきた権限に、セキュリティ機構がやっと追いつき始めた」という同じ流れに乗っています。2 本だけ読むなら、**#1（VSCode トークン脆弱性）** で目の前のリスクを処理し、**#7（MXC）** で中期的なエージェントサンドボックスの方向性を押さえるのがおすすめです。

—— Dev Digest 編集部
