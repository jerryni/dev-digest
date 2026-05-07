---
title: "5月3日 · 今日のテック厳選10本"
date: 2026-05-03T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Kimi", "DeepSeek", "Mercedes", "Haskell"]
categories: ["daily"]
summary: "Kimi K2.6がコーディング挑戦でClaude/GPT-5.5/Geminiに勝利、DeepClaudeはClaude CodeのループをDeepSeek V4 Proで動かす実装、OpenAI o1がER triageで医師を上回る、「Agentic Coding Is a Trap」、メルセデスが物理ボタン復活、TUIsの復権。"
---

## 本日のサマリー

連休3日目。今日の主旋律は「中国製オープンウェイトAIモデルが開発者ツール領域で本当に台頭してきた」です。Kimi K2.6が公開コーディング挑戦でClaude・GPT-5.5・Geminiを上回り、HNでバズった「DeepClaude」はClaude CodeのagentループをDeepSeek V4 Proで動かして劇的なコスト削減を示しました。同時にOpenAI o1がハーバードのER triage試験で医師を上回ったというニュースは、医療AIの規制議論に大きな影響を与えそうです。Agentic Codingに対する懐疑と、TUIs復権の話題が並ぶのも今週の特徴。

---

## 1. Kimi K2.6、公開コーディング挑戦でClaude/GPT-5.5/Geminiに勝利

ソース：[EN · HN Top]
リンク：<https://thinkpol.ca/2026/04/30/an-open-weights-chinese-model-just-beat-claude-gpt-5-5-and-gemini-in-a-programming-challenge/>

Moonshot AIのオープンウェイトモデルKimi K2.6が、3社の閉鎖大手モデルを上回る結果を出した記事。HN 200+コメントの多くは「中国オープンモデルが開発者タスクで本当に先行したのは初めて」と認める論調。日本企業がオンプレ・社内利用で開発支援AIを検討する場合、Kimi系も評価軸に入れる必要があります。

## 2. DeepClaude — Claude CodeのループをDeepSeek V4 Proで

ソース：[EN · HN Top]
リンク：<https://github.com/aattaran/deepclaude>

GitHubで公開された実装。Claude CodeのagentループをDeepSeek V4 Proに置き換えてコストを大幅削減、HN 280コメントには実測データが多数。日本のSI現場で「Claude Codeを試したいがコストが厳しい」という相談が増えていますが、この種の代替実装は実用的選択肢として知っておく価値があります。

## 3. OpenAI o1、ER triageで医師より高精度（67% vs 50-55%）

ソース：[EN · HN Top]
リンク：<https://www.theguardian.com/technology/2026/apr/30/ai-outperforms-doctors-in-harvard-trial-of-emergency-triage-diagnoses>

ハーバード医学校の臨床試験。o1が救急トリアージの診断で医師を明確に上回るという結果。日本の医療AI規制（PMDA、医療機器プログラム）の枠組みでこのデータをどう扱うか、製品化を進めるスタートアップにとって今期の論点になります。

## 4. 「Agentic Coding Is a Trap」

ソース：[EN · HN Top]
リンク：<https://larsfaye.com/articles/agentic-coding-is-a-trap>

冷静なAgentic Coding批判。品質よりも「自分は工学をやっている」という錯覚を生む点が問題、と。日本のSIで AI Coding Agent導入の旗振り役をしている人は、必ず一度通っておくべきテキスト。

## 5. メルセデス・ベンツ、物理ボタンの復活を約束

ソース：[EN · HN Top]
リンク：<https://www.drive.com.au/news/mercedes-benz-commits-to-bringing-back-phycial-buttons/>

ベンツが「全タッチパネル化は間違いだった」と認め、次世代車種で物理ボタンを戻すと発表。500+コメントは概ね歓迎。日本車メーカ（トヨタ、ホンダ、日産）のHMI設計にも参考になる転換点。

## 6. Why TUIs are back

ソース：[EN · HN Top]
リンク：<https://wiki.alcidesfonseca.com/blog/why-tuis-are-back/>

lazygit, k9s, helix, Claude Codeなど、ターミナルUI再興の背景を整理した長文。「Webブラウザがアプリケーションコンテナとして使われすぎた」という反動、という見方。日本の開発者ツールベンダーには、UIの設計言語の選択肢が広がっているという情報。

## 7. A couple million lines of Haskell — Mercuryの本番運用

ソース：[EN · HN Top]
リンク：<https://blog.haskell.org/a-couple-million-lines-of-haskell/>

Mercuryが200万行のHaskellを本番運用しているというエンジニアリング記事。fintechにおけるHaskell採用は今でも珍しいが、CI、人材確保、デバッグ運用など実務知見が網羅されており希少。

## 8. Specsmaxxing — YAMLで仕様を書きAI psychosisを克服

ソース：[EN · HN]
リンク：<https://acai.sh/blog/specsmaxxing>

「AIに口頭で要件を伝えても噛み合わない、構造化された仕様書（YAML）で書け」という主張。日本のSIにおける「仕様書文化」が、AI時代に再評価されている現象として読むと面白い。

## 9. Show HN: WhatCable — Macメニューバーで USB-Cケーブルの実力を表示

ソース：[EN · Show HN]
リンク：<https://github.com/darrylmorley/whatcable>

Swift/SwiftUI製の小ツール。USB-Cケーブルの「見た目同じでも実力が全然違う」問題を解決。日本のオフィス引き出しでも常識化している悩みを救う実用ツール。

## 10. AWS App Runner、4月30日で新規受付停止——AWS複数サービスの終了計画

ソース：[JA · Publickey]
リンク：<https://www.publickey1.jp/blog/26/aws_app_runner430amazon_rds_custom_for_oracle1aws.html>

AWSが9種のサービスの新規受付停止と4種のサービス終了を発表。App Runnerは4月30日でメンテナンスモードへ。Amazon RDS Custom for Oracleは1年後に終了。日本企業で該当サービスを利用中のチームは、移行先（ECS、Fargate、SQL Server等）の検討が必要です。

---

## 編集後記

今日の必読は #1（Kimi K2.6）と #2（DeepClaude）。中国オープンソースの開発者ツール領域での台頭は、日本のSIが採用するAIの選択肢に直接影響します。#3（OpenAI o1 in ER）は医療AI規制の議論を再加速させる材料になります。
