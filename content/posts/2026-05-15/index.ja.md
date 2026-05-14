---
title: "5月15日 · 今日のテック厳選10本"
date: 2026-05-15T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "Claude", "VSCode", "Bun", "Node.js", "Mojo", "Nginx", "Skills", "セキュリティ"]
categories: ["daily"]
summary: "今日の流れは大きく3本。1つ目はインフラ側の世代交代──VS Code 1.108 が複数の AI エージェントを並列に走らせる「Agent window」をプレビュー公開、Bun の Rust 書き直し PR が main にマージ、Node.js 26 で Temporal がデフォルト有効化、Mojo 1.0 が Beta 到達。2つ目はセキュリティ／プライバシー方面の揺り戻し──HN 1位は RAV4 hybrid から DCM と GPS を物理的に抜く DIY 記事、2位は Nginx の新しいスタックオーバーフロー PoC、そして V2EX では「会社で買った LLM の API キーを同僚がこっそり横流ししていた」というやや生々しい話題。3つ目は AI エージェント運用の現場知見──Zenn では同じ Skills を使って Claude Code と Codex にオセロを対局させた 56-8 のレポートが大量にスター、GitHub Trending の obra/superpowers が Skills フレームワークとして急上昇。"
---

## 本日のサマリー

「AI が便利になる話」から「AI が便利になりすぎた後の組織と社会のひずみ」へ、議題の重心がはっきり移った一日でした。日本の現場で特に効きそうなのは VS Code Agent window（条 7）と、同じ Skills で Claude Code と Codex を対局させたレポート（条 8）の二本。前者は「複数エージェントを並列で動かす UI が IDE 標準に降りてきた」初の本気の実装で、後者は「同じプロンプトでもモデルの推論スタイルが違うので、Skills で抑えるか否かの設計判断が必要」という、エンタープライズで明日から使える視点を提供してくれます。

---

## 1. RAV4 hybrid 2024 から DCM と GPS を物理的に取り外す

タグ：[EN · HN トップ 442 pt]
リンク：<https://arkadiyt.com/2026/05/13/removing-the-modem-and-gps-from-my-rav4/>

トヨタ車に積まれている DCM（Data Communication Module）と GPS アンテナを所有者自身が分解して取り外し、CAN バスは抵抗でターミネーションして「DCM がまだ生きている」と車載コンピュータに思わせる、という詳細な手順書。HN コメント欄では「事故時の自動通報がなくなるリスクをどう考えるか」と「メーカーが収集するテレメトリの開示請求がなぜここまで面倒なのか」の二点で議論が活発でした。日本では「コネクテッドカー」の文脈でデータ取得停止が論じられていますが、EU の Data Act では既に「車両所有者がテレメトリを停止する権利」が制度化されつつあります。自動車関連 SaaS を作っている方は、設計前提を見直す一日にしてもよさそうです。

## 2. Nginx の新しいスタックオーバーフロー PoC

タグ：[EN · HN トップ 223 pt]
リンク：<https://github.com/DepthFirstDisclosures/Nginx-Rift>

`DepthFirstDisclosures/Nginx-Rift` で公開された Nginx 向けの PoC。特定の worker 設定と上流側 chunked encoding の組み合わせで発火するスタックオーバーフロー型の脆弱性です。F5 の公式アドバイザリは執筆時点で未公開ですが、HN のコメント欄に大手いくつかが「`large_client_header_buffers` を厳しめに、上流側で chunked を切る」という一時的な mitigation を共有しています。OpenResty や各クラウドの Nginx fork を使っている日本企業の ingress 担当の方は、本家パッチが出るまでに自分の構成が該当パスを露出していないかチェックしておくと安全です。

## 3. GitHub Trending：obra/superpowers — Claude Code 用 Skills フレームワーク

タグ：[EN · GitHub Trending]
リンク：<https://github.com/obra/superpowers>

obra（Jesse Vincent）による "agentic skills framework"。Markdown + shell スクリプト + 軽い規約で「業務手順」「ツール呼び出しパターン」「気を付ける点」を Claude Code から読み込み可能な Skills として束ねる、という方法論をリファレンス実装にしたものです。直近で 1,801 stars/day、Skills 系リポジトリの中で最も参照されている実装の一つになりました。Anthropic 公式の Skills 仕様と互換ですが、obra 流は「まず手順書を書く → script に落とす」という順序を強調しているのが特徴。本日の Zenn の Claude vs Codex オセロ対局も、この superpowers 系の Skills 構成を使っています。社内 AI 運用マニュアルを整理し始めたチームは、ディレクトリ構成だけでも参考になります。

## 4. Mojo 1.0 が Beta 到達

タグ：[Wildcard · Publickey]
リンク：<https://www.publickey1.jp/blog/26/aipythonmojo.html>

Modular（Chris Lattner 率いる）の Mojo がついに 1.0 Beta。Mojo の売りは一貫して「Python ライクな構文で書きつつ、コンパイル時に MLIR へ落ちて GPU や異種ハードウェアにそのまま最適化される」点です。Beta フェーズに入ったということは言語仕様はほぼ凍結、これからの数か月は標準ライブラリとパッケージマネージャ周りの整備が中心になります。日本の推論基盤チームにとっては、PyTorch のカスタム CUDA カーネルを書く工数を 1〜2 桁減らせる可能性のある選択肢。今週 1〜2 時間とって SIMD/ベクトル化プリミティブの章だけでも読んでおくと、2026 年後半の議論についていきやすくなります。

## 5. Bun の Rust 書き直し PR が main にマージ

タグ：[ZH · V2EX 経由 / Bun 公式]
リンク：<https://www.v2ex.com/t/1212789>

Bun はもともと Zig 製でしたが、今年初に「段階的に Rust に移行する」と公式アナウンス。理由は Zig のツールチェイン成熟度が企業のコントリビューターから見るとまだ重い、というのが大きい。今回マージされた PR はコアの native binding を Rust runtime に切り替えるもので、テストスイートはひととおりグリーン。V2EX のコメント欄では「Zig で差別化していた Bun が Deno / Node と同じ Rust ベースに収束するのは長期的にキャラを失わないか」「npm 互換層の長年のバグはこの PR では潰されていない」といった声が並んでいます。Bun に倒した社内ビルドパイプラインを持つチームは、リリースノートのウォッチを継続するのが無難です。

## 6. 会社で買った LLM の API キーを同僚が横流ししていた話

タグ：[ZH · V2EX]
リンク：<https://www.v2ex.com/t/1212742>

中国の V2EX で朝から伸びていた相談スレッド。会社が年契約で買った Claude/OpenAI 系ゲートウェイのキーを、ある同僚が「友人何人かに」共有していて、月末の usage が想定の数倍に達した、というインシデント報告です。コメント欄は具体的で、「per-user API key + 監査ログ」「team の master token を共有しない」「業務上横領に該当する可能性があり懲戒事由になり得る」といった実務的な指針が共有されていました。日本企業で LLM を本格運用しているところでも、ゲートウェイのキー管理を「個人ごとに発行・ローテーション・利用量上限」の三点セットで整える社内ルールを書き始めるタイミングだと思います。

## 7. VS Code 1.108、複数 AI エージェントを並列に動かす「Agent window」プレビュー

タグ：[JA · Publickey]
リンク：<https://www.publickey1.jp/blog/26/vs_codeaiagent_window.html>

5 月 13 日リリースの VS Code 1.108 に、Agent window という新しいウィンドウ形態がプレビュー追加されました。同一 workspace 内で Copilot / Claude Code / Codex / ローカルモデルを並列に走らせ、それぞれの会話と独立した diff バッファを左右で見比べてからマージできる、というもの。これは昨日 Simon Willison が引用していた Boris Mann の「『11 個の AI エージェントを持っている』はそれ自体に意味はない」というツッコミに対する Microsoft からの回答に見えます。意味があるのは並列に走らせる土台と比較 UI であり、IDE がその土台を提供する側に回った、というのが今日のいちばん大きな構造変化です。

## 8. 同じ Skills で Claude Code と Codex をオセロ対局させたら 56-8

タグ：[JA · Zenn]
リンク：<https://zenn.dev/doai/articles/cc97075e985938>

@doai さんが「オセロのルール + 評価関数」を Skills として両方の Coding Agent に渡し、対局させた記録。本記事の面白さは結果ではなく、両モデルの「推論の途中経過」を全部貼ってあるところ。Claude は「この手の 4 手先までの確定石数」を先に出してから決める傾向が強く、Codex は「ヒューリスティック + 試行錯誤」型で動きます。同じ Skills を渡しても推論スタイルがここまで違うという観察は、エンタープライズで「どのモデルにどのタスクを当てるか」を設計する際の貴重なデータです。Skills を本気で運用し始めたチームに今日一番読んでほしい一本。

## 9. Anthropic がゲイツ財団と 2 億ドルパートナーシップ、グローバルヘルスに集中

タグ：[Wildcard · Anthropic 公式]
リンク：<https://www.anthropic.com/news/gates-foundation-partnership>

Anthropic と Bill & Melinda Gates Foundation が 5 年 2 億ドルの協業を発表しました。対象は中低所得国の感染症サーベイランス、プライマリケア支援、医療データ統治。半分は Anthropic API クレジット＋エンジニアの現場派遣として、残り半分は NGO と現地政府への直接資金として動きます。注目すべきは事業構造で、Anthropic は「OpenAI と純粋な企業市場で殴り合う」のではなく「基盤モデル × 公益協業 × 政府調達」という三角形を拡張中。日本企業が海外のソブリンクラウドや厚労相当の機関と組むときの参照ケースとして、今後の RFP で引用されることになるはずです。

## 10. Node.js 26：Temporal がデフォルト有効、Date 時代の終わり

タグ：[Wildcard · Publickey]
リンク：<https://www.publickey1.jp/blog/26/nodejsdatetemporaltemporalchromeedgefirefoxnodejs.html>

Node.js 26 正式版で ECMA-402 Temporal がデフォルト有効化されました。これで Chrome / Edge / Firefox / Node が揃ったことになり、フロントもバックも「ようやく `new Date()` から逃げられる」状態に。Temporal が解決するのは Date の歴史的な負債──ミュータブル、月が 0 始まり、タイムゾーン処理が `toLocaleString` 頼み、といったあれです。クロスリージョン SaaS をやっている日本の開発組織は「東京 vs UTC vs America/Los_Angeles」のロジックを `Temporal.ZonedDateTime` で書き換えるリファクタリング計画を、今期中に立てる価値があります。lint で `new Date()` を新規コードから禁止するルールを足すのが現実的な一手。

---

## 編集後記

今日の 10 本を俯瞰すると、見えてくるのは二つの方向：**基盤レイヤーが何年も溜め込んでいた負債を一気に返済している**（Bun の Rust 化、Node.js Temporal、Mojo Beta、IDE が AI を一等市民として迎える）一方で、**人と組織側の運用前提が想像より早く崩れている**（API キーの横流し、車の通信モジュールを所有者が自分で外す、複数エージェントを並列運用する日常）。今日 2 本だけ読むなら、条 7（VS Code Agent window）と条 6（API キー横流し）。前者は明日からのワークフロー設計を、後者は今期の社内ガバナンス設計を変えるテーマです。

*Dev Digest 編集部*
