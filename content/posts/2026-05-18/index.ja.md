---
title: "5月18日 · 今日のテック厳選10本"
date: 2026-05-18T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "セキュリティ", "SQLite", "Anthropic", "Bun", "ストレージ"]
categories: ["daily"]
summary: "honker.dev が SQLite 1 ファイルに永続キュー・pub/sub・cron を詰め込み、Simon Willison は datasette-llm-limits で LLM 課金の上限を仕組み化。openwall ではゼントー開発者を飛ばした脆弱性公開の話が再燃。Bun の Rust 移行には Zig コミュニティが公開状で反応。"
---

## 本日のサマリー

月曜の主軸は3つです。1つ目は「ツール層の小さな美学」。honker.dev は永続キュー・ストリーム・pub/sub・cron をすべて単一の SQLite ファイルに同居させ、Simon Willison は Datasette 用に LLM 課金を上限管理する `datasette-llm-limits` を出しました。AI 時代のバックエンドが「ミドルウェアの数で殴る」より「責任範囲を絞る」方向に寄り直している兆しです。2つ目はサプライチェーンと脆弱性公開の倫理。openwall に出た「CopyFail を Gentoo メンテナに通知しなかった」議論が HN で 312 点に。3つ目は大型インフラの巻き戻し。比利時の原発廃炉中止と Rivian の「車両ネットワークを完全に切る」スイッチ — どちらも 2024〜25 年に「もう決まった」とされた流れに、社会と市場が正面から修正を入れています。

## 本日の10本

### 1. honker.dev — SQLite 1 ファイルに永続キュー・ストリーム・pub/sub・cron をまとめる（HN · EN）

[公式：honker.dev](https://honker.dev/) ・ [HN スレッド](https://news.ycombinator.com/item?id=47963316)

組み込みプロセスから SQLite を叩くだけで、durable queue とストリームと pub/sub と cron スケジューラが揃う、というツールです。HN で 158 点、コメント欄では NATS・Redis Streams との比較が活発でした。日本のスタートアップ／中小 SaaS にとっては、「PMF 前に Kubernetes と Redis と DLQ を揃えるよりまず 1 ファイルで動かす」という選択肢が現実味を帯びてきたという話。運用負荷を 1 人ぶん圧縮できるなら検討する価値があります。

### 2. CopyFail：Gentoo メンテナに通知されなかった脆弱性開示、Forgejo にも余波（HN · EN）

[openwall ML](https://www.openwall.com/lists/oss-security/2026/04/30/10) ・ [Forgejo の続報](https://dustri.org/b/follow-up-to-carrot-disclosure-forgejo.html) ・ [HN スレッド](https://news.ycombinator.com/item?id=47965108)

脆弱性報告者が上流の一部にしか開示せず、Gentoo のような影響を受けるディストロには連絡が回らなかった、という事案です。HN 312 点。コメントを読むと「開示は1社ではなく依存グラフ全体に対して行うべき」という主張が繰り返されています。日本企業の OSS 利用ガイドライン作成時に、悪い例として参照するとよい記録になりそうです。

### 3. Simon Willison が `datasette-llm-limits` を公開 — LLM 課金の上限をインフラ層で持つ（Simon Willison · EN）

[原文 simonwillison.net](https://simonwillison.net/2026/May/15/)

`datasette-llm-accountant` と組み合わせ、ユーザー単位（または全体）で LLM 呼び出しの上限を設定できるプラグインです。技術的に派手なことはしていません。要点は「課金の上限管理を上司のリマインドではなく、コードの責務にした」こと。社内 LLM ゲートウェイを運用する人にとっては、設計のとっかかりとして参考になります。

### 4. V2EX：「Bun の Rust 移行に対する、Zig コミュニティからの公開状」（V2EX · ZH）

[原帖 v2ex.com/t/1213191](https://www.v2ex.com/t/1213191)

Bun が Zig から Rust への移行を発表したことに対して、Zig コミュニティが公開状で応答。「移行は自由だが、Zig が未熟であるかのようにマーケティング素材で扱わないでほしい。具体的な問題は私たちが修正のロードマップを示せる」という、抑えたトーンです。中国語スレでは「Zig は組織的に大きな後ろ盾がないという構造問題」と「Bun の今回の移行こそ Claude Code が人件費を圧縮した実例」という二系統の議論が並走しています。5/12 の Publickey 記事と合わせ読みたいところ。

### 5. V2EX：macOS Finder の右クリック拡張ツール iRight を作った人の記録（V2EX · ZH）

[原帖 v2ex.com/t/1213192](https://www.v2ex.com/t/1213192)

「圧縮」「一括リネーム」「パスのコピー」など、毎日触る機能を Finder の右クリックに載せた個人開発ツールです。コードよりも、コメント欄に集まった「Apple Silicon 以降も生き残っている Finder 拡張」の比較が読み物としてよくできています。PathFinder、Default Folder X、Forklift などの現在地が分かるので、Mac で仕事する人は一度通すと良い棚卸しになります。

### 6. Anthropic、AWS 上で Claude Platform を正式提供。新機能の遅延配信が解消（Publickey · JA）

[Publickey 原文](https://www.publickey1.jp/blog/26/anthropicawsclaude_platform_on_awsclaudeaws.html)

これまで AWS Bedrock 上の Claude は「直接契約より一拍遅れて機能が来る」状態でしたが、Claude Platform on AWS が正式版になり、フルセットが同期して使えます。日本企業の調達／監査要件で AWS Japan 経由が必須のケースは多く、「Bedrock ではこれが使えない」を毎四半期確認していた SRE には地味に効くアップデートです。社内 Claude Code をエンタープライズで横展開する話と直結します。

### 7. Publickey：エンタープライズストレージ CEO「半導体部品が 4-10 倍、製品価格は 70% 値上げ、まだ上がる」（Publickey · JA）

[Publickey 原文](https://www.publickey1.jp/blog/26/ceo41070.html)

Everpure の CEO が投資家向け説明で、半導体部品の調達コストが 4 倍から 10 倍に跳ねたと発言。製品本体価格を 70% 値上げし、今後もさらに値上げを示唆。背景は AI 学習向けの NAND/HBM 需要が全周期を吸い上げている構造です。来年度の社内ストレージ調達予算は、いまの数字でそのまま組むと確実にはみ出します。データ保全要件が厳しい金融・医療系は特に、今月中に再見積もりをかけたほうがよさそうです。

### 8. Rivian、車両のネットワーク機能を完全にオフにできる設定を公式に提供（HN · EN）

[Rivian サポートページ](https://rivian.com/support/article/can-i-disable-all-data-collection-from-my-vehicle) ・ [HN スレッド](https://news.ycombinator.com/item?id=47967786)

データ収集・OTA・遠隔操作のすべてをアプリから一括無効化できる設定が公式に存在することが共有されました。HN で 331 点、トップコメントは先週話題になった「RAV4 オーナーが DCM と GPS を物理的に取り外した」ニュースに繋がる流れです。日本の自動車メーカーにとっては「ユーザー選択肢としての完全オフライン」を出荷時に用意するかどうかが、これからの差別化軸になり得ます。

### 9. ベルギー議会、原発の廃炉中止を可決（HN · EN）

[dpa-international.com](https://dpa-international.com/general-news/urn:newsml:dpa.com:20090101:260430-930-14717/) ・ [HN スレッド](https://news.ycombinator.com/item?id=47961319)

HN で 712 点。電力価格の高止まり、再エネのベースロード不足、AI データセンターと EV による負荷増を背景に、議会が廃炉スケジュールを止める判断をしました。技術寄りの読み手にとっての関心事はデータセンター立地で、ベルギーと隣接するフランスはハイパースケーラーの候補地として再評価される可能性があります。日本でも電力単価と原発再稼働の議論はあと数年続くので、観測点として記憶しておきたい一件です。

### 10. Daniel Lemire「あなたは二分探索を破れる」 — 大配列での実測（HN · EN）

[lemire.me](https://lemire.me/blog/2026/04/27/you-can-beat-the-binary-search/) ・ [HN スレッド](https://news.ycombinator.com/item?id=47924912)

Lemire が分岐予測と SIMD 寄りのコードで、標準的な二分探索を大きい配列で実測上回る話。HN 226 点。本論は「どのサイズでどちらが速いか」の境界線がはっきり示されていることで、KV インデックスや探索ヘビーなコードを書く人にとって直接効きます。コメント欄ではキャッシュラインの挙動を巡って、コンパイラ後端の人たちが実装ディテールを補足していて、その流れも読み応えがあります。

## 編集後記

今日のメタテーマは「小さく・正しく・引き戻す」。前半 3 本（honker.dev、CopyFail 開示、datasette-llm-limits）は「AI 時代のバックエンドはむしろツールを増やさない方向で成熟する」ことを示唆しています。後半 3 本（Rivian の完全オフライン、ベルギー原発、Lemire の二分探索）は、「もう決まった」と言われていた前提条件が、社会・市場・アルゴリズムのそれぞれで再点検されているという話です。5 分しか時間がなければ、#1（honker.dev）でツール設計の美学、#2（CopyFail）で OSS 開示倫理の最新事例を押さえれば足りるはずです。なお本日は Zenn のトレンドページがレンダリングを返さず、GitHub Trending も取得失敗のため、当該スロットを他の EN ソースに振り替えています。
