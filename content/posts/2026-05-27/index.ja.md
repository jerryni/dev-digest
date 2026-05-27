---
title: "5月27日 · 今日のテック厳選10本"
date: 2026-05-27T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "ブラウザフィンガープリント", "サプライチェーン", "ai-agent", "web標準", "コーディングツール", "原発", "プライバシー"]
categories: ["daily"]
summary: >-
  LinkedIn が 6,278 個の拡張機能を毎リクエストで暗号化して送信していることが判明。Mozilla が Chrome の Prompt API に対して「harmful」の標準ポジションを出しました。PyTorch Lightning に Shai-Hulud 系のサプライチェーン攻撃が侵入。Docker は CLI 内蔵 AI エージェント「Gordon」を GA。.NET MAUI がついに Mono ランタイムを脱却して CoreCLR へ。ベルギーが AI データセンター需要を理由に原発の廃炉中止を表明。Rivian は本物の「全通信オフ」スイッチを実装。Armin Ronacher が LLM で書き直された GitHub Issue に苦言。今日のテーマは「信頼境界の引き直し」。
---

## 本日のサマリー

今日の 10 本は問いがほぼ揃っています。**2026 年において、どの層に信頼境界を引き直すのか。** LinkedIn が毎リクエストで「あなたがインストールしている拡張機能 6,278 個」を暗号化して送っていた件は、ブラウザ側のフィンガープリントを再び敵対的問題として扱う必要があることを示しました。Mozilla が Chrome の `window.ai.languageModel` に対して出した「harmful」声明は、近年で最も強い標準ポジションのひとつで、Web プラットフォームに LLM を組み込むこと自体への原理的な反対です。PyTorch Lightning の供给链汚染は、もはや AI トレーニングの依存ツリーが攻撃者にとって「メインルート」になっていることを意味します。ツール領域では Docker が CLI 内 AI エージェント「Gordon」を GA、同じ週に Cursor は実質的な制限強化、Rivian は車両の完全通信遮断スイッチを実装、ベルギーは原発廃炉の撤回。日本企業の運用者にも示唆が多い一日です。

## 1. LinkedIn が 6,278 個のブラウザ拡張を毎リクエストでスキャン

[LinkedIn scans for 6,278 extensions and encrypts the results into every request](https://news.ycombinator.com/item?id=47967262) · `404privacy.com / HN 299`

404privacy が LinkedIn の Web クライアントを解析した結果、ハードコードされた 6,278 個の拡張機能 ID に対して `web_accessible_resources` 経由で存在チェックを行い、ビットマップを暗号化して毎リクエストに付与していることが判明しました。ここでの暗号化は E2E ではなく、拡張機能側でのブロックを回避するための難読化です。本質は「監視」よりも「インストール済み拡張機能まで指紋に組み込まれる時代に入った」という点。社内で拡張機能の許可リストを運用している情シスにとっては、社員の LinkedIn セッション経由で組織のフィンガープリントが漏れる可能性がある、ということになります。日本企業の SaaS 利用ポリシーにも影響が出るはずです。

## 2. Mozilla が Chrome の Prompt API に「harmful」ポジション

[Mozilla's opposition to Chrome's Prompt API](https://github.com/mozilla/standards-positions/issues/1213#issuecomment-4347988313) · `github.com/mozilla / HN 564`

Mozilla の standards-positions リポジトリに、Chrome の `window.ai.languageModel` 提案を「harmful」と分類するエントリが追加されました。主旨は明快で、「ブラウザ内蔵 LLM API は仕様化できない」というもの。出力が決定的でもバージョン化可能でもないため、Web の「一度書けばどこでも動く」契約を壊す、と主張しています。スレッドには Apple の WebKit チームも静かに同意を寄せています。今 Chrome の Prompt API で機能をリリースするなら、「これは長期にわたって Chrome 専用機能になる」前提で設計しておくのが現実的です。

## 3. PyTorch Lightning に Shai-Hulud 系マルウェア混入

[Shai-Hulud themed malware found in the PyTorch Lightning AI training library](https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/) · `semgrep.dev / HN 299`

Semgrep のリサーチチームが PyTorch Lightning の間接依存に注入された悪意あるパッケージを検出。先期に npm を席巻した "Shai-Hulud" シリーズの系譜です。ペイロードは HuggingFace トークン、AWS キー、Wandb セッションを狙うもの。トレーニングパイプラインが握る資格情報の組み合わせとピッタリ合います。2020 年に CI/CD ビルドシステムが攻撃の本命だったのと同じ位置に、いまや AI 学習リポジトリが立っています。社内でモデル学習を CI に組み込んでいるチームは、本番デプロイと同レベルの警戒度をトレーニング側のサプライチェーンにも適用すべきです。

## 4. Docker 専用 AI エージェント「Gordon」が正式リリース

[Docker専用のAIエージェント「Gordon」が正式リリース](https://www.publickey1.jp/blog/26/dockeraigordondocker.html) · `Publickey`

Docker が Gordon を GA に昇格させ、Docker CLI に直接組み込まれました。`docker ai` で Dockerfile を読み、ビルドエラーを解説し、修正案を提示・適用までやってくれます。無料アカウントの枠も日常利用には十分。注目点は IDE 層での Claude Code / Antigravity との競合ではなく、「特定ツールの CLI に AI が組み込まれる」というパターンを Docker が早めに張ったこと。今後 2 四半期で kubectl、terraform、gh も似た形で AI エージェントを内蔵してくるはずです。日本企業の現場でも `docker ai` ベースのオンボーディングが現実的な選択肢になります。

## 5. .NET MAUI がついに Mono ランタイムを脱却

[ついにMonoランタイムを脱却する「.NET MAUI」](https://www.publickey1.jp/blog/26/mononet_mauinet_mauimonocoreclr.html) · `Publickey`

次期 .NET MAUI で、モバイルとデスクトップ両方が Xamarin 時代から続く Mono ランタイムから CoreCLR へ完全移行することが確定。Xamarin 買収以降ずっと続いてきた移行作業の完了です。実務面の影響は明確で、iOS の AOT パフォーマンスが大きく改善、GC 挙動がサーバ側 .NET と統一、Mono 特有のジェネリックインタフェースディスパッチの癖が消えます。Xamarin.Forms から離れる踏ん切りがつかなかったチームには、ランタイムが揃った今が動き時です。

## 6. Cursor が 500 リクエスト枠を実質的に絞り始めた

[Cursor 对 500 次用户出手了吗，最近可用的旧版本是多少](https://www.v2ex.com/t/1215208) · `V2EX`

中国の開発者コミュニティ V2EX で、Cursor の $20 Pro プランの「500 fast requests」が新バージョンで実質的に縮小されていると複数のユーザーが報告。以前は fast 扱いだったリクエストが新バージョンでは slow に分類されるケースが増えているとのこと。スレッドは「どの旧バージョンならまだ広告通りに動くか」の情報交換の場になっています。先週の Claude Code 「OpenClaw」事件と合わせて読むと明確で、AI コーディングツールはもう「レート制限は将来の問題」の段階を抜け、グレーな運用強化のフェーズに入っています。日本のチームでも「バージョン固定」が日常運用の選択肢に上がります。

## 7. 「会社が AI 代を出してくれない、どれを使う？」

[公司不给钱我该用哪个 AI 码代码？](https://www.v2ex.com/t/1215305) · `V2EX`

V2EX で、自費 / 無料枠の AI コーディングツールを実利目線で比較するスレッドが盛り上がりました。実際に選ばれている顔ぶれは、Alibaba Cloud の無料枠の Qwen3-Coder、Google AI Studio 経由の Gemini、ローカル 4090 でのオープンウェイトモデル。逆に明確に外されていたのは Claude（個人課金が高すぎる）、Cursor（項目 6 参照）、Copilot（企業アカウント前提）。日本のフリーランスや個人開発者にもそのまま参考になる現場感です。

## 8. ベルギーが原発の廃炉を中止

[Belgium stops decommissioning nuclear power plants](https://news.ycombinator.com/item?id=47961319) · `dpa-international / HN 712`

ベルギー連邦政府が、これまで進めてきた原発廃炉計画を正式に停止し、現行炉の運転寿命を 2035 年以降へ延長する法案を準備中。理由は AI とクラウドの電力需要が 2022 年時点のあらゆる予測を上回ったため。ベルギーは特殊例ではなく、ドイツ・オランダ・スウェーデンでも同じ議論が進行中ですが、廃炉スケジュールを実際に撤回した最初の EU 加盟国になります。先週の HBM ウェハー配分の話と並べて読むと、AI インフラのコストは NVIDIA の利益だけでなく、物理世界の各レイヤーが負担している構図が見えてきます。日本の電力政策にも遠からず波及するテーマです。

## 9. Rivian が車両の通信を完全に切るスイッチを実装

[Rivian allows you to disable all internet connectivity](https://rivian.com/support/article/can-i-disable-all-data-collection-from-my-vehicle) · `rivian.com / HN 331`

EV メーカーの Rivian が、車両の全外向き通信（OTA、フリート遥測、リモート診断）を一括で無効化する設定を追加。プラン別ではなく全車両対応、アップセルなし。コネクテッドカーをひたすら推し進める他メーカーの方針とは正反対で、HN スレッドでは実際に全通信が止まっているかをパケットキャプチャで検証する動きが続いています。日本車メーカーにとっても比較対照として参照されるはず。「ここまではユーザーの選択でオフにできる」という業界の下限が見えた格好です。

## 10. Armin Ronacher が「LLM で書き直された Issue」に苦言

[Armin Ronacher: condensed issue reports beat AI-rewritten ones](https://lucumr.pocoo.org/2026/5/24/pi-oss/) · `lucumr.pocoo.org / Simon Willison`

Flask 作者の Armin Ronacher が、自身が新しく公開した Pi ランタイムに対して届く「明らかに LLM で書き直された Issue」の問題点を整理しました。AI が要約した Issue は過剰に自信ありげで、最小再現コードを捏造し、本当に重要な 4 点（実行したコマンド、期待結果、実際の挙動、エラーログ原文）をぼかしてしまう、と。OSS メンテナのテンプレートに「この 4 点だけ書いて」と入れておくのは、AI ツール時代の運用としてかなり現実的な落とし所です。誠実なバグ報告は 4 行で済む、というのが結論。

## 編集後記

今日の通底テーマは **「信頼境界の引き直し」**。LinkedIn は拡張機能リストをフィンガープリントに取り込み、Mozilla はブラウザ内 LLM API を Web 標準の侵食と位置付け、PyTorch Lightning は AI 学習の上流にあるがゆえに狙われ、Cursor は「fast リクエスト」の定義を変え、AI エージェントは個別ツールの CLI に降りてきて（Docker Gordon）、Armin Ronacher は人間同士のコミュニケーションに AI を挟むことに線を引きました。レイヤーごとに「誰が見て、誰が決めて、誰が誰の代わりに話すか」が再交渉されています。今日読むなら 2 本、まず **項目 2（Mozilla vs Prompt API）** で「なぜ Web プラットフォームは LLM を綺麗には飲み込めないか」を押さえ、次に **項目 10（Ronacher の slop issue 論）** で同じ問いの人間プロセス版を読むのがおすすめです。
