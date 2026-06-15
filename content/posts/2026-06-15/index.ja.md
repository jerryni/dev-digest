---
title: "6月15日 · 今日のテック厳選10本"
date: 2026-06-15T07:00:00+09:00
draft: false
tags: ["digest", "2026-06", "ai", "agents", "security", "webassembly", "postgres", "rag"]
categories: ["daily"]
summary: "AIコーディング支援が、IDEの中の補完機能から、権限・監査・コストを持つ開発基盤へ移りつつあります。WASI、RAG、PostgreSQL、agent skills の話題を中心に拾いました。"
---

## 本日のサマリー

今日は「AI agent をどう運用するか」が軸です。日本の開発現場でも、Copilot の課金変更、Claude 系モデルのアクセス制限、agent skills の安全性、RAG の設計見直しはかなり実務に近い話になってきました。IDE が消えるかどうかより、開発フローのどこに agent を置き、どこで止めるかが焦点です。

---

### 1. Kage：Webサイトをオフライン閲覧用の単一バイナリにする — `[Hacker News · Show HN]`
<https://github.com/tamnd/kage>

Kage は、Webサイトを shadow して単一バイナリとして配布できるツールです。ドキュメントのスナップショット、展示会や顧客先でのデモ、閉域網での参照に向いています。日本企業の社内ポータルや古い業務ドキュメントでも、再現可能なアーカイブ手段として使い道がありそうです。

### 2. Jane Street による形式手法の実践まとめ — `[Hacker News]`
<https://blog.janestreet.com/formal-methods-at-jane-street-index/?from_theconsensus=1>

形式手法というと重く聞こえますが、AI がコードを書く時代にはむしろ現場寄りのテーマになります。仕様、型、検証、プロパティテストのような仕組みがないと、生成されたコードを人間レビューだけで支えるのは厳しい。金融や基盤系だけでなく、複雑な業務ロジックを持つチームにも示唆があります。

### 3. Postgres で大規模削除をスケールさせるなら DROP TABLE — `[Hacker News]`
<https://planetscale.com/blog/the-only-scalable-delete>

大量の `DELETE` は、インデックス、WAL、autovacuum、レプリケーションにかなり重い負荷をかけます。記事では、データ保持期間を前提にした分割と、不要になった単位を `DROP TABLE` する設計が紹介されています。ログ、イベント、監査テーブルを持つサービスでは、後から消すより先に消せる形で作るほうが安くつきます。

### 4. NVIDIA SkillSpector：agent skills の脆弱性を検出する — `[GitHub Trending]`
<https://github.com/NVIDIA/SkillSpector>

NVIDIA の SkillSpector は、AI agent の skills に含まれる危険なパターンや悪意ある挙動を検出するスキャナです。skills は便利ですが、実質的には新しいプラグイン配布形式でもあります。社内で skills を共有するなら、レビュー、権限、依存関係、更新履歴を普通のコードと同じように扱う必要があります。

### 5. Simon Willison：AI はなぜソフトウェアエンジニアを置き換えていないのか — `[Simon Willison]`
<https://simonwillison.net/2026/Jun/14/why-ai-hasnt-replaced-software-engineers/>

Simon Willison が、Arvind Narayanan と Sayash Kapoor の論考を紹介しています。コードを書く部分は速くなっても、何を作るか決めること、正しさを検証すること、事業とコードベースの文脈を理解することは残る、という整理です。現場感としても納得しやすい話で、AI 活用を人員削減だけで語る危うさが見えます。

### 6. WASI 0.3 正式版、WebAssembly Component の非同期処理が共通基盤に — `[Publickey]`
<https://www.publickey1.jp/blog/26/wasi_03webassembly_component.html>

WASI 0.3 では、WebAssembly Component Model における非同期処理が正式な形になりました。これは地味ですが、サーバーサイド WASM、プラグイン実行、edge runtime、sandbox 実行に効く基盤です。AI agent にコードを実行させる場面が増えるほど、WASI のような分離実行の標準化は重要になります。

### 7. Gartner：2027年までに coding agent 利用チームの65％が IDE を必須と考えなくなる — `[Publickey]`
<https://www.publickey1.jp/blog/26/2027ai65ide.html>

予測の数字そのものより、IDE 中心の開発体験が崩れ始めている点が重要です。agent はエディタ内だけでなく、Issue、PR、CLI、タスクキュー、チャットにも出てきます。日本のチームでは、まず agent の作業範囲、レビュー条件、失敗時の責任分界を決めるところから始めるのが現実的です。

### 8. PageIndex で推論ベース RAG を組む — `[Zenn]`
<https://zenn.dev/snaga/articles/2026-06-14-doctools-with-pageindex>

PageIndex は、文書を構造化したツリーとして扱い、LLM が生成した要約を検索キーとして使う考え方です。単純なベクトル類似検索だけでは拾いづらい、長い業務文書や PPT、Excel 混在のナレッジに向いています。社内 RAG で「それっぽいが根拠が弱い」回答に悩んでいるチームは読む価値があります。

### 9. Copilot の従量課金を受けて OpenCode Go を Custom Endpoint として使う — `[Zenn]`
<https://zenn.dev/kusuke/articles/82129236caa5f8>

GitHub Copilot の課金変更をきっかけに、OpenCode Go を VS Code の Copilot Chat Custom Endpoint として使う試みです。モデルやサービスの優劣だけでなく、IDE 統合と月額コストを分離して考える姿勢が参考になります。個人開発者だけでなく、部門単位で AI 開発支援を配るチームにも近い悩みです。

### 10. Anthropic、Fable 5 / Mythos 5 のアクセス停止について声明 — `[Anthropic]`
<https://www.anthropic.com/news/fable-mythos-access>

Anthropic は、米政府の指示により Fable 5 と Mythos 5 のアクセスを停止する必要があると説明しました。他のモデルは影響を受けないとされています。前線のモデルを業務に組み込む場合、性能だけでなく、提供停止、地域制約、代替モデルへの切り替えを運用設計に入れておくべきだと分かる事例です。

---

## 編集後記

本日は 10 本を選びました。英語圏 5、日本語圏 4、Anthropic 公式 1 です。V2EX は取得できましたが、今日の hot は広告と技術的に薄い話題が中心だったため採用しませんでした。Dev Digest 編集としては、まず **SkillSpector** と **WASI 0.3** をおすすめします。agent を便利にする話ではなく、agent を壊れにくく、安全に動かす話だからです。

—— Dev Digest 編集
