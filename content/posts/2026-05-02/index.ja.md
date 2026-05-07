---
title: "5月2日 · 今日のテック厳選10本"
date: 2026-05-02T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "VSCode", "Copilot", "NetHack", "Ladybird", "Ask"]
categories: ["daily"]
summary: "VSCodeがCopilot使用有無に関わらずcommitに「Co-Authored-by Copilot」を入れる件で1500+コメント、dav2dがAV2デコーダのOSS実装を公開、NetHack 5.0が長年ぶりの大型リリース、Ladybirdブラウザ進捗、Ask.com閉鎖、Russia Poisons Wikipedia。"
---

## 本日のサマリー

ゴールデンウィーク2日目。今日のHN首位はVSCodeの問題——Copilotを使っていないユーザーのcommitにも「Co-Authored-by: Copilot」を自動追加する仕様で、コメント数は1500を超え、開発者コミュニティの怒りが噴出。dav2d（VideoLANのAV2デコーダ）の公開、NetHack 5.0の久々のリリース、Ladybirdブラウザの月次進捗など、OSSの「Big Tech非主導」の側面が並ぶ日でもありました。

---

## 1. VSCode、Copilot 使用に関わらず「Co-Authored-by Copilot」をcommitに自動付与

ソース：[EN · HN Top]
リンク：<https://github.com/microsoft/vscode/pull/310226>

PR上の挙動が問題視され、HNコメント1500件超え。Copilotを有効化していなくても、VSCodeでcommitすると自動的に「Co-Authored-by: Copilot」が追加される仕様。著作権・GPL系強copyleft許諾下では誰が著者か曖昧になる懸念があり、日本企業のリポジトリポリシー（特に金融・防衛・公共調達）にとっては明確な問題。Microsoftが対応するまで、このバージョンのVSCodeを業務利用している場合はcommitテンプレートをチェック。

## 2. dav2d — AV2デコーダのOSS実装

ソース：[EN · HN Top]
リンク：<https://code.videolan.org/videolan/dav2d>

VideoLANチームによるAV2（AV1の次世代）のデコーダ実装公開。dav1dの後継。動画配信技術のロイヤリティフリー継承の重要なステップ。日本のビデオサービス（AbemaTV、ニコニコ、SmartNews等）にとっては、長期的なエンコード戦略の選択肢が広がる動き。

## 3. Do_not_track

ソース：[EN · HN Top]
リンク：<https://donottrack.sh/>

Cookie同意やサードパーティ追跡を、コマンドラインで一括オプトアウトするOSSツール。日本の改正個人情報保護法・cookie同意要件と組み合わせて評価する価値あり。

## 4. NetHack 5.0.0 公開

ソース：[EN · HN Top]
リンク：<https://nethack.org/v500/release.html>

35年以上続くroguelikeの古典が、久々のメジャーアップデート。コミュニティ駆動でこれだけ持続するOSSプロジェクトは稀少で、企業にとってのオープンソースの非経済的価値の象徴的事例として読めます。

## 5. Ladybird ブラウザ — 2026年4月進捗

ソース：[EN · HN Top]
リンク：<https://ladybird.org/newsletter/2026-04-30/>

ChromiumでもFirefoxでもWebKitでもない、ゼロから書く独立ブラウザプロジェクト。2026年内のα目標。Web標準寡占に対するカウンターとして、長期ウォッチリストに入れる価値があります。日本ではブラウザ自体を作る組織はほぼ皆無ですが、Webプラットフォーム多様性の観点で重要な参照点。

## 6. Ask.com 閉鎖

ソース：[EN · HN Top]
リンク：<https://www.ask.com/>

90年代のサーチエンジンが2026年に静かに閉鎖。日本の旧Web世代にも記憶があるはず。一時代の終わり。

## 7. Russia Poisons Wikipedia

ソース：[EN · HN Top]
リンク：<https://www.bettedangerous.com/p/russia-poisons-wikipedia>

調査レポート。ロシア政府主導でWikipedia編集を組織的に汚染しているという証拠の整理。日本のメディア・コンテンツ事業者が「中立的情報源」を引用する際の信頼性について再考を迫られる材料。Wikipediaは便利ですが、戦場でもある。

## 8. macOS VMの速度とサイズ

ソース：[EN · HN]
リンク：<https://eclecticlight.co/2026/05/02/how-fast-is-a-macos-vm-and-how-small-could-it-be/>

Apple Silicon上のmacOS仮想化のベンチマーク。日本のiOSアプリ開発企業のCI/CD基盤を最適化する材料として直接有用。

## 9. カリフォルニア州、自動運転車に交通違反切符を交付開始

ソース：[EN · HN]
リンク：<https://www.bbc.com/news/articles/clypjx3rg2go>

罰金を「メーカー」に発行する仕組み。法的責任主体の議論が現実の行政運用に降りてきた段階。日本の自動運転実証実験（特に福井・福岡）にも今後参考になる先行事例。

## 10. 「Why does it take so long to release black fan versions?」（Noctua）

ソース：[EN · HN]
リンク：<https://www.noctua.at/en/expertise/blog/how-can-it-take-so-long-to-release-black-fan-versions>

Noctua（オーストリア製の高品質PCファンメーカー）が、なぜ黒いファンの開発に時間がかかるかを技術的に説明。ハードウェアエンジニアリングの「見えないコスト」を伝える良記事として、ものづくりの教材になります。日本のメーカーフェア勢にも示唆あり。

---

## 編集後記

今日のマストリードは #1（VSCodeのCo-Authored-by問題）。日本企業のリポジトリ運用ポリシーに直接影響します。#5（Ladybird）は中長期で追う価値のあるプロジェクト。NetHack 5.0（#4）はOSS文化の生命力を確認する週末の癒やし枠。
