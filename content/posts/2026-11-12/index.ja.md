---
title: "11月12日 · 今日のテック厳選10本"
date: 2026-11-12T07:00:00+09:00
draft: false
tags: ["digest", "2026-11", "agents", "testing", "infrastructure"]
categories: ["daily"]
summary: "エージェント、テスト、基盤を安全に動かすための境界設計が今日の主題です。"
---

# 11月12日 · 今日のテック厳選10本

## 本日のサマリー

今日は派手なモデル比較より、強い仕組みをどう運用可能にするかがテーマです。エージェントがブラウザやクラウドへ近づく一方で、障害事例とサンドボックスは、権限・観測・停止条件の重要性を改めて示しています。

## Picks

### 1. [AWS Emulator](https://github.com/aws/aws-emulator)
`Hacker News · クラウド開発`

AWS Emulator は Rust と Docker を使った AWS サービスのローカルエミュレータで、エージェントを使う開発・テストも想定しています。ローカルで再現性を上げられるのは有益ですが、IAM や非同期処理まで本番と同じとは限りません。実クラウドへ当てる小さな統合テストを残して、差分を早めに検出するのがよさそうです。

### 2. [誤報の火災警報が Jane Street の NYC データセンターを水没させかけた話](https://michael.bacarella.com/2026/11/10/false-smoke-alarm-jane-street-datacenter/)
`Hacker News · インシデント`

誤った警報と浸水を扱うインシデント報告です。施設設備の話に見えても、センサー、対応者、オンコール手順のつなぎ目はソフトウェアの依存関係と同じく壊れます。アプリケーションだけでなく、周辺の通知・設備・復旧手順まで演習対象にしたいところです。

### 3. [Gemini Decisions API](https://simonwillison.net/2026/Nov/11/gemini-decisions-api/)
`Simon Willison · AI API`

Simon Willison が、構造化された判断タスク向けの Gemini Decisions API を取り上げています。出力形式が固定されればパースの不安定さは減りますが、判断そのものの妥当性は別問題です。入力、決定記録、人へのエスカレーションを監査可能にして使うべきでしょう。

### 4. [GitHub Trending の agent-browser](https://github.com/vercel-labs/agent-browser)
`GitHub Trending · エージェントツール`

agent-browser は AI エージェント向けにブラウザ自動化を CLI として提供します。実際のセッションや操作に届くからこそ便利で、同時に権限設計が重要になります。専用アカウント、許可ドメイン、再現できる操作ログを最初から用意しておきたいです。

### 5. [16 GB の Mac mini 2台より 32 GB の1台か](https://www.v2ex.com/t/1256326)
`V2EX · 開発者コミュニティ`

この議論は、合計メモリと単一プロセスの必要メモリを混同しないための良い例です。ローカル LLM、コンテナ、大きなビルドでは、ピークのワーキングセットをまず測るべきです。2台目はスループットを上げられても、1プロセスの OOM を解決するわけではありません。

### 6. [Magpie 作者 yetone の自動化ワークフローを探る](https://www.v2ex.com/t/1256327)
`V2EX · 自動化`

Magpie の自動生成ワークフローを研究したいというスレッドです。再利用すべきなのは目に見えるプロンプトより、トリガー、取得コンテキスト、実行、検証からなる閉ループでしょう。停止条件と検証がない自動化は、失敗を後工程へ送るだけになりがちです。

### 7. [ISUCON 2026 ソロ参加記：自作ハーネスで Claude Code をほぼ無人運転](https://zenn.dev/5alt_nacl/articles/isucon2026-solo-ai-agent)
`Zenn · AI支援開発`

自作ハーネスによって Claude Code を競技中に回し続けた記録です。注目点は無人化そのものではなく、エージェントを制約とフィードバックを持つループにしたことです。チーム利用では、ベンチマーク、停止条件、手動引き継ぎを先に設計すると現実的です。

### 8. [Bedrock AgentCore Gateway の Web Search を Claude Desktop で使う](https://zenn.dev/aws_japan/articles/agentcore-gateway-websearch-cognito)
`Zenn · クラウド連携`

AWS Japan が Cognito を介し、AgentCore Gateway の Web Search を Claude Desktop へつなぐ方法を解説しています。これはモデル機能というより、ID と委譲権限の設計問題です。ゲートウェイのポリシーは狭く始め、拒否されるケースもテストに含めるのが安全です。

### 9. [Playwright が Bun を正式サポート](https://www.publickey1.jp/blog/26/playwrightbun.html)
`Publickey · テスト`

Playwright 1.65.0 では、テストランナーを Bun で実行することが正式にサポートされました。Bun を TypeScript ツールチェーンへ採用済みの組織には魅力がありますが、ブラウザバイナリや CI イメージとの組み合わせが安定性を左右します。共有パイプラインの標準を変える前に、既存スイートを通して測定しましょう。

### 10. [AWS Nitro Sandboxes が AI エージェント向けに提供開始](https://www.publickey1.jp/blog/26/awsaiec2vmaws_nitro_sandboxes.html)
`Publickey · クラウドセキュリティ`

AWS Nitro Sandboxes は、AI エージェントに強い隔離とネイティブ EC2 に近い性能を提供します。ただし、隔離は実行場所の境界であって、アクセス権の判断まではしてくれません。最小権限の認証情報、外向き通信制御、短いデータ保持期間を組み合わせる必要があります。

## 編集後記

今日は Jane Street の障害報告と Nitro Sandboxes を続けて読むのがおすすめです。どちらも、複雑なシステムを大事故にしないための境界を扱っています。Anthropic のニュースページは取得できましたが、当日付の新しい技術発表は確認できなかったため、無理に入れず基盤運用の記事を採用しました。
