---
title: "5月25日 · 今日のテック厳選10本"
date: 2026-05-25T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "privacy", "ai-agents", "supply-chain", "google", "anthropic", "browsers"]
categories: ["daily"]
summary: >-
  Rivianが車両のインターネット接続を完全に切るスイッチを公式サポートに明記。LinkedInは6278個のブラウザ拡張をスキャンし暗号化して毎リクエストに添付していたと判明。SQLiteに「キュー・ストリーム・Pub/Sub・cron」をまとめて押し込むhonker.devが登場。Shai-Hulud風マルウェアがPyTorch LightningのAI学習ライブラリに混入、AI供給網の前段が初めて正面から狙われました。V2EXでは中国国内token課金プランへの不満と「自腹でtoken買って会社の仕事をしている」という話題が並行で伸びています。日本側ではGoogleがManaged Agent APIとAntigravity 2.0を投入。SpaceXのS-1ファイリングで、Anthropicが月12.5億ドルの算力契約を結んでいたことが明らかに。MozillaはChrome内蔵Prompt APIに正式に反対。今日のテーマは「AI時代のプライバシー既定値・供給網信頼・算力請求書、その三つが同時に書き換わっている」。
---

## 本日のサマリー

今日の話題は3本の補助線で読めます。1本目は「既定値の所有権」——Rivianが「完全オフライン」を商品仕様にし、LinkedInが「拡張機能フィンガープリント」を本番投入していたことが明らかになり、MozillaがChromeのPrompt APIに反対した。2本目は「AI供給網の最前線」——PyTorch LightningへのShai-Hulud風混入、GoogleのManaged Agent API / Antigravity 2.0、中国国内のtoken課金プランの実用性。3本目は「算力請求書の可視化」——SpaceXのS-1に書かれたAnthropicへの月12.5億ドル契約、現場エンジニアの自腹token購入。日本の企業実務に最も即効性があるのは、Shai-Huludへの対応（lockfile点検）と、Google Managed Agent APIの動向確認（agent runtimeの内製or外注の判断材料）の2本です。

## 1. Rivian、車両のインターネット接続を完全オフにできることを公式化

[Rivian allows you to disable all internet connectivity](https://rivian.com/support/article/can-i-disable-all-data-collection-from-my-vehicle) · `Rivian / HN`

Rivianのサポート記事に「車両のすべてのデータ送受信を停止できる」とはっきり書かれました。診断データだけでなく、OTA、地図更新、車両テレメトリも含めて完全に切れます。コネクテッドカーが既定で常時オンライン化している現在、これは旧来の自動車メーカーに対して新しいプライバシー下限を設定する動きです。注目点は、これがEFFや規制ではなくメーカー自身のサポートKBに書かれていること。日本の自動車メーカーの企画部署も、今後の機能要件定義で「Rivian水準のオフライン操作」を要求される可能性があります。

## 2. LinkedIn、6278個のブラウザ拡張をスキャンして暗号化フィンガープリントを毎リクエストに付与

[LinkedIn scans for 6,278 extensions and encrypts the results into every request](https://404privacy.com/blog/linkedin-is-scanning-your-browser-extensions-this-is-how-they-use-the-data/) · `404privacy.com / HN`

リサーチャーがLinkedInのフロントエンドJSを解析した結果、6278個のブラウザ拡張の存在をクライアント側で能動的にチェックし、結果を暗号化したフィンガープリントとしてリクエストヘッダーに乗せていたとのこと。Web標準としては「拡張機能の有無は外部に漏れない」が前提でしたが、サイドチャネルで突破されています。日本のBtoB SaaS、特に営業支援や採用領域で同様の手法を検討しているチームは、技術的可否ではなく個人情報保護法・GDPR的妥当性で判断する局面に来ています。

## 3. honker.dev：SQLite一個に「キュー・ストリーム・Pub/Sub・cron」を全部入れる

[Durable queues, streams, pub/sub, and a cron scheduler – inside your SQLite file](https://honker.dev/) · `honker.dev / HN`

「SQLiteで何でも」シリーズの最新作。1個の.dbファイルに永続キュー、ストリーム、Pub/Sub、cronスケジューラを全部詰め、Redis・RabbitMQ・別cronプロセスを廃止できます。スタートアップや個人開発の「Kafka要らないけど何かは要る」帯にぴったり。日本では小規模SaaS、社内ツール、IoTゲートウェイの初期構築で運用負荷を一段下げる選択肢になり得ます。安定運用の実績はこれから積み上げていく段階。

## 4. 中国国内のtoken課金プラン、実態とPRに乖離があるとV2EXで議論

[阿里云 tokenplan 和百度 codingplan 慎买](https://www.v2ex.com/t/1214866) · `V2EX`

アリババクラウドのtokenplanとBaiduのcodingplanについて、実際の利用上限・有効期限・返金条件が宣伝と乖離しているという指摘が伸びています。背景には、海外のクレジットカードでClaude / OpenAIを直接契約する技術が中国国内のエンジニア層で安定してきたことがあり、国内token課金プランは「信頼の貯金」を切り崩しにくくなっています。日本企業の中国オフィスや中国向けプロダクトを持つチームには、現地エンジニアの実質的なtoolchainがどちらに寄っているかを示す観測点になります。

## 5. 自腹でtokenを買って会社の仕事をしている、というV2EXスレッド

[你们多少人是自己付费买 token 干公司的工作任务了？](https://www.v2ex.com/t/1214981) · `V2EX`

「会社がClaudeやCursorの予算を承認しないので、自分のクレカでtokenを買って業務に使っている」という話題。レスは賛否両論で、「キーボードを自費で買うのと同じ」派と「生産性コストの個人転嫁」派が拮抗しています。日本企業の人事・情報システム部門にとっても他人事ではなく、「AIツール経費精算ガイドライン」が事実上の必須項目になりつつあります。シャドーITの定義そのものがAI時代に再定義される瞬間です。

## 6. Google、APIコール一発でLinux環境付きAIエージェントを起動する「Managed Agent API」発表

[APIコール一発でGoogleがホストするLinux環境付きのAIエージェントを起動](https://www.publickey1.jp/blog/26/apigooglelinuxaimarkdownmanaged_agent_api.html) · `Publickey`

Google I/Oの第二弾とも言える発表。HTTPリクエスト1本で、Google側でフルLinuxサンドボックス付きのAIエージェントが起動し、振る舞いはMarkdownのカスタム指示で記述できます。「agent runtime」がいよいよマネージドサービス化された格好で、自前でDockerやMCP wrapperを管理するコストを丸ごと吸収します。日本企業がagent製品をビルドしている場合、「ランタイム自前 vs Google Managed」の損益分岐点をこの夏中に出しておく必要があります。

## 7. Google Antigravity 2.0発表、デモはゼロからOS開発しDoomも動かす

[Google、「Antigravity 2.0」発表。デモとしてゼロからOSを開発、Doomも実行可能に](https://www.publickey1.jp/blog/26/googleantigravity_20osdoom.html) · `Publickey`

Antigravity 2.0がI/Oで正式登場。デモでは「ゼロからDoomが動くミニOSを書く」という派手な題材で、長時間・高複雑度タスクへの信頼を視覚的に演出しました。同時にAndroidアプリ開発の正式サポート、Android Knowledge BaseとAndroid Skillsも公開。日本のAndroid開発現場では、Antigravity導入を「単なるIDEの選択」ではなく「組織のCI/CDと skill 管理基盤への組み込み」として評価し直す時期に来ています。

## 8. Shai-Hulud風マルウェアがPyTorch Lightning（AI学習ライブラリ）に混入

[Shai-Hulud Themed Malware Found in the PyTorch Lightning AI Training Library](https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/) · `semgrep.dev / HN`

SemgrepがPyTorch Lightningの依存パッケージにShai-Hulud（『デューン』の砂蟲）モチーフのマルウェアが混入していたことを公表。狙いは学習機上のSSH鍵、クラウド認証、wandbトークンの収集で、学習されたモデル自体への影響よりも、学習を回している組織の認証情報が抜かれる構図です。「AI供給網汚染」がモデル配布だけでなく学習側の依存パッケージにも本格的に到達しました。本日中にすべてのML系プロジェクトで`uv.lock` / `poetry.lock` / `requirements.txt`の点検を推奨します。

## 9. SpaceX S-1ファイリングで、Anthropicが月12.5億ドルの算力契約を結んでいたと判明

[SpaceX S-1 — Anthropicとの COLOSSUS / COLOSSUS II 契約](https://www.sec.gov/Archives/edgar/data/1181412/000162828026036936/spaceexplorationtechnologi.htm) · `SEC / Simon Willison`

SpaceXの上場申請書類にAnthropicが実名で登場。Anthropicはxai側のCOLOSSUS / COLOSSUS IIに対し2029年5月まで月額12.5億ドルを支払う、いずれかの当事者から90日前通知で解除可能、という条件が公開されました。前線モデル企業の物理レイヤーの単価がSEC文書として可視化されたのは珍しく、これからの「AIは経済的に持続可能か」議論で必ず参照されることになる数値です。Anthropicの算力源がAWS、Google Cloud、SpaceXへと多角化していることも同時に裏付けられました。

## 10. Mozilla、Chrome内蔵Prompt APIに正式に反対

[Mozilla's opposition to Chrome's Prompt API](https://github.com/mozilla/standards-positions/issues/1213#issuecomment-4347988313) · `GitHub mozilla/standards-positions`

Mozillaの標準ポジションリポジトリに、Chromeが提案しているPrompt API（ブラウザ内蔵LLMをJSから呼ぶAPI）への明確な反対意見が掲載されました。論点は、ブラウザフィンガープリントの密度増加、ブラウザごとに異なる内蔵モデルによるweb fragmentation、そして特定ベンダー能力をweb標準に取り込む先例の3つ。フロントエンド側で「`await ai.prompt(...)`」を前提にした設計に踏み込もうとしていた人は、当面はExperimental前提に巻き戻しておくのが安全です。Web標準でのAI内蔵化は政治フェーズに入りました。

## 編集後記

今日の10本は「既定値の所有権」「AI供給網信頼」「算力請求書の可視化」の3本の補助線で見ると整理しやすい一日です。今日の必読を2本挙げるなら、まず **Shai-Hulud風マルウェアのPyTorch Lightning混入**——AI供給網の議論が学習側の依存パッケージという具体的なレイヤーまで降りてきました。もう1本は **SpaceX S-1の月12.5億ドル数値**——前線AI企業のインフラコストが初めて公開資料に載った節目です。
