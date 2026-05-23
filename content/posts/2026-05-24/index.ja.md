---
title: "5月24日 · 今日のテック厳選10本"
date: 2026-05-24T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "memory-shortage", "ai-privacy", "supply-chain", "anthropic"]
categories: ["daily"]
summary: >-
  HBMが消費者向けメモリを食い尽くし、廉価スマホが値上げへ。Claude Opus 4.7は文体から本名を推測でき、匿名性のデフォルトが静かに崩れる。Daniel Lemireは「二分探索を超える」現代版を提示。Zennトレンドは「Claude Max 20xでもトークン不足」と「Vibe Coding時代のサプライチェーン攻撃」が首位。Anthropic Project Glasswingの半年経過レポート、cPanelの実環境脆弱性、EFFがNSAのRoom 641Aを知った経緯を回顧する書籍抜粋。今日のテーマは「AIによって既存の物差しが失効する」一日。
---

## 本日のサマリー

物理層（HBMの晶圓占有がDDR/LPDDRを締め上げる）、モデル層（Opus 4.7が文体から本名を当てる）、プロセス層（AI時代のcommit数KPI）、ガバナンス層（Glasswingの中間報告、cPanel在野脆弱性）——AIが各レイヤーで既存秩序を再計算させる一日です。日本企業の運用観点で特に重く効くのは「メモリ価格の構造変化」と「Vibe Coding由来のサプライチェーン攻撃」の2本。前者は2027年の調達計画、後者は今日からのlockfile運用に直結します。

## 1. メモリ不足、消費者向けエレクトロニクスの値段表を書き換える

[The memory shortage is causing a repricing of consumer electronics](https://davidoks.blog/p/ai-is-killing-the-cheap-smartphone) · `Simon Willison / David Oks`

世界のメモリ製造大手は実質3社、ウエハ供給量は固定。そこをHBM（AI GPU向け）が侵食し、2026年末にはHBMが全ウエハの20%を占める見込み。HBMは1GBあたりDDR/LPDDRの3倍以上のウエハを消費するため、結果として100ドル以下のスマホがまず犠牲になります。日本の業務端末の更新計画は、来期から実質値上げを前提に組み直す必要がありそうです。

## 2. Claude Opus 4.7、文体だけで「本当のKelsey」を当ててくる

[Opus 4.7 knows the real Kelsey](https://www.theargumentmag.com/p/i-can-never-talk-to-an-ai-anonymously) · `The Argument Magazine / HN`

記者Kelseyが「匿名」設定でClaudeと会話したところ、数ターンで本名と職業背景を当てられた話。手がかりは文体・語彙・業界用語の3点セット。匿名チャットというUXのデフォルトが、最強モデルの前ではもはや成立していないという問題提起です。社内チャットBot、問い合わせ窓口、医療相談など匿名性を前提にしたUIを抱える事業は、この前提を今日から見直したほうがいい。

## 3. Daniel Lemire · 二分探索は超えられる

[You can beat the binary search](https://lemire.me/blog/2026/04/27/you-can-beat-the-binary-search/) · `lemire.me / HN`

分岐予測に優しい条件移動を使った実装で、`std::lower_bound`より20〜40%速くなる事例の解説。算術命令の追加で分岐ペナルティを潰すという、現代CPUの実情に合わせた最適化です。ホットパス担当の方は10分の投資価値あり。学校で習った「O(log n)で十分」は2026年のマイクロアーキでは必ずしも最適ではない、と再認識できます。

## 4. Zennトレンド · Claude Max 20xでも足りない、トークン節約8選

[Claude Max 20xプランでも足りないので、トークン節約のためにやったこと8選](https://zenn.dev/acntechjp/articles/1396e20b5167ce) · `Zenn / Accenture Japan`

Accenture Japan有志による実戦記。context分割、cache hit戦略、安いモデルでplan→高いモデルでexecuteの切り分け、`/clear`の打ちどころなど。月200ドルのMax 20xでも超過する現実が来ていて、ボトルネックは「払えるか」より「節約スキルがあるか」に移っています。SIerの現場で展開する際の値段交渉資料としても使えます。

## 5. Zennトレンド · Vibe Coding時代のサプライチェーン攻撃と防御

[Vibe Coding 時代のサプライチェーン攻撃と防御方法](https://zenn.dev/loglass/articles/c619f704045181) · `Zenn / ログラス`

LLMが生成する偽パッケージ名を攻撃者が事前にsquattingする「slopsquatting」、prompt injectionによるlockfile書き換え、IDE拡張のサイレントinstallなど、Vibe Coding特有の攻撃面を6つに整理。今週のPyTorch Lightning Shai-Hulud事件と合わせて読むと、Coding Agentを業務投入する前のチェックリストとして実用的です。

## 6. V2EX · qwen3.7-max、中国産モデルの評価軸が変わる

[qwen3.7-max 的代码能力提升非常大](https://www.v2ex.com/t/1214878) · `V2EX`

中国の開発者コミュニティで、qwen3.7-maxのコード生成能力が前世代から大きく跳ねたという報告が広がっています。「Claude Sonnet 4.6に肉薄」という評価で、阿里雲のtoken planから直接呼べる点も国内利用を後押し。日本企業でも、中国側拠点・パートナー企業が「まず通義で試してみよう」と提案してくる場面が今期から増えそうです。

## 7. V2EX · AIによってcommit数はもうKPIにならない

[自从有了 AI 之后，Commit 数量是不是已经不适合衡量开发效率了](https://www.v2ex.com/t/1214914) · `V2EX`

中国の開発者掲示板での議論。AIで作業量が水増しされる前提のもとで、commit数はもはや開発効率指標として機能しないという主張に対し、「PR通過率と本番障害率を見るべき」「AIで簡単に膨らむKPIは全部見直し対象」という意見が並びます。日本企業の人事制度・開発組織OKRも、来期から代理指標の整理が必要になる議論です。

## 8. Anthropic · Project Glasswing 半年経過レポート

[Project Glasswing: An initial update](https://www.anthropic.com/research/glasswing-initial-update) · `Anthropic`

AWS、Apple、Google、Microsoft、CrowdStrike、JPMorgan、Linux Foundationなどと組んだ、AIによる重要OSSの脆弱性監査プロジェクトの中間報告。修正済みCVE数、各社との連携プロセス、英NHSが一部リポジトリを非公開化した件への間接的な応答が含まれます。AIが国家基盤的なOSSセキュリティに「制度として」組み込まれる、その最初のテンプレートです。

## 9. EFFはどうやってRoom 641Aを知ったか（書籍抜粋）

[How Mark Klein told the EFF about Room 641A (book excerpt)](https://thereader.mitpress.mit.edu/the-whistleblower-who-uncovered-the-nsas-big-brother-machine/) · `MIT Press Reader / HN`

MIT Pressの新刊抜粋。2006年にAT&T技師Mark Kleinが、サンフランシスコの光ファイバ分岐室をEFFに告発した経緯を当時の手記から再構成しています。今日この記事を読むと、20年前は政府が回線中継点で盗聴していたものが、今や消費者向けモデルが文体から個人を特定する形に進化していることに気付かされます。手段は変わっても「匿名性が侵される」構造は同じです。

## 10. cPanel/WHMの実環境脆弱性、攻撃が活発化

[Hackers are actively exploiting a bug in cPanel and WHM](https://techcrunch.com/2026/04/30/hackers-are-actively-exploiting-a-bug-in-cpanel-used-by-millions-of-websites/) · `TechCrunch / HN`

世界の共有ホスティングのデファクトであるcPanel/WHMに在野で悪用されている脆弱性が確認されました。日本国内のホスティング事業者、レンタルサーバー再販業者、個人サイト運営者にも影響範囲が広いので、今日中のパッチ適用とroot SSHログ・最近のwebshell混入チェックを推奨します。

## 編集後記

本日のメタテーマは「AIにより既存のものさしが失効する」——メモリ価格、匿名性、commitKPI、二分探索の「O(log n)で十分」、いずれもAIの台頭で再計算が必要になっています。必読は **メモリ不足の構造解説**（中期の調達と価格戦略に直結）と **Opus 4.7のKelsey事件**（匿名UXのデフォルトを今日から見直すきっかけ）。なお、Zenn APIから取得したトレンドは約1ヶ月遅延がありますが、内容の有用性から本日も2本採用しました。GitHub Trendingは今日のフェッチが空応答だったため個別項目は割愛しています。
