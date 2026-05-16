---
title: "5月17日 · 今日のテック厳選10本"
date: 2026-05-17T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Anthropic", "Claude", "セキュリティ", "VSCode"]
categories: ["daily"]
summary: "LinkedInのブラウザ拡張スキャン、PyTorch Lightningのサプライチェーン汚染、Anthropicとゲイツ財団の2億ドル提携。週末明けの情報量は多めです。"
---

## 本日のサマリー

週末を挟んで一気に話題が積み上がりました。セキュリティ系はLinkedInが拡張IDを暗号化してサーバへ送っていた件と、PyTorch Lightningへの「Shai-Hulud」テーマのサプライチェーン攻撃。AI企業の動きとしてはAnthropicがゲイツ財団と2億ドル規模の提携を発表し、同時にClaude for Small Businessも投入。日本側ではVS Code 1.120で複数AIエージェントを並走させるAgent windowが入り、Zennでは「Claude CodeからCodexへ移行する前に知っておきたかったこと」が読まれています。今日は「AIをどう仕事に組み込むか」と「組み込んだ後どう守るか」が同時進行のテーマです。

## 今日の10本

### 1. LinkedInが6,278個のブラウザ拡張を裏でスキャンしていた（HN · EN）

[原文：404privacy.com](https://404privacy.com/blog/linkedin-is-scanning-your-browser-extensions-this-is-how-they-use-the-data/) · [HNスレッド](https://news.ycombinator.com/item?id=47967262)

LinkedInが全リクエストに暗号化ペイロードを忍ばせ、6,278個の拡張機能IDをフィンガープリントしていたという調査記事。プライバシー寄りの拡張を入れているとアカウントが妙に渋い扱いを受ける現象も、これで一定の説明がつきそうです。Webスクレイピングや業務効率化ツールを社内配布している会社は、社員のLinkedIn接続体験への副作用も意識した方がよさそうです。

### 2. PyTorch LightningにShai-Hulud風サプライチェーン攻撃（HN · EN）

[Semgrep分析](https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/) · [HNスレッド](https://news.ycombinator.com/item?id=47964617)

昨年npmで暴れた「Shai-Hulud」ワームと同系統の手口がAI学習スタックに到達。Lightningの依存経由でトレーニング環境に侵入し、GPU基盤のサービスアカウントを横展開する想定です。`pip install`してそのまま長時間学習を回す現場が多い分、被害規模が一般的なWeb案件より大きくなりやすい構図です。lockfile固定とCIの短命クレデンシャル化が、今日からの宿題と言えます。

### 3. プログラミング言語はもうロックインではない（Simon Willison · EN）

[原文：Not so locked in any more](https://simonwillison.net/2026/May/14/not-so-locked-in/)

BunがZigからRustへ書き直された話と、ある中規模企業がコーディングエージェントでiOS/Androidネイティブアプリを数週間でReact Nativeに置き換えた話を、Simonが「言語選定はもう"10年単位の意思決定"ではない」と総括。日本の現場でよくある「Kotlinに揃えるかFlutterに行くか」議論にも、まったく別角度の選択肢が生まれてきています。

### 4. Infraエンジニアによる週200ドルCodex消費レポート（V2EX · ZH）

[V2EXスレッド](https://www.v2ex.com/t/1213114)

中国語圏のV2EXで盛り上がっている、Infra開発者の1週間のCodex実費レポート。「どの作業はAgentに任せるとペイし、どこは手で書いた方が早いか」のリアルな線引きが詰まっています。日本企業でClaude Code / Codexの法人プランを検討中のチームには、ベンダー資料より参考になる外部データとして読めます。

### 5. 「AI Codingで、プログラマーへの愛情を失ってきている」（V2EX · ZH）

[V2EXスレッド](https://www.v2ex.com/t/1213164)

中国語圏で同じ日に伸びている「コードを自分で書かなくなって職人としての満足感が薄れた」という投稿。技術論ではなくアイデンティティの話で、Zennでも似た論調の記事が複数浮上しています。日本の現場でも、評価面談やキャリア設計でこの揺らぎをどう扱うかは近いうちに必ず議題になるはずです。

### 6. Claude Code派だった僕がCodexに移る前に知りたかったこと（Zenn · JA）

[Zenn原文](https://zenn.dev/gemcook/articles/e56eabc7ba2961)

Gemcookのエンジニアによる移行記。サブエージェントの粒度、コンテキスト管理の癖、料金体系の違いまでが具体的に並んでいます。両方を業務で触ったことがある立場からの記事なので、社内の「どっち入れる？」議論で配布資料として強い一本です。

### 7. VS Code 1.120、複数AIエージェント開発を支える「Agent window」プレビュー（Publickey · JA）

[Publickey原文](https://www.publickey1.jp/blog/26/vs_codeaiagent_window.html)

VS Codeが「複数Agentを別ウィンドウで同時稼働させる」という発想を本体に取り込みました。CursorやCodexデスクトップが先行していた領域に、エディタ側からの正面回答という形です。チームでAgent運用ルールをどう揃えるか、`.vscode/agents.json`のような共通設定がそろそろ現実的な課題になります。

### 8. Anthropic、ゲイツ財団と2億ドル規模で提携（Anthropic公式）

[Anthropic公式発表](https://www.anthropic.com/news/gates-foundation-partnership)

グローバルヘルス・農業・教育の3領域で、財団のパートナー網にClaudeを供給するという提携。日本のNPOや自治体DXに関心がある人にとっては、「非商用AI活用」をフロンティアラボがどう本気で制度化していくかの参考事例になります。

### 9. Anthropic、Claude for Small Businessを発表（Anthropic公式）

[Anthropic公式発表](https://www.anthropic.com/news/claude-for-small-business)

5〜50人規模を狙った独立SKU。これまでProとTeamの間に空いていた価格・機能の谷を埋める形で、日本の中小SaaSや士業オフィスにも刺さりそうな構成です。Microsoft 365 / Google Workspaceとどう並べるかの議論が、いよいよ「組合せ前提」の時代に入った感があります。

### 10. MozillaがChromeのPrompt APIに反対表明（HN · EN）

[Mozilla standards-positions issue](https://github.com/mozilla/standards-positions/issues/1213) · [HNスレッド](https://news.ycombinator.com/item?id=47959463)

ChromeがブラウザにLLMを組み込んでJSから呼べるようにする「Prompt API」を標準化しようとしているのに対し、Mozillaが明確に反対の立場を表明。「モデル重みを暗黙の前提とするWeb APIは、Webプラットフォームの中立性を壊す」という論点で、Webフロントエンドの今後数年に効いてくる議論です。

## 編集後記

今日の裏テーマは「AIサプライチェーンの守り」と「Agentが業務インフラへ昇格していく速度」の同時進行。必読は2本。**第2項のShai-Hulud風攻撃**は、AIチームが日常的にやっている`pip install`の脆さを正面から突いています。そして**第10項のMozilla反対声明**は、AIをブラウザ既定機能にしてよいかという、Webプラットフォーム史に残るレベルの分岐点です。

データソース備考：GitHub Trendingは本日HTML取得が安定せず、本号では集計対象外としました。他6ソースは正常に取得できています。
