---
title: "6月1日 · 今日のテック厳選10本"
date: 2026-06-01T07:00:00+09:00
draft: false
tags: ["digest", "2026-06", "pyodide", "openbsd", "aws", "claude", "zenn", "markitdown", "tts"]
categories: ["daily"]
summary: "Pyodide を Service Worker に載せて ASGI アプリをブラウザ単体で動かす実装、OpenBSD チームによる openrsync 公開、AWS Interconnect の 500Mbps 無料枠。Claude Code の token 節約術と markitdown も今日の見どころ。"
---

## 本日のサマリー

月曜の朝。先週末は Anthropic の Opus 4.8 と Series H で持ちきりでしたが、今日はもう少し手触りのある話題が並びます。Simon Willison が Pyodide + Service Worker で Datasette Lite の長年の課題を片付け、OpenBSD チームが rsync のクリーンな再実装を公開、AWS は Interconnect の multicloud 接続を 500Mbps まで無償化しました。Zenn では「Claude Max 20x でも足りない人向けの節約 8 選」が圧倒的トレンド。日本のチームが今週から普通に使える材料が多めです。

---

### 1. Simon Willison：Service Worker で Pyodide を駆動して ASGI アプリをブラウザで動かす — `[Simon Willison]`
<https://simonwillison.net/2026/May/30/pyodide-asgi-browser/>

Datasette Lite は長らく「`<script>` タグから Python が動かせない」課題を抱えていました。原因は Pyodide が Web Worker 上にあり、メインスレッドの DOM や fetch を直接扱えなかったこと。今回 Simon は Claude Code for web 上で Opus 4.8 に書かせ、Pyodide を Service Worker に移し、fetch を ASGI アプリに転送する構成に。FastAPI / Datasette がそのままブラウザで動きます。「サーバーレス」を文字通り実現するパターンとして、社内ツールの配布形態を見直すきっかけになりそうです。

### 2. OpenBSD チームによる openrsync — `[Hacker News · 184 pts]`
<https://github.com/kristapsdz/openrsync>

BSD ライセンス、純 C、依存最小で rsync プロトコル互換。HN コメント欄は「ようやく監査しやすい実装が来た」「OpenSSH 一本化後の供給網としても意味がある」と前向きです。エンタープライズで GPL 起因のライセンス確認に消耗していたチーム、組み込みや受託案件で軽量な同期ツールが必要なチームには良い選択肢になりそうです。

### 3. Pandoc Templates 公式集約サイト — `[Hacker News · 274 pts]`
<https://pandoc-templates.org/>

LaTeX / Beamer / HTML / reveal.js / DOCX / EPUB まで、Pandoc 用テンプレートを一箇所に集めたコミュニティ・サイト。社内ドキュメントや技術書執筆を Pandoc に寄せたい場合、最初の壁は「テンプレートをゼロから組む手間」でした。AI に下書きを書かせて Pandoc で清書する、というワークフローを敷きたい人にとって今日一番実用的なブックマークです。

### 4. 16GB AMD GPU では vLLM/SGLang より Transformers のほうが速い？ — `[V2EX · Local LLM]`
<https://www.v2ex.com/t/1216752>

中国側コミュニティでのベンチ報告。コンシューマー帯 16GB AMD カード上で、vLLM と SGLang よりも素の HF Transformers のほうがスループットと VRAM 双方で良かった、と。原因は ROCm 経路における PagedAttention のフォールバック実装と、小 batch でのフレームワークオーバーヘッド。AMD でローカル LLM を運用するチームには、信仰ではなく実測ベースで構成を組み直す材料になります。

### 5. クラウドストレージへの E2E 暗号化バックアップ構成 — `[V2EX · 程序员]`
<https://www.v2ex.com/t/1216774>

スレッドで挙がっているスタックは rclone crypt、Cryptomator、Restic / Kopia、鍵管理に age。日本でも iCloud / Google Drive / OneDrive をオブジェクトストレージ代わりに使うケースが増えており、「クラウドは信頼しない、ローカルだけ信頼する」前提の構成は十分参考になります。個人開発者の DR 計画の出発点にどうぞ。

### 6. Claude Max 20x でも足りないので、トークン節約のためにやったこと8選 — `[Zenn · 207 likes]`
<https://zenn.dev/acntechjp/articles/1396e20b5167ce>

本日 Zenn 圧倒的トレンド。CLAUDE.md による索引固定、コンテキストの明示的剪定、タスク分割、サブエージェント活用、コードベース要約の事前生成など。Claude Code を毎日触っている人は「あるある」しかないはず。Max 20x 帯で枯渇する現象が 5 月末から目立っており、価格ではなく使い方で殴る方向の解が日本側で先に整理された格好です。

### 7. AWS Interconnect - multicloud に 500Mbps までの無料枠 — `[Publickey · インフラ]`
<https://www.publickey1.jp/blog/26/aws500mbpsaws_interconnect_-_multicloud.html>

AWS が GCP / Azure との専用線接続を 500Mbps まで無償化。マルチクラウド戦略を取る日本企業にとって、これまで最大のネックだった「出口課金」が部分的に消えます。Re:Invent 前に基盤系の値下げが続く流れも合わせて、社内のクラウド戦略レビューに直接効く材料です。

### 8. microsoft/markitdown：Office / PDF / 画像 / 音声を LLM 用 Markdown に一発変換 — `[GitHub Trending · 2,759 stars today]`
<https://github.com/microsoft/markitdown>

Microsoft 製の Python ツール。docx / pptx / xlsx / pdf / 画像 / 音声を、LLM が読みやすい Markdown に変換します。社内 RAG / ナレッジ基盤を構築する際の前処理が一気に楽になる定番候補。134K star を超えてなお伸びており、「社内 AI を本気でやる」局面に入った企業が増えていることの証左です。

### 9. OpenBMB/VoxCPM2：オープンソースの多言語 TTS — `[GitHub Trending · 639 stars today]`
<https://github.com/OpenBMB/VoxCPM>

清華大学発 OpenBMB チームによる第二世代 TTS。tokenizer-free、多言語対応、声の複製や創作的なボイスデザインまで可能。日本語の発音品質次第ですが、社内動画ナレーション、ポッドキャスト試作、AI 動画生成用の音声差し替えなど、自前運用が成立する局面が増えそうです。

### 10. EveryInc/compound-engineering-plugin：Claude Code / Codex / Cursor 共通プラグイン — `[GitHub Trending · 243 stars today]`
<https://github.com/EveryInc/compound-engineering-plugin>

「複合エンジニアリング」（タスク分解 + 並列サブエージェント + コンテキスト管理）を、Claude Code / Codex / Cursor すべてに対応する公式プラグインとして配布。Zenn の節約 8 選を人手でやるか、こうしたプラグインで再利用可能にするか、というレベル感の選択になってきました。チーム標準として導入を検討する価値があります。

---

## 編集後記

今日の通底テーマは「予算を増やさずに AI ツールのレバレッジを伸ばす」。Pyodide の構成変更も、Claude の節約術も、AWS の無償化も、全部同じ方向を向いています。明日からの仕事に直接効くのは **#6（Claude 節約 8 選）** と **#8（markitdown）** の組み合わせ。気持ちに余裕があれば **#1（Pyodide + Service Worker）** を読むと、社内ツール配布のメンタルモデルが少し変わるはずです。
