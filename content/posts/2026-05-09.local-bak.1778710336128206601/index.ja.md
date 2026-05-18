---
title: "5月9日 · 今日のテック厳選10本"
date: 2026-05-09T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Claude", "Bun", "AWS", "プライバシー", "Anthropic"]
categories: ["daily"]
summary: "Google が de-googled Android で reCAPTCHA を壊す。『AWS に戻ったらまた離れた理由を思い出した』が HN で 732 点。Bun の Rust 移植がテスト互換 99.8%。Timothy Gowers が ChatGPT 5.5 Pro で本物の研究数学を試した。EU が VPN を『塞ぐべき抜け穴』と呼ぶ。"
---

## 本日のサマリー

今日の通底テーマは「プラットフォーム権力が締まる」。Google は Android 側で、EU は VPN 側で、Meta は Instagram DM 側で、それぞれ自由度を引き下げに来ています。その合間に「AWS から離れたのに戻された運用エンジニア」のポストモーテムが大バズ。3 本だけ読むなら 1・4・7。

---

## 1. Google、de-googled Android で reCAPTCHA を壊す

タグ：[EN · HN Top]
リンク：<https://reclaimthenet.org/google-broke-recaptcha-for-de-googled-android-users>

HN 1520 点。reCAPTCHA のチャレンジ判定アップデートにより、CalyxOS や GrapheneOS などの脱 Google 系 Android がほぼ全件「不審なトラフィック」扱いに。多くのサイトで解けないパズルが延々出る挙動です。意図は明示されていませんが、結果として「Google Mobile Services なしで公開 Web を快適に使う」コストが一段上がりました。本日の項目 7（EU の VPN 規制）と合わせて読むと、今四半期「Google モバイル生態系から出ていく」ことのコストが、一枚ずつブロックを積み上げる形で確実に上がっている構図が見えます。

## 2. 「AWS に戻ったら、また離れたかった理由を思い出した」

タグ：[EN · HN Top]
リンク：<http://fourlightyears.blogspot.com/2026/05/i-returned-to-aws-and-was-reminded-hard.html>

HN 732 点。著者は AWS から小規模クラウドへ移ったあと、エンタープライズ顧客の都合で AWS に戻され、今週いちばん引用されているオペレーション・ポストモーテムを書きました。具体的な不満：IAM が複雑すぎて参入障壁化、コンソールと API の挙動ドリフト、マルチアカウント組織の認知負荷、そして「請求最適化」が独立した職務になっていること。論旨は「AWS はダメ」ではなく「AWS で動かすときの 1 エンジニアあたりの認知コストは構造的なもので、スキルでは消せない」。これは移行判断で誰もコストに計上しないやつです。

## 3. Bun の Rust 移植、テスト互換 99.8% に到達

タグ：[EN · HN Top]
リンク：<https://twitter.com/jarredsumner/status/2053047748191232310>

HN 691 点。Jarred Sumner が、Bun の Zig→Rust 移植が Linux x64 glibc で既存テストスイートの 99.8% を通過したと投稿。予想よりかなり早いペースです。HN の議論は「なぜ移すか」が中心：コントリビューター獲得のしやすさ、システムプログラミング向けの標準ライブラリの厚み、ツールチェインの成熟。構造的に面白いのは、これが今のところ最も注目度の高い Zig→Rust 移行であり、「コントリビューター集まらない壁」にぶつかった新言語プロジェクトに先例を作りつつあること。

## 4. Timothy Gowers、ChatGPT 5.5 Pro で本物の数学に挑む

タグ：[EN · HN Top]
リンク：<https://gowers.wordpress.com/2026/05/08/a-recent-experience-with-chatgpt-5-5-pro/>

HN 689 点。フィールズ賞受賞者ティモシー・ゴワーズ氏が、ChatGPT 5.5 Pro を研究レベルの数学に対して使った体験を丁寧に書き起こしています。どこで本当に役に立ったか、どこでもっともらしく間違ったか、証明スケッチを自分で外科的に修正する必要があったか、まで具体的に。要点は「もう真剣な数学者にとっておもちゃではない、ただし『検証作業』は依然として人間の仕事」。今月見るなかで「AI は頭打ちした」という主張に対する最も強い反証です。

## 5. Simon Willison：音声 AI にとって WebRTC は問題そのもの

タグ：[EN · Simon Willison]
リンク：<https://simonwillison.net/2026/May/9/luke-curley/>

Simon が Luke Curley の記事を引用。論旨は「WebRTC は LLM 音声インターフェースに構造的に向いていない」。WebRTC はリアルタイム性のために音声パケットを積極的にドロップしますが、これは Zoom 通話には合理的でも、生成型応答では完全に逆方向です（200ms 余分に待ってでも壊れていないプロンプトが欲しい）。Curley の追い打ち：「ブラウザ内では WebRTC オーディオパケットの再送信が事実上できない」——OpenAI の音声 AI プレスリリースには絶対に出てこない種類のプラミング詳細。

## 6. Claude Code：HTML 出力フォーマットは過小評価されている

タグ：[EN · HN]
リンク：<https://twitter.com/trq212/status/2052809885763747935>

HN 513 点。Claude Code チームの Thariq Shihipar 氏が、解説系タスクでは Claude に Markdown ではなく HTML を出させるべきだと主張。コスト（追加トークン）は GPT-4 時代には重要でしたが、100 万トークン文脈の時代には事実上無視できます。利益（SVG 図、色分け注釈、インタラクティブウィジェットの埋め込み）は大きい。GPT-4 時代から「Markdown で答えて」をデフォにしてきた人は、計算を組み直す時期です。

## 7. 欧州議会調査局：VPN は「塞ぐべき抜け穴」

タグ：[EN · HN Top]
リンク：<https://cyberinsider.com/eu-calls-vpns-a-loophole-that-needs-closing-in-age-verification-push/>

HN 635 点。欧州議会調査局が委託した報告書が、消費者向け VPN を EU の年齢認証制度に対する障害と位置づけ、規制介入を推奨。手段はまだ曖昧（プロバイダ登録制、強制ログ、下流プラットフォームへの義務付け）ですが、フレーミングそのものが重要：「抜け穴」という言葉で、プライバシーツールが「治理対象」に再定義されました。立法に至らなくても、「ネット上の匿名はどこまで正当か」という Overton 窓口が確実に狭まっています。

## 8. V2EX：AI はあらゆる層で「ものの価値」を希釈している

タグ：[ZH · V2EX]
リンク：<https://www.v2ex.com/t/1211027>

短いスレですが論点が刺さります。LLM 以前の「作者が手間をかけたサイン」——きれいな README、100 コミットある GitHub リポジトリ、構造の整ったブログ、丁寧な PR 説明——いずれも数分で量産可能になり、シグナルとして機能しなくなった、という観察。本日項目 4 と並べて読むと立体的になります：Gowers のポストは AI がバリューチェーンを上りつつある側、V2EX のスレは同じ動きを下から見たときの風景。

## 9. Zenn：AI エージェント時代の DB 設計、Turso が書き換えに来ている

タグ：[JA · Zenn]
リンク：<https://zenn.dev/emuni/articles/6eef9f97f564b4>

Zenn で 85 いいね。エムニ社のエンジニアの論点：「短命のエージェントが各々個別の DB を持つ」というワークロードは、Turso の『数百万個の安価な SQLite インスタンス』モデルが想定していた対象そのもの。コスト試算（Turso: エージェントごと DB が月数セント、Postgres のテナントごとだと月数ドル）も具体的に出ています。マルチテナント前提のエージェントシステムを設計するなら、現状の Postgres-per-tenant 案と並べて評価する価値あり。

## 10. u32 を渡したら root が返ってきた：io_uring ZCRX freelist LPE

タグ：[EN · HN]
リンク：<https://ze3tar.github.io/post-zcrx.html>

HN 213 点。Linux の io_uring ゼロコピー受信パスにおける新しいローカル権限昇格。非特権ユーザが攻撃者制御の u32 一つから freelist 管理バグを引き起こせる、というもの。利用チェーン全体が教科書級に丁寧に書かれています。io_uring のセキュリティ track record は引き続き運用側に悪夢を提供しており、ホットパスの性能と引き換えに値するのかどうかは今も議論余地あり。ハードニングされたマルチテナント Linux 群を運用しているなら、今日中にパッチを。

---

## 編集後記

今日の通底テーマは「プラットフォーム権力が締まる」——Google が Android で、EU が VPN で、Meta が Instagram E2EE で、それぞれ自由度を引き下げに来ています。その合間に AWS から逃げ切れない郷愁の一篇。項目 1 と 7 は規制ライン、項目 3 と 4 は技術進歩ライン。マルチクラウド判断が目の前にあるなら項目 2、AI が頭打ちした派なら項目 4——ゴワーズの記事は今月いちばん重い反証です。
