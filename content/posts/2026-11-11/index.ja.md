---
title: "11月11日 · 今日のテック厳選9本"
date: 2026-11-11T07:00:00+09:00
draft: false
tags: ["digest", "2026-11", "ai", "agents", "cloud"]
categories: ["daily"]
summary: "モデル更新の先にある、エージェントの実行境界と運用の引き継ぎを追います。"
---

# 11月11日 · 今日のテック厳選9本

## 本日のサマリー

今日はモデルそのものより、AI エージェントを現実のシステムへ置いたときの話が目立ちます。実行環境、検証、引き継ぎの設計まで揃えて初めて、開発速度を品質に変えられます。

## ピックアップ

### 1. [Claude Fable 5.2 と Mythos 5.2](https://www.anthropic.com/claude-fable-and-mythos-5-2)
`Anthropic News · モデル`

Anthropic は難度の高い技術作業向けとして Fable 5.2 と Mythos 5.2 を発表しました。コーディング、金融、科学での能力を掲げていますが、既存プロダクトの既定モデルを替える前にはツール呼び出しと失敗時の挙動を見直すべきです。社内ベンチマークを固定し、リリースごとの差分を残す運用が効きます。

### 2. [AlphaProof Code](https://deepmind.google/blog/introducing-alphaproof-code/)
`Hacker News · AI研究`

DeepMind の AlphaProof Code は、数学的な証明とコード能力の接点を前に進める試みです。すぐに業務アプリへ入れる技術ではありませんが、テストが通ることと仕様を満たすことは別だという原点を思い出させます。コンパイラや決済のような高保証領域では、形式手法の実用化を追う価値があります。

### 3. [agent-browser が GitHub Trending に](https://github.com/vercel-labs/agent-browser)
`GitHub Trending · エージェントツール`

agent-browser はブラウザ操作を AI エージェント向けの CLI として提供します。Web の実画面を扱えることは便利ですが、ログイン状態、ダウンロード、遷移先までがセキュリティ境界になります。まずは専用アカウント、対象ドメイン制限、操作ログの保存から始めるのが安全です。

### 4. [llm-gemini 0.36](https://simonwillison.net/2026/Nov/10/llm-gemini/)
`Simon Willison · 開発者ツール`

Simon Willison は Gemini 用 LLM プラグインを更新しました。小さなアダプターでも、モデルの話題を再現可能なコマンドとログに変えられる点が重要です。チームで使うスクリプトは、モデル名だけでなくパラメータと実行時点も記録しておきましょう。

### 5. [AI が書いたコードは将来事故を起こすか](https://www.v2ex.com/t/1255786)
`V2EX · 開発者コミュニティ`

この議論では、生成量が増えても設計、レビュー、受け入れ試験が追いつくかが論点になりました。良い実践は、各エージェント変更に変更理由、検証方法、不明点を残して次の担当者へ渡すことです。実装速度だけを測ると、QA と保守に負債が移るだけになりかねません。

### 6. [Claude Code で最近使っている Tips](https://zenn.dev/oikon/articles/claude-code-recipe)
`Zenn · AI開発`

Claude Code の使い方を具体的にまとめた Zenn の記事です。個人の手元技だけで終わらせず、環境設定や規約を共有可能な形にする視点が大切です。コンテキスト、権限、完了条件を再現できてこそ、エージェントはチームの道具になります。

### 7. [SELECT だけなのに PostgreSQL のマイグレーションが待たされた理由](https://zenn.dev/naokisuzuki27/articles/cb1a5ac0e23763)
`Zenn · データベース`

SELECT 実行中でも、マイグレーションはロック待ちで失敗し得ます。SQL を読み書きだけで分類するのではなく、トランザクション時間、ロック互換性、デプロイ時間帯まで含めて考える必要があります。タイムアウト、観測、ロールバックを先に準備しておくと障害対応が短くなります。

### 8. [.NET 11 正式リリース](https://www.publickey1.jp/blog/26/net_11cjitaot.html)
`Publickey · .NET`

.NET 11 では C# 15 の union types、JIT と AOT、コマンドラインツールが強化されました。日本企業の .NET 基盤では、新機能よりビルド時間、コンテナサイズ、ネイティブ配布との相性が移行判断を左右します。まず独立したサービスで計測してから範囲を広げるのが現実的です。

### 9. [Agent Substrate と gVisor 関連を CNCF へ](https://www.publickey1.jp/blog/26/googlekubernetes10aiagent_sustrategvisorcncf.html)
`Publickey · Kubernetes`

Google は Kubernetes 上でエージェントを効率よく動かすための Agent Substrate と gVisor 関連の取り組みを CNCF へ寄贈しました。ツール呼び出しとネットワーク待ちが多いエージェントでは、隔離、スケジューリング、コスト配賦が設計の中心になります。プラットフォーム担当者は、公開後の導入条件と既存クラスタへの影響を追いたいところです。

## 編集後記

今日は agent-browser と PostgreSQL のロック記事を並べて読むのがおすすめです。前者は行動の境界を、後者は本番システムの境界を示してくれます。9本に絞ったのは、V2EX の他の技術系上位記事が販促中心で、Anthropic にも直近の技術発表が1件しかなかったためです。
