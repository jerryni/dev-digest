---
title: "6月3日 · 今日のテック厳選10本"
date: 2026-06-03T07:00:00+09:00
draft: false
tags: ["digest", "2026-06", "openai", "codex", "stanford", "rolldown", "vite", "anthropic", "alphabet", "aws"]
categories: ["daily"]
summary: "OpenAIのフロンティアモデルとCodexがAWSに着陸。Rolldown 1.0がついにGAし、Vite 8.0で正式採用へ。AlphabetはAI向けに800億ドル株式調達。Anthropicは上場準備の翌日にGlasswingを拡張。"
---

## 本日のサマリー

火曜日のトーンは「AIインフラの陣取り合戦」一色です。OpenAIがGCP/Azureに加えてAWS Bedrockにも全モデルを展開、AlphabetはAI向けに800億ドルの株式調達を発表、Anthropicは前日のS-1提出に続いてProject Glasswingの拡張を発表しました。日本のエンジニアにとって実務上いちばん効きそうなのはRolldown 1.0のGA — Vite 8.0に正式採用されることで、esbuild時代がついに終わりに近づきます。中国語圏はOpenAIが一夜にしてCodexアカウントすべてに二段階認証を要求した件で大荒れ。

---

### 1. OpenAIフロンティアモデル + CodexがAWSで利用可能に — `[Hacker News · 285 pts]`
<https://openai.com/index/openai-frontier-models-and-codex-are-now-available-on-aws/>

GPT-5.5 / 5.4 / 5.3とCodexがAWS Bedrockから直接呼び出せるようになりました。AWSをメインで使う日本企業にとっては、これまで「OpenAI使うためだけにAzureサブスクを作る」というSAP/CTOへの説明コストがゼロになるのが大きい。さらにTokyoリージョンでの提供も同時開始なので、レイテンシ要件のある業務でも採用が現実的になりました。AWSが「マルチクラウドではない、唯一のクラウド」へと舵を切ったタイミングと重なるのも興味深い動きです。

### 2. Rolldown 1.0 GA、Vite 8.0で標準採用 — `[Publickey · 6月2日]`
<https://www.publickey1.jp/blog/26/rustjavascriptrolldown10vite_80.html>

Rust製のJavaScriptバンドラ「Rolldown」がついに1.0に到達し、Vite 8.0の標準バンドラとして採用されました。esbuildに対して機能パリティを達成しつつ、ベンチマークでは30〜50%高速、Rollupプラグイン互換も完備。日本の大規模フロントエンド開発（特にNuxt / Astroベースの企業案件）では、dev / buildのパスが統一されることで「devで動くのにbuildで落ちる」あるあるが大幅に減るはずです。Vite 8.0アップデートは6月中旬予定。

### 3. AWS Kiro Web、ブラウザだけで使えるコーディングエージェントを発表 — `[Publickey · 5月28日]`
<https://www.publickey1.jp/blog/26/awswebaikiro_web.html>

AWSが「Kiro Web」を発表しました。Cursor / Windsurfと異なり、まず仕様書を書いてからAgentに実装させる「spec-driven」アプローチが特徴で、AWSアカウントだけでログイン可能。日本企業のCIOにとっては、開発者ひとりひとりに外部SaaSサブスクを発行する手間がなくなり、IT統制下にAIコーディング環境を置けるのは大きい。富士通やNTTデータなど、AWS主軸のSIerが社内展開の検証を始めているという話も出ています。

### 4. Stanford CS336：ゼロから言語モデルを作るコース教材全公開 — `[Hacker News · 480 pts]`
<https://cs336.stanford.edu/>

Percy LiangのCS336（Language Modeling from Scratch）の今年度版教材・課題・参照実装がすべて公開されました。トークナイザ実装からTransformer、データパイプライン、RLHFと評価まで、PyTorchで動くコード付き。日本国内でLLMを「使う側」から「作る側」に回りたいエンジニアにとって、現時点で世界最高峰の無料教材です。社内勉強会の題材にも最適で、英語ですが図表が豊富で読み物として成立しています。

### 5. Alphabetが800億ドルの株式調達発表、AIインフラへ集中投資 — `[Hacker News · 205 pts]`
<https://abc.xyz/investor/news/news-details/2026/Alphabet-Announces-Proposed-80-Billion-Equity-Capital-Raise-to-Expand-AI-Infrastructure-and-Compute-2026-b0myAMewCa/default.aspx>

Googleの親会社Alphabetが単独で800億ドルの株式調達を実施。用途はTPU工場、データセンター、電力契約と明記されています。Microsoftの800億、Metaの700億CapExと合わせると、2026年のハイパースケーラーのAI設備投資は3000億ドル規模。日本の電力業界にとっても無関係ではなく、千葉・印西の新規データセンター建設が再加速する可能性が高いです。日本の電力グリッドが2027年問題（容量市場）と重なるので、現場のSREは電力ピーク回避の運用設計を今から考えておいたほうがよさそうです。

### 6. Anthropic、Project Glasswingを拡張 — `[Anthropic公式 · 6月2日]`
<https://www.anthropic.com/news/expanding-project-glasswing>

AnthropicがS-1機密提出の翌日、Project Glasswing（4月発表の重要ソフトウェア保護イニシアチブ）の参加企業を拡大しました。当初のAWS / Apple / Cisco / Google / Microsoft / NVIDIAに加え、欧州とOSS陣営から複数団体が加入。日本企業の参加はまだですが、Linux Foundationが東京で開催する「AGNTCon + MCPCon」（9月）でGlasswing関連セッションが組まれる予定なので、セキュリティ担当者は要チェック。

### 7. Simon Willison：Codexデスクトップで作る「Pasted File Editor」 — `[Simon Willison's Weblog · 6月2日]`
<https://simonwillison.net/2026/Jun/2/pasted-file-editor/>

Claude.aiが大きなテキストを貼り付けるとファイル添付に自動変換する挙動を、Simon WillisonがCodexデスクトップに依頼して再現ツールを作った、という小さな実例。コード自体は短いですが、AIにツールを「直接実装させる」開発スタイルがどこまで実用になっているかの良いサンプルになっています。日本のZenn記事でも最近こうした「vibe codingで作った道具」紹介が増えてきており、流れの一致を感じます。

### 8. OpenAI、Codex全アカウントに二段階認証を強制 — `[V2EX · 多数のホットスレッド]`
<https://www.v2ex.com/t/1217218>

OpenAIが昨夜、Codexアカウント全体に電話番号による二段階認証を強制適用。Plus契約者も対象で、中国本土・東南アジアからのVPN経由アクセスが大量にブロックされたと報告されています。日本在住エンジニアでも、楽天モバイルなどMVNOで認証SMSが届かないケースが散見。AWS進出のタイミングと重なるので、コンプライアンス清算の意味合いが強そうです。「シェアアカウント」運用していたチームは早めに各自契約に切り替えを。

### 9. Encrypted reasoning blobs：OpenAIの推論暗号化を解剖 — `[Hacker News · 101 pts]`
<https://blog.cryptographyengineering.com/2026/05/29/fooling-around-with-encrypted-reasoning-blobs/>

暗号研究者Matthew GreenがOpenAIの「encrypted reasoning blob」（推論過程の暗号化機構）を技術的に検証。設計自体は妥当だが、信頼モデルは依然「OpenAIが鍵を差し替えない」前提に依存していると結論付けています。金融・医療系のRAG案件で「LLMに機密データを通せるか」を稟議で通すための材料として使えるレベルの論考なので、企業導入担当のエンジニアは目を通しておく価値があります。

### 10. CSS-Native Parallax Effect：JS不要のパララックス — `[Hacker News · 17 pts]`
<https://dan-webnotes.com/posts/2026-06-02-css-native-parallax-effect/>

CSSの新しいスクロール駆動アニメーション（`scroll-timeline`）だけで、JSなしのパララックスを実現する解説記事。Safari Technology PreviewとChrome 132で対応済み、Firefoxは6月リリース予定で全主要ブラウザ対応が間近。日本のコーポレートサイト案件はパフォーマンス制約が厳しいので、JSバンドルを軽くしたいフロントエンドエンジニアは今のうちに手元で触っておくと、半年後に実案件で使えます。

---

## 編集後記

本日のメタテーマは**「AI巨人たちのインフラ陣取り」**。OpenAIのAWS進出、Alphabetの800億ドル、AnthropicのGlasswing拡張——三大プレイヤーがそれぞれ違う角度から「次の5年の支配権」を確保しに動いています。実務でいちばん効くのは**4のStanford CS336**（LLMの内部を知りたいなら最高の無料教材）と**2のRolldown 1.0**（フロントエンドの体感を変える）の2本。

Zennは本日トレンディングのHTMLが取得できなかったため他ソースで補完しています。
