---
title: "5月20日 · 今日のテック厳選10本"
date: 2026-05-20T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "ai-agents", "supply-chain", "vs-code", "anthropic"]
categories: ["daily"]
summary: >-
  Simon Willison が「ここ半年の LLM」を 5 分のライトニングトークにまとめ、PyTorch Lightning には Shai-Hulud 系のサプライチェーン攻撃、Mozilla は Chrome の Prompt API に正面から反対表明。Anthropic は Stainless を買収して SDK 生成パイプラインを内製化し、KPMG とは 27.6 万人規模の戦略アライアンスを締結。Coding Agent が「日常使い」フェーズに入ったあとの、開発実務とエコシステムの動きを 10 本に。
---

## 本日のサマリー

Coding Agent が「使える」から「日常的に使う」段階に移ったことが、ここ数日のニュースで一気に可視化されました。Simon Willison の振り返りに加え、サプライチェーン攻撃、ブラウザ API 標準論争、Anthropic の M&A、Big4 への大規模導入と、副作用と本格運用が同じ週に並んで出てきている格好です。日本国内のエンジニア向けには、Publickey の VS Code Agent window と Node.js 26（Temporal デフォルト有効化）の 2 本が直接効きます。

## 1. Simon Willison · 直近半年の LLM を 5 分で

[The last six months in LLMs in five minutes](https://simonwillison.net/2026/May/19/5-minute-llms/) · `Simon Willison`

PyCon US 2026 のライトニングトークの注釈付きスライドです。「2025 年 11 月の inflection point」以降の流れ、Coding Agent が日常使いに耐えるラインを超えたこと、OpenClaw 騒動までを駆け足で。最近の動きを 1 本でキャッチアップしたい方にちょうど良い分量です。

## 2. PyTorch Lightning にサプライチェーン汚染

[Shai-Hulud Themed Malware Found in the PyTorch Lightning AI Training Library](https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/) · `Semgrep / HN`

Semgrep が PyTorch Lightning 周辺の悪性依存を検出。命名は昨年来の「Shai-Hulud（砂蟲）」系の流れを汲んでいます。学習パイプラインは API キー・モデル重み・社内データが集まる高価値ターゲットなので、CI でのシークレット露出と依存ロックの運用は、Web/Node 開発者が当然やっていることを ML チームでも同じレベルで詰める段階に来ています。

## 3. Mozilla、Chrome の Prompt API に明確に反対

[Mozilla's opposition to Chrome's Prompt API](https://github.com/mozilla/standards-positions/issues/1213#issuecomment-4347988313) · `GitHub / HN`

Chrome が進める `window.ai.languageModel` 系の Prompt API に対して、Mozilla が標準化ポジションで反対を明文化しました。モデルがブラックボックスでありフィンガープリント懸念、ベンダーロック、挙動の予測不可能性が主な論点です。「AI 能力をどのレイヤーが提供するのか（OS / ブラウザ / サイト）」という、これから数年もめる議論の起点になります。

## 4. V2EX · AI 時代、プログラマは 2 種類に分かれた

[AI 时代，程序员被清楚地分为了两类人](https://www.v2ex.com/t/1213387) · `V2EX`

中国の開発者コミュニティでの 74 レスのスレッド。「AI を使う／使わない」だけで分かれるのではなく、「設計とレビューを残せる人 / Agent に丸投げして自分の理解が止まっている人」という分かれ方が議論の中心です。日本企業の中堅エンジニアがメンタリングのときに参考にできる切り口で、評価制度の見直し議論にも繋がっていきます。

## 5. V2EX · インターンが AI に頼り切り、通すべきか

[实习生极度依赖 AI，要不要让他实习通过？](https://www.v2ex.com/t/1213466) · `V2EX`

「成果物は動くし、ドキュメントもある。ただし本人がコードを読めない」というインターン受け入れの相談。「ツールを使えること自体が新しい基礎」とする派と、「自分の PR を説明できないなら不可」とする派で割れています。日本の新卒採用にも近い将来そのまま降りてくるテーマで、面接時の「自分の言葉で説明させる」ステップ設計が改めて重要になります。

## 6. Publickey · VS Code 「Agent window」プレビュー公開

[VS Code、複数AIエージェントでの開発を容易にする新機能「Agent window」プレビュー公開](https://www.publickey1.jp/blog/26/vs_codeaiagent_window.html) · `Publickey`

VS Code 1.120 で、複数の AI エージェントを並行運用するための独立ウィンドウ「Agent window」が入りました。BYOK の表示と権限制御、長尺タスクのバックグラウンド実行が主な改善点です。社内ガイドラインで「使ってよいモデル」を縛りたい企業 IT には、API キーがどこで使われているかの可視化が前進した、という意味で取り組みやすくなっています。

## 7. Publickey · Node.js 26、Temporal がデフォルト有効

[Node.js、Dateに代わる日時処理「Temporal」がデフォルト有効化](https://www.publickey1.jp/blog/26/nodejsdatetemporaltemporalchromeedgefirefoxnodejs.html) · `Publickey`

`Date` を実質置き換える新 API「Temporal」が、Chrome / Edge / Firefox / Node.js 26 すべてでデフォルト有効になりました。タイムゾーン・日付計算・Duration が言語標準で扱えるようになるのは大きく、新規プロジェクトはここから `dayjs` や `date-fns` を入れる必要がなくなっていきます。既存コードは段階移行で十分です。

## 8. Anthropic、Stainless を買収

[Anthropic acquires Stainless](https://www.anthropic.com/news/anthropic-acquires-stainless) · `Anthropic News`

Stainless は OpenAPI から多言語 SDK を生成する会社で、Anthropic / OpenAI / Cloudflare などの公式 SDK をまとめて支えてきました。Anthropic が買収したことで、Claude SDK・Connector・Skills のツールチェーンを内製で握ることになります。短期的には SDK 更新が速くなり、長期的には API レイヤーが Anthropic 側の「インフラ的な強み」として効いてきそうです。

## 9. Anthropic × KPMG · 27.6 万人規模の戦略アライアンス

[KPMG integrates Claude across its core business and workforce of more than 276,000 in strategic alliance](https://www.anthropic.com/news/anthropic-kpmg) · `Anthropic News`

Big 4 で初めて、単一の AI ベンダーを戦略アライアンスとして組み込む格好です。直近の PwC、Gates Foundation、Blackstone との発表と並べると、Anthropic は B2C ではなく、監査・法務・コンサルなど「文書密度の高い業界」から面で押さえに行っているのが分かります。日本法人での導入が時間差で来るので、社内ガイドラインの整備はそろそろ着手しておいて損はありません。

## 10. HN · Pu.sh — 400 行の shell で書いた Coding Agent ハーネス

[Show HN: Pu.sh – a full coding-agent harness in 400 lines of shell](https://pu.dev/) · `Hacker News / Show HN`

ツール呼び出し、コンテキスト管理、サブプロセス分離、ファイル diff 適用までを 400 行の bash で実装した Coding Agent ハーネス。作者の主張は「今の LLM 品質では、LangChain / AutoGen のような重いフレームは要らない」というもので、社内 dev tool を自前で書こうとしているチームには良い読み物です。実装方針の比較対象として一読をおすすめします。

## 編集後記

今日のテーマは「Coding Agent が日常になった結果、地味だが効く副作用が同時多発している」です。マスト 2 本は **Simon の振り返り**（半年の流れの再確認）と **Anthropic による Stainless 買収**（来年の SDK / API エコシステムを読むため）。日本のチームには Publickey 2 本（Agent window と Temporal）が直接効きます。GitHub Trending は本日レンダリング不調のため個別エントリ化を見送りました。
