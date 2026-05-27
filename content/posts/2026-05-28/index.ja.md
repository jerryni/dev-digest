---
title: "5月28日 · 今日のテック厳選10本"
date: 2026-05-28T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "cloudflare", "llm", "code-agent", "qwen", "dotnet-maui", "vscode", "anthropic", "xai"]
categories: ["daily"]
summary: >-
  Cloudflare が社内 SRE ツールをそのまま商用化した「Flagship」を発表、Datadog と真正面から競合する構図に。next-token prediction の限界をきれいに言語化したブログが HN で議論を呼んでいます。ZIRP 時代の「Noと言えるエンジニア」像が成り立たなくなった理由を冷静に書いた記事も。中国コミュニティでは Qwen3.7 と GLM5.1 のコーディング能力比較、そして国産 code agent の実用性が真剣に議論中。Publickey からは .NET MAUI が Mono から CoreCLR へ移行、VS Code が「Agent window」プレビュー公開。ワイルドカードは Anthropic の Project Glasswing 初報告、Gemini 3.5 Flash の GA、xAI Grok Build のベータ公開。
---

## 本日のサマリー

今日の縦糸は **「agent はもはや単なるチャット欄ではない」** という流れです。VS Code の Agent window、xAI Grok Build の並列 sub-agent、V2EX で議論されている国産 code agent — どれも 2026 年下期に「IDE = 編集環境 + 複数 AI ワーカー」が標準になることを示しています。日本の現場視点で気になる横糸は二つ。一つは Cloudflare Flagship が国内 SRE 文化（特にメルカリ・LINE・サイバーエージェント系の大型 Datadog 利用）に与える価格圧力。もう一つは .NET MAUI の CoreCLR 移行で、Xamarin 時代から残る業務系モバイルアプリの「いつ書き直すか」議論が再燃するはずです。

## 1. Cloudflare、社内 SRE ツールを商用化した「Flagship」を発表

[Cloudflare Flagship](https://developers.cloudflare.com/flagship/) · `HN 199`

Cloudflare が長年自社で使ってきたインシデント管理・可観測性・ランブック自動化ツールをそのまま商品化、名前は Flagship。立ち位置は明らかに Datadog / PagerDuty の領域です。説得力の源は「世界トラフィックの 20% を支えている当社自身が毎日使っている」というシンプルな事実。日本の SRE 界隈で気にすべきは、Cloudflare Workers 既導入の会社にとって乗り換え障壁が極めて低いこと。Datadog 契約更新時期の Engineering Manager は、コスト比較表に必ず Flagship を入れておいた方が良いでしょう。

## 2. next-token prediction の到達点はどこか

[Where does next-token prediction leave us?](https://pop.rdi.sh/where-does-next-token-prediction-leave-us/) · `HN 175`

純粋な next-token prediction だけで進めるアプローチが、2026 年時点でどこまで届くかを冷静に分解したブログ記事。著者は scaling law が一部の次元では依然有効としつつ、long-horizon planning / tool use / self-verification については「10倍にしても解けない」と複数の実例で示します。業界が agent + RL post-training に全面シフトしている現状の「なぜ」を綺麗に説明していて、社内の LLM 戦略ドキュメントに引用しやすい一本です。

## 3. 「Noと言えるエンジニア」は ZIRP 時代の副産物だった

[The just-say-no engineer was a ZIRP phenomenon](https://www.seangoedecke.com/the-just-say-no-engineer-was-a-zirp-phenomenon/) · `HN 130`

「PM の無理な要求を断れるエンジニア像」は、2015〜2022 のゼロ金利・人材不足期間の副産物だった、という辛口の主張。資本コストが上がれば、企業が許容するのは「まずやってから文句を言う」タイプであって、断れる人ではない、と。日本のソフトウェア業界はもともと「断れる」文化が薄めなのでピンと来ない読者もいるはずですが、外資系・スタートアップで働く中堅エンジニアには刺さる内容です。エンジニアリングマネージャー視点でも、評価軸を見直すきっかけになります。

## 4. 中国コミュニティ：国産 Code Agent は本当に Cursor に対抗できるのか

[国産 Code Agent はちゃんと動くものがあるのか？](https://www.v2ex.com/t/1215881) · `V2EX 41`

V2EX で議論されている話題。投稿者は「Cursor / Claude Code 以外に、中国製で実用に堪える code agent はあるか？」と問いかけ。コメントで頻出するのは ByteDance の MarsCode、Zhipu GLM 系、Alibaba 通義灵碼、DeepSeek R2 派生ツール。コンセンサスは「補完なら追いついた、ただし複数ファイルのリファクタリング＋長コンテキスト計画実行はまだ差がある」。日本企業で中国オフショア利用がある場合、相手側エンジニアがどのツールを実務で使っているかを把握しておくと、コードレビューの観点が変わります。

## 5. Qwen3.7 のコーディング性能、本当に GLM5.1 を抜いたのか

[Qwen3.7 がコーディングランキングで GLM5.1 を抜いたが、使った人いる？](https://www.v2ex.com/t/1215786) · `V2EX 28`

LiveCodeBench と SWE-Bench Verified では確かに Qwen3.7-Coder が GLM5.1 を上回っているものの、実際に使った V2EX ユーザーからは不一致な感想が出ています。React/TypeScript プロジェクトでは Qwen の方が「文脈を理解する」、Java の大規模コードベースでは GLM の方が安定、といった具合。ベンチマーク drift が常態化した 2026 年、中国の開発者は「複数モデルをタスク別に使い分ける」習慣が既に定着しています。日本の Devin / Cursor 一本足の組織は、この使い分け文化を参考にした方が良いかもしれません。

## 6. .NET MAUI、Mono から CoreCLR へランタイム移行

[.NET MAUI、ランタイムを Mono から CoreCLR へ](https://www.publickey1.jp/) · `Publickey`

クロスプラットフォーム .NET の歴史的負債である Mono ランタイムを、ついに CoreCLR で完全置き換えする計画が発表されました。これにより MAUI 上のアプリも ASP.NET Core と同じ GC / JIT 最適化を享受でき、起動時間とメモリ使用量が顕著に改善する見込みです。Xamarin 時代から続く業務系モバイル案件を抱える SIer にとっては大きな朗報。ただし iOS 側の AOT 部分は互換性テストを一通りやり直す必要があり、移行プロジェクト計画には織り込むべきです。

## 7. VS Code、複数 AI を同時に動かす「Agent window」プレビュー公開

[Visual Studio Code 「Agent window」 プレビュー版を公開](https://www.publickey1.jp/) · `Publickey`

VS Code の May 2026 リリースに、Agent window という新しいウィンドウタイプが追加されました。複数の AI agent を別タスクで同時に走らせられる仕組みで、たとえば Claude Code にバックエンドを書かせつつ Copilot にテストを走らせる、といった使い方が可能。これまでは複数拡張を組み合わせて無理やり実現していたものが、ネイティブ対応になりました。日本企業で VS Code Server を用いたリモート開発をしている組織は、SSH セッション越しの挙動を一度検証することをお勧めします。

## 8. Anthropic、Project Glasswing 連合の初報告を公開

[Project Glasswing: An initial update](https://www.anthropic.com/research/glasswing-initial-update) · `Anthropic`

4月発足の Project Glasswing（AWS・Anthropic・Apple・Cisco・CrowdStrike・Google・JPMorgan・Linux Foundation・Microsoft・NVIDIA・Palo Alto Networks の連合）が初の成果物を公開しました。内容は critical software に対する攻撃面モデリングのホワイトペーパー数本と、AI トレーニングパイプラインのサプライチェーン脆弱性データベース。日本の SBOM / OSS 管理ツールベンダー（特に NRI セキュア、サイバートラストなど）は、データソースとしての価値を含めて要観察です。

## 9. Google、Gemini 3.5 Flash を preview 抜きで GA

[Gemini 3.5 Flash, generally available](https://simonwillison.net/) · `Simon Willison`

Google I/O で発表された Gemini 3.5 Flash は preview フェーズなしで GA。Simon Willison の実測レビューによれば、ツール呼び出しシナリオでの context window が 2.5 系列より安定し、TTFT が 200ms 以下に短縮。voice agent 系プロダクトには質的変化です。価格も同等クラスの Sonnet より一段下で、mid-tier ユースケースの API コストは下げ圧力。Vertex AI 経由で使う場合、東京リージョンの可用性を確認の上で本番投入を。

## 10. xAI、並列 sub-agent 対応の「Grok Build」をベータ公開

[xAI のコーディング AI 「Grok Build」 ベータ版を公開](https://www.publickey1.jp/) · `Publickey / xAI`

xAI の coding agent「Grok Build」がベータに入り、最大の特徴は **並列 sub-agent**。メイン agent が複数の子 agent を fork して独立タスクを走らせ、結果を合流させる仕組みで、子 agent 同士は git worktree で隔離されます。Claude Code の subagent モデルと方向性は同じですが「ロックなし並列」を強調。短期的に Claude / Cursor のシェアを奪うかは未知数ですが、「sub-agent はもはやオプションではなく標準」という認識は業界で固まったと言えます。

## 編集後記

本日のメタテーマは **「agent はチャット欄を卒業した」** です。VS Code の Agent window、Grok Build の並列 sub-agent、V2EX で議論される国産 code agent は、いずれも「IDE = エディタ + 複数 AI ワーカー」という近未来を指しています。今日のマストリードは **2 番 next-token prediction の限界** と **3 番 ZIRP エンジニア論**。前者は agent への移行が必然である「技術的理由」を、後者は組織が agent を受け入れざるを得ない「経済的理由」を、それぞれ説明しています。
