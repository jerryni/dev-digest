---
title: "9月18日 · 今日のテック厳選10本"
date: 2026-09-18T07:00:00+09:00
draft: false
tags: ["digest", "2026-09", "ai", "security", "rust", "database", "hardware"]
categories: ["daily"]
summary: >-
  本日は法律向けAI、proofでAIのミスを抑える言語、Rust supply chain攻撃、BrowserSkill、WebMCP、PlanetScale Neki、FUJITSU-MONAKAを取り上げます。
---

## 本日のサマリー

今日は、AIを単体のチャットではなく、法律、ブラウザ操作、GUI開発、フロントエンド連携にどう埋め込むかという話題が目立ちます。もう一つの軸は基盤技術です。Rustのサプライチェーン攻撃、PlanetScaleのPostgreSQLシャーディング、FUJITSU-MONAKAなど、日本の開発者にも関係が深いニュースが並びました。

---

### 1. OpenAI、Astra for Lawを発表 — `[Hacker News]`
<https://openai.com/index/astra-for-law/>

OpenAIのAstra for LawがHNで大きく注目されています。法律調査、文書分析、ケースワークフローにAI agentを組み込む方向で、汎用チャットというより専門業務向けの製品です。日本企業で見るなら、生成品質だけでなく、引用、権限、監査ログ、事実確認、責任分界点をどう設計するかが本題になります。

### 2. Bend、proofでAIのミスを抑える言語 — `[Hacker News]`
<https://bend-lang.com/>

Bendは、CPUとGPUで動き、proofによってAIのミスを防ぐことを掲げる言語です。AIにコードを書かせる前提が広がるほど、型システム、検証、コンパイラによる制約の価値は上がります。言語そのものの成熟度はこれから見る必要がありますが、agent時代のプログラミング言語がどこへ向かうかを考える材料になります。

### 3. Fujitsu、国産次世代CPU FUJITSU-MONAKAを発表 — `[Hacker News]`
<https://global.fujitsu/en-global/pr/news/2026/09/14-02>

Fujitsuが日本製の次世代CPU、FUJITSU-MONAKAを発表しました。AIブームの裏側では、データセンターの電力効率、HPC、国内で制御できる計算基盤がますます重要になっています。日本のエンジニアにとっては、クラウドの上だけでなく、その下にある半導体とサプライチェーンを意識するニュースです。

### 4. Rust crate maintainerを狙う標的型攻撃に注意 — `[Simon Willison]`
<https://simonwillison.net/2026/Sep/17/targeted-attacks-on-rustaceans/>

Simon Willisonが、Rust crates security teamの警告を紹介しています。人気crateのownerやRust関係者を狙い、ビデオ会議や仕事の話を装って端末やアカウントを侵害し、マルウェア配布につなげようとするキャンペーンがあるとのことです。依存関係の安全性は、コードスキャンだけでなく、公開権限を持つ人間の守り方にもかかっています。

### 5. GitHub Trending: Tencent BrowserSkill — `[GitHub Trending]`
<https://github.com/Tencent/BrowserSkill>

TencentのBrowserSkillがGitHub Trendingに入っています。AI agentが、ユーザーの実ログイン状態のブラウザを使いながら、現在の作業を邪魔しないようにするCLIと拡張機能です。便利な一方で、ログイン済みセッション、個人情報、操作確認、監査ログをどう扱うかが重要になります。ブラウザはagentの主要な実行面になりつつあります。

### 6. V2EX: MetaのMuseが使えるようになったという報告 — `[V2EX]`
<https://www.v2ex.com/t/1242834>

V2EXで、MetaのMuseが使えるようになったという投稿が出ています。深い技術解説ではありませんが、AIプロダクトが実際にユーザーへ届いたとき、アクセス条件、体験、既存ツールとの差分がすぐ話題になる点が見えます。日本でも同じで、新モデルの発表より、普段の開発や調査に入るかどうかが評価を左右します。

### 7. V2EX: Jevへの期待と懐疑 — `[V2EX]`
<https://www.v2ex.com/t/1242839>

Jevについて、V2EXではマーケティング先行ではないかという疑問も出ています。こうした温度感は大事です。AI開発ツールは、派手なデモだけでは評価できず、遅延、安定性、コード品質、文脈保持、価格、ローカルな開発習慣への合い方で見られます。導入する側は、小さな評価セットを作って比較したいところです。

### 8. Zenn: vibe codingでGUIが壊れる理由と対策prompt — `[Zenn]`
<https://zenn.dev/nrs/articles/9ba91aea587bf5>

Zennで、vibe codingによってGUIが壊れていく理由と、その対策promptを扱った記事が読まれています。AIは局所的な修正が得意な一方、デザインシステム、余白、状態、既存コンポーネントの一貫性を崩しがちです。日本のフロントエンド現場でも、AIに任せる範囲と、守るべきUI制約を明文化する必要が高まっています。

### 9. Zenn: WebMCPを試してみた感想 — `[Zenn]`
<https://zenn.dev/chot/articles/268804cd6694ab>

WebMCPを試した感想記事です。MCPはagentとツールをつなぐ文脈で語られることが多いですが、WebMCPはその発想をブラウザやフロントエンドアプリへ広げます。SaaSや社内管理画面では、UI状態、権限、実行可能な操作をどの粒度でagentに公開するかが設計テーマになりそうです。

### 10. PlanetScale、PostgreSQL向けシャーディングサービスNekiをプレビュー — `[Publickey]`
<https://www.publickey1.jp/blog/26/planetscalepostgresql11800qpsdbneki.html>

Publickeyによると、PlanetScaleがPostgreSQLのシャーディングを自動化する新DBサービスNekiをプレビュー公開しました。1億1800万QPSという数字も出ていますが、実務上の関心はルーティング、トランザクション、クエリ計画、移行、障害対応をどこまで面倒見てくれるかです。Vitessで知られるPlanetScaleがPostgreSQL側へ踏み込む動きとして注目です。

## 編集後記

本日は10本を選び、内訳はHN 3、Simon Willison 1、GitHub Trending 1、V2EX 2、Zenn 2、Publickey 1です。Anthropic Newsは取得できましたが、新記事の直接URLは確認できませんでした。V2EXは広告・生活系の話題が多かったため、AIツール利用の温度感が見える2本に絞っています。Dev Digest編集部としては、Rustの標的型攻撃、Bend、PlanetScale Nekiを優先して読むのがおすすめです。
