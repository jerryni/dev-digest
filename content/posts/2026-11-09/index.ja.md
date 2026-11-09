---
title: "11月9日 · 今日のテック厳選10本"
date: 2026-11-09T07:00:00+09:00
draft: false
tags: ["digest", "2026-11", "developer-tools", "ai", "security"]
categories: ["daily"]
summary: "ローカルAI、デスクトップ、セキュリティ自動化を通じて、新しい道具を運用境界に収める方法を追います。"
---

# 11月9日 · 今日のテック厳選10本

## 本日のサマリー

今日の話題は派手な新機能より、ツールを実運用へ持ち込む際の境界設計です。GPU を使う Web アプリ、ローカル推論、agent のブラウザ操作は、便利さと同時にデータ・権限・監査の設計を要求します。

## ピックアップ

### 1. [KetchUp：Rust と WebGPU によるオープンソースの3Dモデラー](https://ketchup3d.github.io/app/)
`Hacker News · グラフィックス`

KetchUp はブラウザでの3Dモデリングを狙うプロジェクトです。WebGPU が実用域に入ると、従来デスクトップ前提だった制作ツールにも配布形態の選択肢が増えます。導入判断では、入出力形式と大規模モデル時の挙動を先に確認したいところです。

### 2. [Dux：Wayland 向けのオープンソースデスクトップ Shell](https://duxlabs.dev/)
`Hacker News · Linux`

Dux は shell、ファイル管理、テーマを一つのプロジェクトで扱います。Wayland 対応は見た目だけでなく、入力、ウィンドウ制御、拡張性まで含む長い仕事です。Linux デスクトップを支える技術選択を読む題材としても面白いです。

### 3. [Llama-modchip：GPU なし・64GB RAM で 284B DeepSeek を動かす](https://github.com/synchopate/llama-modchip)
`Hacker News · ローカルAI`

大容量メモリを使って巨大モデルをローカル実行する試みです。誰もが自前推論へ移るという話ではありませんが、量子化、速度、データ持ち出し制約のトレードオフを具体的に考えられます。機密データを扱う組織では、実行可能性そのものが選択肢を広げます。

### 4. [SQLite 拡張 parse_number() を C と Rust で比較](https://simonwillison.net/2026/Nov/8/sqlite-parse-number-c-vs-rust/)
`Simon Willison · データ基盤`

小さな SQLite 拡張を題材に C と Rust の実装を比較しています。こうした小規模な部品は、言語選定を試すには格好の場所です。コード量だけでなく、配布、ビルド、障害時の調査しやすさまで見ると判断が変わります。

### 5. [agent-browser が GitHub Trending に登場](https://github.com/vercel-labs/agent-browser)
`GitHub Trending · Agent`

agent-browser は agent にブラウザ操作を与える CLI です。実アカウントやダウンロードに触れるため、導入時には権限を狭くし、許可ドメインと操作ログを持たせるべきです。成功率より、誤操作を止められる設計を先に検証しましょう。

### 6. [Anthropic Skills が GitHub Trending に登場](https://github.com/anthropics/skills)
`GitHub Trending · 開発プロセス`

再利用可能な agent 向け手順を Skills として管理するリポジトリです。手順を共有するだけでは安全にならず、必要な権限、入力、完了条件も同じ変更履歴に置く必要があります。社内で育てるなら、コードと同様にレビュー対象にするのが自然です。

### 7. [FinallyShell：Go 製の SSH クライアント](https://www.v2ex.com/t/1255296)
`V2EX · 開発者コミュニティ`

FinalShell に近い使い勝手を Go で再実装したという紹介です。SSH クライアントの価値は画面より、鍵の扱い、踏み台、切断復帰といった日常の摩擦で決まります。既存ツールの不満を限定して解く個人開発の参考例でもあります。

### 8. [Terminal Spike：SSH、Mosh、tmux、Agent を備える Android 端末](https://www.v2ex.com/t/1255422)
`V2EX · モバイル運用`

Android 上でリモート作業をまとめるオープンソース端末です。緊急対応をモバイルに広げるなら、便利なコマンド以上に、短命な認証情報と操作履歴が重要になります。本番環境へ直結する経路は、特に小さく保ちたいです。

### 9. [明治元年の開始日変更で単体テストが失敗した話](https://zenn.dev/xin9le/articles/9a1cf8e10494d6)
`Zenn · テスト`

暦データの更新がテストを壊した事例です。日付、タイムゾーン、暦、行政区分は外部の不変量ではありません。データの出所と版をテストに残しておくと、コードを変えていない CI 失敗を説明しやすくなります。

### 10. [Zero Wire、GitHub Actions、Claude による脆弱性チェック自動化](https://zenn.dev/tomipetit/articles/zero-wire-github-actions)
`Zenn · セキュリティ`

脆弱性情報と公開サーバーの確認を日次フローにつなげた実践です。LLM の判定は修正指示ではなく、確認すべきチケットに留める設計が堅実です。外部資産に近い自動化ほど、人の確認、通知、ロールバックを外せません。

## 編集後記

今日はローカル実行と自動化を、運用上の責任分界から読み直す10本です。まずは Zenn の暦データ事例と脆弱性チェックを読むと、変化する外部データと agent をどう扱うかが具体的に見えてきます。Anthropic News は当日分として確認できる技術更新がなかったため、古い記事は採用しませんでした。
