---
title: "5月26日 · 今日のテック厳選10本"
date: 2026-05-26T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "coding-agents", "memory-shortage", "ai-economics", "security", "publickey", "rhel"]
categories: ["daily"]
summary: >-
  Claude Code が commit メッセージに「OpenClaw」と書くだけで拒否したり追加課金を要求したりするという挙動が HN トップを取りました。AI ベンダーが競合名を区別しているかどうかが、初めて公開議題になった一日です。DDR/HBM の wafer 配分をめぐる David Oks の分析は、AI データセンタの拡張が消費者向けスマホ価格に直接効いてくる因果を明快に説明しています。xAI が Grok Build CLI を投入し Anthropic と Google の編集 agent に並びかけ、Red Hat は RHEL の「無期限サポート」アドオンを発表。一方で FTC は「Active Listening」広告を打っていた Cox Media Group に約 100 万ドルの罰金、Gentoo 開発者は CopyFail の disclosure を迂回されたと声を上げ、スペイン議会は LaLiga による大量 IP ブロックに立法で対抗する構えです。今日のメタテーマは「AI 時代のインフラに値札が貼り直されている」。
---

## 本日のサマリー

本日 10 本のメタテーマは一言で **「AI 時代のインフラに値札が貼り直されている」** です。Claude Code が競合名 "OpenClaw" を含む commit を別扱いしている件は、AI ベンダの「振る舞いを観測できるか」という問題を初めて HN トップに押し上げました。David Oks の DDR/HBM 配分の解説は、AI データセンタが LPDDR の wafer 枠を奪った結果、サブ 100 ドル帯のスマホが先に値上がりするという物理因果を明快に示します。日本企業の文脈で読むなら、コーディング agent の戦線が xAI Grok Build の参入で 3 社競合になったこと、Red Hat の RHEL Long-Life が金融・電力・公共の「監査対応で永遠に上げられない OS」を救うこと、この 2 本が特に響くはずです。FTC の「マイク盗聴広告」判決、CopyFail の disclosure 迂回、LaLiga の IP ブロック立法化と、プライバシー / セキュリティ / ネットワーク中立性の話題も同時並行で動いています。

## 1. Claude Code、commit に "OpenClaw" と書くと拒否または追加課金

[Claude Code refuses requests or charges extra if your commits mention "OpenClaw"](https://twitter.com/theo/status/2049645973350363168) · `Twitter / HN 865 points`

本日の HN トップ。開発者 Theo 氏が、git commit メッセージに競合プロダクト名「OpenClaw」を含めると Claude Code が依頼を拒否したり「上位プランへのアップグレードが必要」と返したりする挙動を公開しました。AI ベンダがプロンプトの中で競合名をどう扱っているのか、その「振る舞いの公開可能性」が初めて市民権を得た形です。日本の SaaS で AI モデルを再ラップして提供している事業者にとっても、自社モデルの振る舞いが第三者から逆解析され得るという前提で SOP を作る必要があります。

## 2. AI が消費者向け DRAM を食い尽くしている – メモリ高騰の本当の理由

[The memory shortage is causing a repricing of consumer electronics](https://davidoks.blog/p/ai-is-killing-the-cheap-smartphone) · `davidoks.blog / Simon Willison`

David Oks 氏が、世界に 3 社しか残っていない DRAM メーカが、固定された wafer 容量を DDR・LPDDR・HBM の 3 つに配分している構造を整理しています。HBM 向けの割り当ては 2% から 2026 年末の 20% まで急上昇、しかも 1GB の HBM は同容量の DDR/LPDDR の 3 倍超の wafer を消費する。結果として最初にしわ寄せが来るのが 100 ドル以下の Android 端末、つまりアフリカ・南アジア市場です。日本国内のメーカが安価モデルの BOM を組み直す時期に入ったというサインでもあります。

## 3. Pu.sh – シェルスクリプト 400 行で動く完全な coding-agent harness

[Pu.sh – a full coding-agent harness in 400 lines of shell](https://pu.dev/) · `pu.dev / HN`

Show HN に上がった反潮流プロジェクト。Python も Docker も使わず、POSIX shell 400 行だけで「ファイル読み・編集・テスト実行・次の手を決める」までの agent コアループを実装しています。Claude Code や Cursor のような重 IDE 路線へのアンチテーゼで、組み込み機器・閉域網・隔離 CI など制約環境で agent を動かしたい現場には現実的な選択肢になります。「agent harness は実はそんなに大層なものではない」という宣言として読めます。

## 4. 阿里云の社内開発者に Claude Code 4.6 無制限、週次 token 消費ランキング

[公司给每个研发分配了不限量 CC sonnet 4.6，每周发布额度消耗排行榜](https://www.v2ex.com/t/1215243) · `V2EX`

中国の V2EX で話題になっているスレッド。会社が Claude Code Sonnet 4.6 を「使い放題」で配布しつつ、週次の token 消費量でランキングを発表するという運用です。コメント欄は二派に割れていて、「token 消費量を KPI 化すると水増しが必ず起きる」派と「AI を使えるかどうかは実力差なのでランキングが妥当」派の論争に。日本企業で AI 開発ツールを導入中の組織にも 100% 跳ね返ってくる議題で、「成果」と「消費量」を切り分けない KPI 設計は早晩失敗するでしょう。

## 5. 阿里云が DNS 解決サービスの有料化を発表

[阿里云的 dns 解析要收钱了](https://www.v2ex.com/t/1215176) · `V2EX`

これまで無料だった阿里云の DNS 解決サービスが、有料化されることになりました。V2EX のスレッドは 110 件超のコメントで「無料インフラ時代の終焉」と評しています。日本のクラウド利用者にとっても他人事ではなく、AWS Route 53、Google Cloud DNS の競合だった「無料 DNS」の選択肢が一つ減るということ。さらに広い文脈では、クラウドベンダが「集客用に無料で出していた小サービス」に一斉に値札を付け直す流れの 1 つ目です。インフラコスト見積を見直す良いタイミング。

## 6. xAI がコーディング agent「Grok Build」ベータ公開

[xAIがコーディングエージェント「Grok Build」ベータ公開。サブエージェントを並列に実行可能など](https://www.publickey1.jp/blog/26/xaigrok_build.html) · `Publickey`

イーロン・マスク氏の xAI が、コーディング特化の agent CLI「Grok Build」早期ベータを公開しました。差別化ポイントは sub-agent の並列実行 – 親 agent が複数の sub-agent にタスクを振って同時に走らせ、結果を集約する仕組みです。Anthropic の Agent SDK でも実現は可能ですが、xAI は最初から「並列前提の CLI」として打ち出しました。Claude Code、Google Antigravity CLI に続く 3 番手として、日本企業の開発現場で評価対象に加える価値があります。

## 7. Red Hat、無期限サポート「RHEL Long-Life アドオン」発表

[あるバージョンのRHELを永遠に動かし続けられる。Red Hatが期限のないサポート](https://www.publickey1.jp/blog/26/rhelred_hatred_hat_enterprise_linux_long-life.html) · `Publickey`

Red Hat Summit 2026 で発表された RHEL Long-Life アドオン。指定したバージョンの RHEL を「期限なし」でセキュリティ更新・サポートし続けるという有料オプションで、金融・電力・官公庁といった「監査周期の中でメジャー OS バージョンを上げられない」現場が主な対象です。日本でも社会インフラ系で同様の課題は普遍的に存在しており、CentOS Stream への移行を躊躇していた組織にとっては「正規ルートで永久に止まらない」契約形態が選べるのは大きな安心材料になります。

## 8. FTC、Cox Media Group の「Active Listening」マイク盗聴広告に約 100 万ドル罰金

[FTC to Require Cox Media Group, Two Other Firms to Pay Nearly $1 Million](https://www.ftc.gov/news-events/news/press-releases/2026/05/ftc-require-cox-media-group-two-other-firms-pay-nearly-1-million-settle-charges-they-deceived) · `FTC / Simon Willison`

2024 年に話題になった「スマートフォンがマイクで会話を盗聴して広告ターゲティングしている」というあの売り文句、ようやく FTC が決着をつけました。Cox Media Group、MindSift、1010 Digital Works の 3 社に合計約 100 万ドルの和解金、結論は「実際には音声データなど一切使っておらず、データブローカから買った email リストを転売していただけ」。さらに FTC は「アプリの利用規約にこっそり入れた opt-in は有効な同意とは認められない」と明示。日本国内で広告 SDK を組み込んでいるアプリ開発者にとっても、規約上の文言設計を見直す根拠になります。

## 9. CopyFail 脆弱性、Gentoo 開発者への disclosure が迂回された

[CopyFail was not disclosed to Gentoo developer](https://www.openwall.com/lists/oss-security/2026/04/30/10) · `openwall / HN`

Gentoo の開発者が oss-security メーリングリストで抗議：CopyFail と名付けられた脆弱性の発見時、研究者が通常の coordinated disclosure の手順を踏まずに Gentoo を素通りして上流に直接報告し、ディストリビュータが公開後の対応に追われたという話です。「研究者は上流（vendor）と協調するがディストロを忘れる」というパターンはオープンソース界隈で繰り返されており、disclosure SLA の設計テンプレートとして読む価値があります。日本で OSS 配布物の保守をしている技術者にも示唆的。

## 10. スペイン議会、LaLiga による大量 IP ブロックに立法で対抗の構え

[Spain's parliament will act against massive IP blockages by LaLiga](https://www.democrata.es/en/politics/congress-and-senate/congress-will-act-against-massive-ip-blockages-by-laliga/) · `democrata.es / HN`

スペインのサッカーリーグ LaLiga は、海賊配信対策として裁判所命令で大規模に CDN の IP レンジを ISP にブロックさせてきました。副作用として Cloudflare、Vercel などの共有 IP を使う無関係のサイトが巻き添えで一時アクセス不能になる事案が頻発し、いよいよ国会が立法レベルで「商業団体による IP ブロックの正当性」に枠をはめる動きに入りました。EU で「商用 IP ブロックの責任分界」が初めて立法で議論される事例で、日本企業が EU 向けに CDN を運用する際の前例として注視に値します。

## 編集後記

今日の暗号メッセージは **「AI 時代のインフラに値札が貼り直されている」** です。物理レイヤ（DDR/HBM）、クラウドレイヤ（阿里云 DNS）、プロトコルレイヤ（LaLiga）、倫理レイヤ（FTC・CopyFail）、企業レイヤ（Claude Code KPI）と、全レイヤで料金体系と責任分界が同時に更新されつつあります。本日「これだけは読む」を 2 本選ぶなら、まず **2 番の DRAM 配分の話** – AI 投資のコストが物理的に消費者へ転嫁される因果が初めて明快に説明されました。次に **1 番の OpenClaw 拒否** – モデルの振る舞いを観測できるかという問題が、ベンチマーク数字より重要な競争軸になり始めています。
