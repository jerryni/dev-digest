---
title: "6月25日 · 今日のテック厳選10本"
date: 2026-06-25T07:00:00+09:00
draft: false
tags: ["digest", "2026-06", "ai", "agents", "cloudflare", "github", "ruby", "aws", "codex"]
categories: ["daily"]
summary: "今日はcomputer use、OAuth、Mac向けコンテナ、PRスパム、Lambda MicroVMsなど、AI時代の開発基盤に関わる話題が中心です。"
---

## 本日のサマリー

今日はAIそのものより、AIを仕事に入れるための周辺基盤が目立ちました。Geminiのcomputer use、CloudflareのSelf-Managed OAuth、Apple Silicon向けコンテナ、AWS Lambda MicroVMsは、どれも実システムとの接続点です。日本の開発現場では、ZennのAI時代のレビュー論とPublickeyのLambda MicroVMsが特に実務に近い読み物です。

---

### 1. Gemini 3.5 Flashにcomputer useが追加 — `[Google · Hacker News]`
<https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-computer-use-gemini-3-5-flash/>

GoogleはGemini 3.5 Flashに、画面やアプリを操作するcomputer useツールを追加しました。APIが整っていない業務アプリ、管理画面、社内ツールを扱う自動化では大きな意味があります。一方で、操作権限、監査ログ、失敗時の停止条件を設計しないまま導入すると、便利さよりリスクが先に出ます。

### 2. Cloudflare Self-Managed OAuthが全開発者向けに — `[Cloudflare · Hacker News]`
<https://blog.cloudflare.com/oauth-for-all/>

CloudflareはSelf-Managed OAuthを全開発者に開放し、その裏側で行ったゼロダウンタイム移行も説明しています。OAuthは、アプリ連携や企業向け権限管理の入口になる地味に重要な機能です。WorkersやCloudflare Appsを社内外のシステムとつなぐ場合、この層が整うと実装の選択肢が増えます。

### 3. RubyLLM、Ruby向けの統一AI providerレイヤー — `[Hacker News]`
<https://rubyllm.com/>

RubyLLMは、Rubyから主要AI providerを扱うためのフレームワークです。AIアプリ開発はPythonとTypeScriptに寄りがちですが、Railsで動いている既存業務システムは今も大量にあります。既存のRubyチームが、無理に別スタックへ寄せずにモデル呼び出しやストリーミングを扱えるのは実務上大きいです。

### 4. PRスパムは2000年代初期のメールスパムに似てきた — `[Hacker News]`
<https://www.greptile.com/blog/prs-on-openclaw>

Greptileの記事は、AIで増えた低品質PRを初期のメールスパムになぞらえています。PRを作るコストは下がりましたが、レビューする人間の時間は増えていません。GitHubのPR制限機能ともつながる話で、OSSでも企業monorepoでも、AI生成PRの流量制御と品質基準が必要になります。

### 5. apple/container、Apple Silicon向けLinuxコンテナ実行ツール — `[GitHub Trending]`
<https://github.com/apple/container>

Appleの `container` は、Mac上で軽量VMを使ってLinuxコンテナを作成・実行するツールです。Swiftで書かれ、Apple silicon向けに最適化されています。Mac開発環境ではコンテナ体験が生産性に直結するため、Docker DesktopやColima、OrbStackとの棲み分けを含めて注目したいプロジェクトです。

### 6. browser-compat-db、MDN互換性データをSQLiteへ — `[Simon Willison]`
<https://simonwillison.net/2026/Jun/24/browser-compat-db/#atom-everything>

Simon Willisonさんは、MDNのbrowser compatibility dataをSQLiteデータベースに変換するリポジトリを公開しました。MCPやagentから使いやすい形にするには、信頼できるデータを検索可能な構造へ落とすのが効きます。フロントエンドの互換性調査を毎回検索で済ませるより、こうしたローカルDB化は再現性があります。

### 7. AIで会社のワークフローを作り直したV2EX投稿 — `[V2EX]`
<https://www.v2ex.com/t/1222667>

V2EXでは、長く本格的な開発から離れていた投稿者が、AIを使って会社の業務フローを組み直した話が注目されています。技術的な尖りよりも、業務を知る人が自分で自動化を進められる点が重要です。日本の中小企業でも、在庫、顧客対応、帳票、運用メモのような小さな業務改善から同じ流れが起きそうです。

### 8. Codexの高頻度ディスク書き込みに関するコミュニティ調査 — `[V2EX]`
<https://www.v2ex.com/t/1222665>

V2EXに、Codexが長時間実行時に頻繁にディスクへ書き込むという報告と対策メモが出ています。内容はコミュニティ由来なので検証が必要ですが、agentツールのリソース消費を見る観点としては有用です。CPU、メモリ、tokenだけでなく、ログ、キャッシュ、ファイル監視、ディスクI/Oも運用対象になります。

### 9. AI時代のコードレビューは人ではなく仕組みに向ける — `[Zenn]`
<https://zenn.dev/manalink_dev/articles/ai-coding-era-review-to-dev-process-not-human>

このZenn記事は、AIが実装の大半を担う時代には、レビュー対象を個人ではなく仕組みに向けるべきだと主張しています。悪いコードが出たときに、誰を責めるかではなく、どのプロンプト、コンテキスト、CI、テスト、レビュー導線が弱かったかを見る発想です。AI導入をチーム運用に落とすなら、この視点はかなり重要です。

### 10. AWS Lambda MicroVMs、serverlessで一時的な有状態環境を提供 — `[Publickey]`
<https://www.publickey1.jp/blog/26/aws_lambda_microvms.html>

Publickeyは、AWS Lambda上で一時的にステートフルで隔離された実行環境を用意するAWS Lambda MicroVMsを紹介しています。serverlessの手軽さと、VMに近い隔離・状態保持を組み合わせる狙いです。AI agentのツール実行、短時間のサンドボックス、データ処理基盤などで使い道が広そうです。

---

## 編集後記

今日は英語圏ソース6本、中国語圏ソース2本、日本語ソース2本です。ZennはRSSで取得でき、今日の記事から採用しました。Anthropic Newsも到達可能でしたが、最新の技術系発表は前日のDigestで扱ったため、今回は重複を避けました。まず読むならGemini computer use、AWS Lambda MicroVMs、AI時代のコードレビューの3本です。
