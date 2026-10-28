---
title: "October 28 · Today's 10 Dev Picks"
date: 2026-10-28T07:00:00+09:00
draft: false
tags: ["digest", "2026-10", "ai", "developer-tools", "testing"]
categories: ["daily"]
summary: "Ten reads on the developer workflow beneath today's AI headlines."
---

# October 28 · Today's 10 Dev Picks

## Today at a glance

The interesting thread today is infrastructure for judgment, not another claim of frictionless automation. Terminal releases, testing strategy, formatting compatibility, and AI explanations all come down to making the default workflow trustworthy.

## Picks

### Ghostty 1.4
**[HN / Terminal](https://ghostty.org/docs/install/release-notes/1-4-0)**

Ghostty 1.4 lands with another round of features and fixes. Terminal software is a mature category, but rendering, input latency, and configuration ergonomics compound across an entire workday. Treat this as a chance to audit local-development friction, not simply a reason to switch terminals.

### Python's experimental JIT is being removed
**[HN / Python](https://lwn.net/SubscriberLink/1102102/0c00e4d550f25f8c/)**

CPython's experimental JIT is headed out. That is a useful reminder that runtime work survives on maintenance cost and compatibility as much as on benchmark wins. Teams planning around Python performance should keep production profiling, rather than a future JIT, at the center of their capacity model.

### Game Boy Color on a conference badge
**[Simon Willison](https://simonwillison.net/2026/Oct/27/game-boy-color-on-my-conference-badge/)**

Simon Willison documents fitting a Game Boy Color into a conference badge. It is a playful hardware project, but constrained displays, power budgets, and input methods make sharp product-design teachers. Building one deliberately constrained thing can reveal more about prioritization than another dashboard prototype.

### Thinkrail and the lightweight-editor reset
**[V2EX](https://www.v2ex.com/t/1252393)**

Developers are discussing JetBrains Thinkrail after the company's earlier editor experiments. The question is no longer whether an editor feels light at launch; it is whether project intelligence, extensions, and remote work remain coherent later. Separate a personal trial from a team-standard decision.

### HelloGitHub issue 127
**[V2EX](https://www.v2ex.com/t/1252397)**

HelloGitHub's new issue is a useful discovery surface for projects circulating in Chinese-speaking developer communities. A list is not a selection process, but it is a good source of candidates that do not travel through the usual English-language channels. Follow it with the unglamorous checks: license, maintenance, and issue response.

### Recent E2E strategy in 2026
**[Zenn](https://zenn.dev/polyco/articles/26624b38c951b5)**

This Zenn piece revisits the current trade-offs in end-to-end testing. E2E suites should protect costly user-flow and integration failures, not mechanically repeat every unit-level assertion. Before adding tests, agree which production failures are expensive enough to deserve that coverage.

### Fix the AI explanation before shortening it
**[Zenn / Microsoft](https://zenn.dev/microsoft/articles/explain-before-shorten)**

Microsoft's piece advocates an explain-first, shorten-later workflow for AI-generated copy. The sequence transfers neatly to engineering documents: validate that the model holds the constraints before asking for brevity. Compression without that checkpoint often produces polished text with the important caveat missing.

### Bun's Prettier-compatible formatter
**[Publickey](https://www.publickey1.jp/blog/26/javascriptbunprettier300prettier.html)**

Bun announced a formatter compatible with Prettier configurations and positioned it as dramatically faster. For formatters, compatibility with a repository's existing output and editor workflow matters more than a headline timing number. Run it in non-blocking CI first and inspect the diff before migrating.

### Hallmark on GitHub Trending
**[GitHub Trending](https://github.com/Nutlope/hallmark)**

Hallmark is among today's trending repositories, representing the continued rush of generative design tooling. The practical review points are reproducibility, asset rights, and collaboration boundaries, not the first demo. Once a design generator enters a real delivery path, versioning becomes a concrete problem fast.

### Anthropic's early report on drug-development work with Claude
**[Anthropic](https://www.anthropic.com/research/early-progress-drug-development)**

Anthropic shares early work on applying Claude to drug development. The more durable lesson is not the model as a scientist, but the surrounding loop of retrieval, hypothesis generation, and expert review. That verification chain is the part worth borrowing for any high-consequence AI system.

## Editor's note

The two must-reads are the E2E strategy and the Python JIT update: both are about making engineering gains sustainable. All seven requested sources were reachable today; Anthropic's research update made the final wildcard selection.
