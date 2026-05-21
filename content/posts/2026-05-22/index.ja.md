---
title: "5月22日 · 今日のテック厳選10本"
date: 2026-05-22T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "privacy", "supply-chain", "ai-agents", "browser", "dev-tools"]
categories: ["daily"]
summary: >-
  Rivianが本気の「通信を全部切る」スイッチを実装。PyTorch LightningにShai-Hulud系のマルウェアが混入。MozillaがChromeのPrompt APIに正式反対。Simon Willisonが直近半年のLLM動向を5分で総括。AnthropicがStainlessを買収。400行のシェルでコーディングAgentを名乗るプロジェクトも登場。本日のテーマは「土台の固まり方」。
---

## 本日のサマリー

ビッグニュースの日ではないものの、密度は高めです。HNの上位はプライバシーとサプライチェーン話題、AIインフラ層は静かに統合が進んでいます。Rivianは「本物のオプトアウト」とは何かを示し、PyTorch Lightningエコシステムは「本物のサプライチェーン攻撃」を体験することになりました。AnthropicのStainless買収は、SDK生成という「地味だが効く」レイヤーの所有権がどこに向かうかを物語っています。コネクテッドデバイスやLLM連携を扱うチームには、最後まで読む価値があります。

## 1. Rivian、車両の通信を完全にOFFにできるスイッチを公開

[Rivian、車両のデータ収集を完全に無効化する手順](https://rivian.com/support/article/can-i-disable-all-data-collection-from-my-vehicle) · `Hacker News`

Rivianがサポート記事で、OTA・テレメトリ・リモートサービスをまとめて遮断する単一トグルの使い方を公開しました。デグレードモードに落ちることもなく、警告のポップアップが連発することもなく、本当に「何も話さない車」になります。Tesla・Ford・GMはまだデータ経路を体験の前提として扱っていますが、主要OEMで本物のオフスイッチを実装し、公式に手順を出したのはRivianが初です。2年以内に規制側のベースラインになるでしょう。

## 2. PyTorch LightningにShai-Hulud系マルウェアが混入

[PyTorch LightningにShai-Hulud系の悪意あるパッケージを発見](https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/) · `Hacker News`

Semgrepのリサーチチームが、pytorch-lightningの固定依存を装った悪意あるパッケージを発見しました。狙いはクラウド認証情報とHugging Faceトークンです。昨秋のnpm事件と同じファミリーが、今度はMLツールチェーンに移植されてきた形です。CIでモデルウェイトをキャッシュしている、あるいはartifactを取得している現場は、来四半期ではなく今週中にlockfileを監査してください。

## 3. MozillaがChromeのPrompt APIに公式反対

[Mozilla standards-positions：Prompt APIへの反対立場](https://github.com/mozilla/standards-positions/issues/1213) · `Hacker News`

Mozillaがstandards-positionsリポジトリで、ブラウザ内LLMアクセスを提供するPrompt APIに正式な反対を表明しました。論点は「AI反対」ではありません。モデル挙動をプラットフォーム仕様に焼き込むと、まだ高速に動いている品質基準を凍結することになり、しかも誰も望んでいないフィンガープリント面が増えるという話です。Chromeはそのまま出荷するでしょうが、「ブラウザに載せるAI」の設計が見た目より難しい理由を、これだけ整理した文章は他にありません。

## 4. Simon Willisonが直近半年のLLMを5分で総括

[The last six months in LLMs in five minutes](https://simonwillison.net/2026/may/19/six-months-llms/) · `Simon Willison`

11月から5月までの動きを圧縮した記事です。短いcontext windowの終焉、tool-useプロトコルの収束、「agent」という語が業界用語から構造語へ昇格した過程、価格がどこに落ち着いたか。単一プロダクトに集中していて視界が狭くなってきた人が、一度に視点をリセットするのに最適な一本です。

## 5. V2EX：vibe codeで積んだ技術的負債、どう返す？

[vibe codeで生まれた技術的負債をどう消すか？](https://www.v2ex.com/t/1214452) · `V2EX`

中国の現役エンジニアコミュニティで、今年どのチームも遅かれ早かれ直面する問いが投げかけられました。インターンやPMがAgentで一気に書き上げた機能の書き直しはどう進めるのか、誰がオーナーシップを持つのか。スレッドの回答は「外注コードと同じ扱いにする」から「同じAgentで2日で書き直す」まで様々ですが、議論の早さと率直さは英語圏より一歩進んでいます。

## 6. V2EX：AntigravityがGeminiの利用枠を恒久的に3倍に

[Antigravity: Gemini枠が恒久3倍に](https://www.v2ex.com/t/1214387) · `V2EX`

V2EXの複数の独立な観測から、Googleが公式アナウンスせずにAntigravityのFree/Proの両プランでGeminiコール枠を3倍に引き上げたことが確認されました。中国語圏ではこれを、Anthropic + AWSの本格展開を前にした価格戦と読む向きが優勢です。解釈はさておき、「個人プロジェクトはとりあえずAntigravityで」という選択がさらに自明になったのは確かです。

## 7. DuckDBに通信プロトコルが追加：Quack

[DuckDBをクライアント／サーバ化する「Quack」プロトコルが登場](https://www.publickey1.jp/blog/26/duckdbquackduckdb.html) · `Publickey`

DuckDBはこれまでin-processの分析エンジンとして使われてきました。Quackは複数のDuckDBインスタンスが互いに接続できる通信プロトコルを追加し、組み込みウェアハウスを「複数台のフリートから叩ける対象」に変えます。ClickHouse級の成熟度にはまだ届きませんが、分析ワークロードから見たDuckDBの輪郭が、急にノートブック向けではなく本物のデータベースに見えてきました。

## 8. BunがClaudeを使ってZigからRustへ移行中

[JavaScriptランタイムのBun、Claudeを使って開発言語をZigからRustへ移行中](https://www.publickey1.jp/blog/26/javascriptbunclaudezigrust.html) · `Publickey`

Bun作者のJarred SumnerがZig→Rust移行のポーティングガイドを公開しました。Claudeに機械的な翻訳をさせ、人間はdiffをレビューするという分担です。注目すべきは言語選定そのものではなく、ランタイム開発チームがAI支援で百万行規模のリファクタリングを公開で進め、そのプレイブックまで共有しているという事実の方です。

## 9. AnthropicがStainlessを買収

[Anthropic acquires Stainless](https://www.anthropic.com/news/anthropic-acquires-stainless) · `Anthropic`

Stainlessは主要AIプロバイダのクライアントSDK（Anthropic自身を含む）の裏側にいる、OpenAPIから型付きSDKを生成するツールです。買収によってSDK生成が内製化され、Anthropicがクライアントレイヤーをエンドツーエンドで握りに行く意思が見えます。10年前にStripeが決済APIで同じプレイをしました。ClaudeのSDKリリース速度がさらに上がり、外部向けにはStainlessの後継プロダクトが出てくる可能性が高いと見ています。

## 10. Pu.sh：400行のシェルで動くコーディングAgent

[Show HN: Pu.sh - 400行のシェルで動くコーディングAgent harness](https://pu.dev/) · `Hacker News`

Agentフレームワーク軍拡競争への反論のような一品です。Pu.shは400行のPOSIXシェルだけで、ツール呼び出し、ファイル編集、plan/executeループを実装しています。Python不要、Node不要。Claude CodeやAiderの本番代替にはなりませんが、「Agentの内側で何が起きているか」を理解するための強制読書素材としては優秀です。実行しなくてもソースを読む価値があります。

## 編集後記

本日のメタテーマは「土台が固まりつつある」です。Postgresに乗ったワークフローエンジン、通信プロトコルを得たDuckDB、SDKレイヤーを内製化するAnthropic、急成長中のランタイム内部でRustに置き換わっていくZig。Rivianのオフスイッチ事件もPyTorch Lightningのサプライチェーン事件も、本質的には「データ経路の支配権」を巡る話です。1日2本だけ読むならSimon Willisonの半年総括（視点のキャリブレーション用）と、PyTorch LightningのShai-Hulud記事（CIがモデルartifactを触る現場は必読）をお勧めします。Zennのtrending feedは今日も空のSPAシェルが返ってきたので、日本系の2本はすべてPublickey由来です。
