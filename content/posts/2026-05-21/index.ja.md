---
title: "5月21日 · 今日のテック厳選10本"
date: 2026-05-21T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "ai-agents", "antigravity", "dell", "agntcon"]
categories: ["daily"]
summary: >-
  LinkedIn が 6,278 個のブラウザ拡張を毎回スキャンしていることが判明。ベルギーは原発の廃炉を撤回。honker.dev は SQLite 1ファイルに耐久キュー / Stream / Pub-Sub / Cron を全部入れた。日本側では Google Antigravity 2.0、Dell Deskside Agentic AI、Google Managed Agent API、そして Linux Foundation の AGNTCon + MCPCon が 9 月に東京渋谷で開催決定。今日のテーマは「AI エージェントが基盤を取りに来た」——電気、ハード、API、会場まで含めて。
---

## 本日のサマリー

今日のキーワードはひとつ、「Agent がインフラ層を飲み込みに来た」です。Google は Managed Agent API で「Linux サンドボックス付き Agent」を 1 API 呼び出しで提供開始。Dell は GB10 / GB300 をデスクトップに載せた "Deskside Agentic AI" を発表。Antigravity 2.0 のデモでは Agent が空のリポジトリから OS を書き上げ Doom まで動かしました。日本企業視点で見逃せないのは、Linux Foundation が AGNTCon + MCPCon の会場に東京渋谷を選んだ事実。AI エージェント関連の予算が日本市場にも本気で降りてきたサインです。セキュリティ面では LinkedIn の拡張機能スキャン問題が、業務で SaaS 管理画面を扱う方への警告として効いてきます。

## 1. LinkedIn が 6,278 個のブラウザ拡張を毎リクエストでスキャン

[LinkedIn scans for 6,278 extensions and encrypts the results into every request](https://404privacy.com/blog/linkedin-is-scanning-your-browser-extensions-this-is-how-they-use-the-data/) · `Hacker News`

404privacy の調査で、LinkedIn が既知の Chrome 拡張 6,278 個をクライアント側 JS で能動的に検出し、暗号化して毎 API リクエストに添付していることが分かりました。営業職や採用担当が Sales Navigator 系の自動化拡張を使う場合、当然ながら検知対象になります。社内利用ポリシー上、ブラウザプロファイルを業務用と検証用で分けている方は、LinkedIn 系の自動化ツールは必ず別プロファイルに隔離するのが安全です。

## 2. ベルギー、原発の廃炉を撤回

[Belgium stops decommissioning nuclear power plants](https://dpa-international.com/general-news/urn:newsml:dpa.com:20090101:260430-930-14717/) · `Hacker News`

廃炉予定だった原子炉 2 基の運転継続を政府が決定。AI データセンターの電力需要増を明示的に理由として挙げています。英国・スウェーデンに続く欧州の方針転換で、AI 投資が動かしているのは半導体ではなく電源だ、という現実が一段とはっきりしました。日本の電力会社や経産省側の議論にも遅れて影響してくるはずなので、エネルギー業界寄りの SI に関わる方は流れを押さえておく価値があります。

## 3. honker.dev · 耐久キュー / Stream / Pub-Sub / Cron を SQLite 1ファイルに

[Durable queues, streams, pub/sub, and a cron scheduler – inside your SQLite file](https://honker.dev/) · `Hacker News`

Sidekiq / NATS / Cron 的な機能を、SQLite 1 ファイルに収めた組み込み型ライブラリ。プロセス内で完結し、ファイルコピーでバックアップできる手軽さがウリです。社内向けの自動化ワーカーや Bot、小規模 SaaS のバックエンドで、Redis + 別途キュー基盤を立てる手間を一段抜くのに向いています。WAL モード前提で単機数千 TPS を狙えるという主張で、用途次第では十分実用域です。

## 4. V2EX · 国産 AI IDE で一番マシなのはやはり TRAE か

[国産的 AI IDE 矮子头上选将军好像也就 TRAE 好用点](https://www.v2ex.com/t/1213384) · `V2EX`

中国の開発者コミュニティでの議論。中国国産 AI IDE（通義霊碼・CodeGeeX・文心快碼・TRAE）を比較し「Agent モードでまともに動くのは TRAE くらい」という結論。日本のエンジニアにとっての示唆は「中国市場では Claude Code / Cursor が直接使えないので別エコシステムが立ち上がっている」点です。日本拠点で中国側チームと共同開発しているなら、相手側 IDE 事情を把握しておくと差分の説明コストが下がります。

## 5. V2EX · 「算力ネット」が来る — 中国の全国統一コンピュート基盤

["算力网"要来了](https://www.v2ex.com/t/1213402) · `V2EX`

中国版「東数西算 2.0」の進捗スレッド。省を跨いだ GPU リソースの統一スケジューリングと価格決定機構の話で、要は EU が議論している「ソブリン AI コンピュート」の中国版です。日本企業の中国子会社で AI 学習を回している場合、来年以降の調達経路が変わる可能性があります。即時の影響はないが、来年度予算を組む段階で「中国側 GPU 調達は本土プラットフォーム経由が前提」と織り込んでおいた方が無難です。

## 6. Publickey · Google Antigravity 2.0、Agent が OS を書いて Doom まで起動

[Google、Antigravity 2.0発表。デモとしてゼロからOSを開発、Doomも実行可能に](https://www.publickey1.jp/blog/26/googleantigravity_20osdoom.html) · `Publickey`

Antigravity の Agent ランタイムが 2.0 に。長時間タスクの自律分解と再計画が強化され、デモでは空のリポジトリから最小 OS を実装、Doom を動かすところまでをノーガイドで完走しています。Claude Code、OpenAI Codex に続き、Google が「実プロジェクトを Agent に最後まで任せる」陣営に揃ったかたちです。社内 PoC で「Coding Agent はどこまで任せられるか」を測る局面なら、3 社並べてのベンチが避けて通れません。

## 7. Publickey · Dell Deskside Agentic AI、GB10 / GB300 を載せたデスクトップ

[デル、ローカルでAIエージェントを動かすためのデスクトップPCなど Dell Deskside Agentic AI 発表](https://www.publickey1.jp/blog/26/aipcdell_deskside_agentic_ainvidia_gb10gb300.html) · `Publickey`

GB10 / GB300 を搭載したデスクトップ機を「ローカルで Agent を回す業務マシン」として打ち出しました。日本企業との相性が良い製品設計です。コードを社外に出せない金融・公共・製造領域は、本気で「クラウド経由ではなくデスクサイド」を選ぶ動きが出てきそうです。PoC 予算を組む段階の方は、ハード調達 + Claude / 国内 LLM ハイブリッドの構成図を一度引いておくと社内提案が早くなります。

## 8. Anthropic · フロンティア AI の議論を広げる

[Widening the conversation on frontier AI](https://www.anthropic.com/news/widening-conversation-ai) · `Anthropic News`

Anthropic がフロンティアモデルの能力評価を「ラボの内側だけで完結させない」ための方針を表明。政府・学術・第三者機関を巻き込む方向です。実務影響としては、企業が Claude を本番採用する際の合規エビデンスとして RSP（Responsible Scaling Policy）系の文書が要求される場面が増えそうです。日本企業の IT 部門が今後 LLM 採用稟議を回すとき、想定 Q&A に追加しておきたいトピックです。

## 9. Publickey · Google Managed Agent API、1 API 呼び出しで Linux 環境付き Agent を起動

[APIコール一発でGoogleがホストするLinux環境付きのAIエージェントを起動、Markdownでカスタム指示もできる Managed Agent API 発表](https://www.publickey1.jp/blog/26/apigooglelinuxaimarkdownmanaged_agent_api.html) · `Publickey`

Google Cloud に新しい Managed Agent API が追加。1 回の API 呼び出しで Linux サンドボックス付きの Agent インスタンスが立ち上がり、Markdown でカスタム指示を渡せます。Anthropic の Claude Agent SDK + Code Execution の Google 版にあたります。SaaS バックエンドで「ユーザーごとに隔離された Agent サンドボックス」を提供したい事業者にとって、自前で Firecracker / gVisor を運用しない選択肢が増えたことになります。

## 10. Linux Foundation · AGNTCon + MCPCon、9 月 10-11 日に東京渋谷で開催

[Linux Foundation、AIエージェントをテーマにしたイベント AGNTCon + MCPCon を東京渋谷で開催](https://www.publickey1.jp/blog/26/linux_foundationaiagntcon_mcpcon910112.html) · `Publickey`

LF が AI Agent / MCP テーマの 2 イベントを 9 月 10-11 日に東京渋谷で同時開催すると発表。海外勢の主要 vendor がほぼ揃う見込みで、日本企業のキーパーソンとの接続が一気に取れる窓になります。スピーカー / スポンサー枠の応募はこれから本格化するので、Agent / MCP 関連プロダクトを持っている方は早めにエントリーを検討する価値があります。

## 編集後記

本日のテーマは「AI Agent がインフラ階層に降りてきた」。原発の運転継続、デスクサイド GPU PC、マネージド Agent API、東京開催の AGNTCon——これら全てが「デモから業務基盤へ」のシグナルです。**マスト読み 2 本：LinkedIn 拡張スキャン**（業務 SaaS をブラウザで触る人は全員影響あり）と **Google Managed Agent API**（自社で sandbox 基盤を持っている企業は今後 12 ヶ月で再検討対象になります）。なお Zenn の Trending ページは本日 SSR レンダリングが空で取得できなかったため、JA 枠は Publickey 中心で構成しています。
