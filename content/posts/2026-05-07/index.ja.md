---
title: "5月7日 · 今日のテック厳選10本"
date: 2026-05-07T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Claude", "DeepSeek", "TypeScript", "AWS", "auth"]
categories: ["daily"]
summary: "Simon Willisonがvibe codingとagentic engineeringの境界が崩れつつあると述べ、Anthropicは Claude Opus 4.7 を発表、DeepSeek V4 Proは月末まで75% OFF、AWS中東UAEリージョン障害は復旧まで数か月、TypeScript 7.0（Go移植版）がBetaに。"
---

## 本日のサマリー

今日の主旋律は「エージェントがエンジニアリングの定義を書き換えつつある」という流れです。Simon Willisonがvibe codingとagentic engineeringの境界が技術的にほぼ消えつつあると認めた記事と、HNでバズっている「The bottleneck was never the code」を併せて読むと、コードを書く速度がボトルネックでなくなった世界の不安と機会の両方が見えてきます。AI各社の動きはClaude Opus 4.7のリリースとDeepSeek V4 Proの大幅値下げ。日本企業に直接効くのはTypeScript 7.0 Beta（Go移植版で10倍高速化）と、AWS中東UAEリージョンの長期障害。後者は中東進出している商社・ECには無視できない事案です。

---

## 1. Simon Willison：vibe codingとagentic engineeringの境界が消えつつある

ソース：[EN · Simon Willison]
リンク：<https://simonwillison.net/2026/May/6/vibe-coding-and-agentic-engineering/>

Simon は長らく「vibe coding（コードを見ずに動作だけ確認）」と「agentic engineering（エージェントに書かせるが人間がレビュー）」を区別してきましたが、最新ポストではツールの進化で両者が事実上同じになりつつあると認めました。日本のチームにとって示唆的なのは「レビュー頻度がある閾値を下回ると、自分はagentic engineeringのつもりでも実態はvibe coding」という指摘です。社内コーディング規程をAI時代に合わせて見直す段階に来ています。

## 2. The bottleneck was never the code

ソース：[EN · HN Top]
リンク：<https://www.thetypicalset.com/blog/thoughts-on-coding-agents>

論旨はシンプルで、コードを書くこと自体は元々ボトルネックではなく、要件定義・デバッグ・調整・コンテキスト把握こそがボトルネックだった、というもの。LLMがコーディングを高速化したことで、両端のボトルネックがより目立つようになったと述べています。SIerの現場では「実装より仕様確定が遅い」という古典的な問題と直結する話で、PMやテックリードが共有する価値があります。

## 3. From Supabase to Clerk to Better Auth

ソース：[EN · HN Top]
リンク：<https://blog.val.town/better-auth>

Val Townの認証基盤移行記。Supabase Auth → Clerk → Better Auth（OSS、セルフホスト可）の変遷で、特に Clerk から離脱した理由のセクションが読みどころです。SaaS価格と機能ロックインのトレードオフを定量的に書いており、日本のスタートアップでAuth0/Clerkのコストに悩んでいるチームには参考になります。Better Authは TypeScript 製でNext.js等とも親和性が高い。

## 4. V2EX：2026年、PodmanかDockerか

ソース：[ZH · V2EX]
リンク：<https://www.v2ex.com/t/1208359>

中国の開発者コミュニティで盛り上がっているコンテナランタイムの選択論。2026年現在、企業現場ではdaemonless・rootlessなPodmanの採用が増えてきており、新規プロジェクトはPodmanで、既存のDockerは無理に切らない、という現実解が支持されています。日本でもRedHat系を採用しているSIerでは同じ判断が増えているはずで、海外コミュニティの温度感を確認する一本として。

## 5. V2EX：2026年なのに、Android/HarmonyOSプロジェクトのパスに中国語が使えない問題

ソース：[ZH · V2EX]
リンク：<https://v2ex.com/t/1204805>

ローカライゼーションがツールチェーンの最下層でいかに後回しにされるかを示す事例。日本語のディレクトリ名でビルドが通らない問題は2010年代に何度も繰り返された話で、HarmonyOSが急成長した2024-2025を経ても、依然として直っていません。多言語対応をプロダクトに組み込む側の立場で読むと、教訓が多い。

## 6. AWS中東UAEリージョン障害、復旧まで数か月

ソース：[JA · Publickey]
リンク：<https://www.publickey1.jp/blog/26/awsuae2.html>

地政学的衝突に起因する物理層攻撃でME-CENTRAL-1が深刻な被害を受け、AWSは2か月ぶりの状況報告で「完全復旧には数か月」と発表。クラウドサービスでこの規模・期間のリージョン障害は過去にほぼ例がありません。中東に拠点を持つ日系商社・物流・ECは、ME-SOUTH-1（バーレーン）あるいはEU-WEST-1への退避設計を改めて点検すべきタイミング。BCP/DR計画への直接的な示唆があります。

## 7. TypeScript 7.0 Beta公開、Go移植コンパイラで10倍高速化

ソース：[JA · Publickey]
リンク：<https://www.publickey1.jp/blog/26/typescript_70typescriptgo10.html>

Microsoftが昨年予告したTSコンパイラのGo移植が、いよいよ7.0 Betaとして公開。数百万行クラスのコードベースで10倍の高速化が報告されています。日本のフロントエンドの大規模 monorepo 運用チーム——特にCIビルド時間が15分超えに苦しんでいるところ——にとっては、明確な投資対象です。5.x系はメンテナンスモードに入る見通し。

## 8. Claude Opus 4.7 リリース

ソース：[EN · Anthropic]
リンク：<https://www.anthropic.com/news/claude-opus-4-7>

5月4日、AnthropicがOpus 4.7を発表。最大の変更点は視覚能力で、より高解像度の画像を扱えるようになりました。スクリーンショットを使ったデバッグやUI自動化エージェントの精度向上が期待されます。価格は4.6と同じ（input $5/M、output $25/M）。SpaceXとの計算リソース提携も同時発表されています。

## 9. DeepSeek V4 Pro、5月31日まで75% OFF

ソース：[EN · HN]
リンク：<https://api-docs.deepseek.com/quick_start/pricing>

DeepSeekが期間限定で全料金を1/4に。日本の中堅SaaSでLLMコストが営業利益を圧迫しているケースは少なくないので、long-context系のユースケースを中心にA/Bを取るには良い窓口です。Claude/GPT系との出力品質差は用途次第ですが、コスト差は大きく、5月末までに比較データを取る価値があります。

## 10. Google Cloud Fraud Defense：reCAPTCHAの次世代

ソース：[EN · HN]
リンク：<https://cloud.google.com/blog/products/identity-security/introducing-google-cloud-fraud-defense-the-next-evolution-of-recaptcha/>

reCAPTCHAは行動シグナル＋AIによる「不正対策プラットフォーム」へと進化。チェックボックス型のbot対策ウィジェットの時代の終わりを示唆しています。日本の決済・EC事業者にとって、PayPay的な不正検知ベンダーとの比較対象として実装評価する価値があります。UXの観点でもreCAPTCHA v2/v3の摩擦が減ることが期待されます。

---

## 編集後記

今日の裏テーマは「コードを書くスピードはもうボトルネックではない」で、Simon Willisonの記事 (#1) と「The bottleneck was never the code」(#2) の組み合わせがマストリードです。日本企業の実務に直結する2本としては、AWS UAE リージョン障害 (#6) とTypeScript 7.0 Beta (#7) が今週中にチームと共有しておきたい話題。残りはAI各社の値下げと能力アップ競争の継続報告です。
