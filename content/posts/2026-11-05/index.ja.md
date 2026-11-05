---
title: "11月5日 · 今日のテック厳選10本"
date: 2026-11-05T07:00:00+09:00
draft: false
tags: ["digest", "2026-11", "ai", "opensource", "developer-tools"]
categories: ["daily"]
summary: "Go の JSON API から AI エージェントの運用境界まで、実装後の検証に目を向ける10本です。"
---

# 11月5日 · 今日のテック厳選10本

## 本日のサマリー

今日は、AI を導入することよりも、その出力をどこで検証し、誰が責任を持つかが見える記事が集まりました。標準ライブラリ、データアプリ、コードレビュー、研究支援まで、便利さを運用に落とす設計が共通テーマです。

## ピックアップ

### 1. [Go の新しい JSON API](https://go.dev/blog/jsonv2)
`HN · Go`

Go チームが新しい JSON API を紹介しています。既存 API で蓄積した挙動や拡張性の課題を見直す内容で、サービス側では新旧の混在期間をどう設けるかが重要になります。ライブラリ更新だけでなく、境界のテストを増やす契機になりそうです。

### 2. [NVIDIA auto-ontology が GitHub Trending に](https://github.com/NVIDIA/auto-ontology)
`GitHub Trending · オープンソース`

NVIDIA の auto-ontology は、知識表現の設計と更新を自動化する方向を示すプロジェクトです。RAG の品質は検索以前に、用語や関係をどう管理するかで崩れがちです。自動生成した本体を人がレビューし、差分を追える形にできるかを確認したいところです。

### 3. [Datasette Agent 0.5a0 の panel](https://simonwillison.net/2026/Nov/3/datasette-agent/)
`Simon Willison · AIツール`

Datasette Agent に、会話とテーブル・クエリ画面を並べる panel が追加されました。データを見ながら生成したアプリを直せるため、チャットを単なる回答欄ではなく作業面として扱えます。業務導入では、生成結果を元データと同時に確認できることが特に効きます。

### 4. [SSH、SFTP、AI をまとめたネイティブクライアント](https://www.v2ex.com/t/1254583)
`V2EX · 開発ツール`

三つのプラットフォーム向けに作られた SSH クライアントが、SFTP と AI 機能も統合しています。リモート作業の道具は機能数より、鍵の保管、再接続、端末間の状態同期で評価されます。日常運用の細部をどう処理しているかを追いたい発表です。

### 5. [Synology NAS のランサムウェア被害と SSD キャッシュ復旧](https://www.v2ex.com/t/1254586)
`V2EX · ストレージ`

NAS がランサムウェア被害を受けた後、SSD キャッシュからの復旧を試みた記録です。個別環境の成功談を一般化はできませんが、バックアップを「存在すること」でなく「戻せること」として扱う重要性がよく分かります。小規模チームでも復元訓練は後回しにしにくい領域です。

### 6. [EasyEEG：脳波研究の伴走エージェント](https://zenn.dev/hackathons/google-cloud-japan-ai-hackathon-vol5/projects/bf62c6a94633a5)
`Zenn · Agentic AI`

EasyEEG は実験計画、電極準備、波形観察、解析を支援するプロジェクトです。研究・医療に近い領域では、モデルの賢さだけでなく、承認フロー、倫理ガードレール、データ最小化がプロダクト要件になります。そこを設計に含めている点が参考になります。

### 7. [Hachi Atelier：写真から印刷可能な鉢へ](https://zenn.dev/katsunori04/articles/a3fb70431bbb1c)
`Zenn · 生成AI`

植物の写真を入力に、設計案から STL までを作る AI エージェントの紹介です。生成コードは分離した sandbox で動かし、形状の検査と修正を繰り返します。物理世界へ出力する AI では、生成の巧さより検証ループの堅さが品質を決めます。

### 8. [Octoverse 2026：TypeScript が2年連続で最多](https://www.publickey1.jp/blog/26/github2typescriptrustosscc_switchomarchygithub_octoverse_2026.html)
`Publickey · OSS`

GitHub Octoverse 2026 の紹介では、TypeScript が最も使われる言語を維持し、Rust はプルリクエスト増加率で目立ったとされます。統計は採用判断の答えではありませんが、採用市場、SDK、保守者の集まり方を考える材料にはなります。日本のプロダクト開発でも周辺エコシステムの厚みは無視できません。

### 9. [Copilot Dreaming の個人メモリ構想](https://www.publickey1.jp/blog/26/github_copilot_dreaminggithub_universe_2026.html)
`Publickey · GitHub Universe`

Copilot Dreaming は、開発作業を振り返り、個人向けの記憶やガイダンスをバックグラウンドで整理する機能です。便利さの裏で、何を記憶するか、誤った記憶をどう消すか、組織の情報をどこまで混ぜないかが問われます。導入前に運用ルールを置くべきタイプの機能です。

### 10. [Kimi K3.1 Pro のモデル重み公開](https://huggingface.co/moonshotai/Kimi-K3.1-Pro)
`HN · オープンモデル`

Kimi K3.1 Pro の重み公開は、ローカル評価と内製の選択肢を増やします。実際の採用ではベンチマークだけでなく、ライセンス、推論コスト、VRAM、ツール呼び出しの安定性を並べて見る必要があります。重みがあることと、運用できることは別問題です。

## 編集後記

本日のキーワードは「検証可能な AI」です。Datasette Agent と Hachi Atelier は、生成の前後に人が確認できる場所を作るという意味で特に読みどころがあります。Anthropic のニュースページには直近24時間で確認できる技術発表がなかったため、古い記事で枠を埋めませんでした。
