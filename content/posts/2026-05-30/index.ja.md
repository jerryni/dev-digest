---
title: "5月30日 · 今日のテック厳選10本"
date: 2026-05-30T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "claude", "kiro", "docker", "agents", "datasette"]
categories: ["daily"]
summary: "AWSがKiroをブラウザに持ち込み、DockerはGordonを正式リリース。HNではVicki Boykisの「人間のほうがモデルより疲れているべき」が話題。V2EXではOpus 4.8がqwenを名乗る珍事と、AIに月1200元まで課金額を「育てられた」体験談が並びました。"
---

## 本日のサマリー

土曜日ですが、コーディングエージェント周りの動きは止まりません。AWSの **Kiro Web** とDockerの **Gordon** が同じタイミングで出てきたことで、「どのCLIを入れるか」ではなく「どのブラウザ／公式ツールに乗っているエージェントを使うか」という選択に主戦場が移りつつあります。日本の開発現場で気になるのは、社内の端末ポリシーがCLI型エージェントの導入を阻んでいたチームにとって、Webブラウザ完結型は一気に検討しやすくなる点です。あわせて、Vicki Boykisの「私たちはモデルより疲れているべき」というエッセイは、エージェント運用に慣れてきた現場のシニア層にこそ刺さる内容でした。

## 本日の10本

### 1. AWS、ブラウザで動くコーディングエージェント「Kiro Web」発表
**Source: Publickey**
<https://www.publickey1.jp/blog/26/awswebaikiro_web.html>

これまでデスクトップ版だったKiroが、インストール不要のWeb版として登場しました。日本企業のIT部門はCLIエージェントのインストール許可で揉めることが多いので、「ブラウザだけで完結」というのは導入障壁を大きく下げます。Cursor／Claude Codeのインストール型と、ブラウザ常駐型のどちらに収斂していくか、ここから3〜6ヶ月の動きが分水嶺になりそうです。

### 2. Docker専用エージェント「Gordon」が正式リリース
**Source: Publickey**
<https://www.publickey1.jp/blog/26/dockeraigordondocker.html>

Dockerに関する質問専用のエージェントが正式版になりました。compose の書き方、よくあるエラーの修正、Dockerfileのリファクタまで、無料アカウントで触れます。少し前のDart & Flutter Agent Skillsもそうですが、上流のツールベンダーが「AIに読ませる前提の公式ドキュメント／エージェント」を自分で持つ流れは、確実に2026年下半期のトレンドになります。

### 3. 私たちはモデルより疲れているべきだ
**Source: Vicki Boykis（HN #9経由）**
<https://vickiboykis.com/2026/05/28/we-should-be-more-tired-than-the-model/>

『What are embeddings』の著者Vicki Boykisによる短いエッセイ。「一日エージェントを動かしたあとに、何も学んだ感じがしないなら、それは丸投げであって設計ではない」という趣旨です。AI否定論ではなく、エージェントは増幅器であって代替ではない、という立場。シニアになるほど「全権委任」の誘惑が強くなる、というHN側の議論も読みごたえがあります。

### 4. 標準GPUで1リクエスト3,000 tokens/秒のリアルタイム推論
**Source: blog.kog.ai（HN #8経由）**
<https://blog.kog.ai/real-time-llm-inference-on-standard-gpus-3-000-tokens-s-per-request/>

H100にこだわらず、L40SやA100クラスでも1リクエスト3k tokens/秒まで攻められるという実装記事。KVキャッシュのメモリレイアウトを書き直して、attention kernelをカスタムする方向です。H100調達が厳しい日本の事業者にとって、既存GPUの稼働率を最大化する側のアプローチは現実的な選択肢になります。

### 5. AnthropicとOpenAIはPMFを掴んだ
**Source: Simon Willison's Weblog**
<https://simonwillison.net/2026/May/27/product-market-fit/>

Anthropicが間もなく初の黒字四半期に入りそうだという話と、企業のClaude請求額が想定を超えているという報道を組み合わせて、Simonが「両社はPMFを越えた」と論じています。「Claude Code利用に上限を設けなかった結果、1ヶ月で5億ドル燃やした顧客がいる」という匿名引用が強烈です。

### 6. Claude Opus 4.8、自分のことを「qwen」と名乗る
**Source: V2EX · Claude板**
<https://www.v2ex.com/t/1216494>

中国語コミュニティV2EXでの観察報告。サードパーティのAPI転送サービス経由でOpus 4.8を呼び出したら、自己紹介で「私はqwenです」と返してきた、という話。背景として、転送業者が安いモデルにすり替えていないか？という議論が湧いています。日本の開発者にとっても示唆的で、「公式以外の経路で買うLLM APIは、本当にそのモデルか」を疑う仕組み（自己申告だけに頼らない検証）は必要です。

### 7. AIに月1,200元まで課金額を育てられた話
**Source: V2EX · 程序员板**
<https://www.v2ex.com/t/1216578>

「最初は無料版で十分だと思っていたのに、気がつけば月1,200元（約25,000円）課金していた」という告白スレ。スレ主は後悔ではなく、ROIを淡々と振り返っています。#5のSimonのエッセイと併せて読むと、企業だけでなく個人開発者の側にもPMFが浸透している様子が見えます。

### 8. Datasette 1.0a31：書き込みSQLとstored queriesに対応
**Source: Simon Willison's Weblog**
<https://simonwillison.net/2026/May/29/datasette/>

長らく「SQLiteのリードオンリーブラウザ」だったDatasetteが、ついにUI上から書き込みSQLを実行できるようになりました。社内向けの簡易管理画面を自前で書いていたチームなら、Datasetteで置き換えられるケースがかなり出てきます。社内ツールの選択肢として再評価のタイミング。

### 9. AIはフロントエンドの「失われた10年」を繰り返させているのか
**Source: mastrojs.github.io（HN #16経由）**
<https://mastrojs.github.io/blog/2026-05-23-is-AI-causing-a-repeat-of-frontends-lost-decade/>

2010年代のフロントエンド——フレームワーク戦争、バンドルサイズ肥大化、エンドユーザー体験はそれほど良くならなかった——という歴史を、いまのAIエージェント乱立に重ねた批評記事。「ツールチェーンばかり進化してプロダクト品質が追いついていない」という指摘は、SaaSを多く抱える日本企業のエンジニアにとっても他人事ではありません。

### 10. CloudflareのAIコードレビュー運用
**Source: Cloudflare Blog（HN #12経由）**
<https://blog.cloudflare.com/ai-code-review/>

CloudflareがプロダクションでどうAIコードレビューを回しているかを公開。PRの選別、モデルの使い分け、false positiveの折り畳み方、人間レビュアーとの分担まで踏み込んだ運用記事です。「PRにBotを付けてみた」レベルではなく、組織的な導入を考えている開発組織には参考価値が高い内容。

## 編集後記

今日の隠れたメインテーマは2つ、**エージェントがブラウザと公式ツールチェーンに溶け込み始めた**（#1 Kiro Web、#2 Docker Gordon）こと、そして **「PMFは請求額で証明される」**（#5 Simon、#7 V2EX）こと。一本だけ読むなら **#3 Vicki Boykisの「私たちはモデルより疲れているべき」**を推します。シニアエンジニアほど読んでおいたほうが良い種類のエッセイです。次点は **#10 CloudflareのAIコードレビュー運用**、社内導入の設計図として手元に置きたい内容です。

---

*本日、GitHub Trendingはキャッシュが古く有用なデータが取れなかったため除外。Anthropic公式Newsは昨日のリリース以外に新規なし。*
