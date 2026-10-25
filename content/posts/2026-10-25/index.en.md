---
title: "October 25 · Today's 8 Dev Picks"
date: 2026-10-25T07:00:00+09:00
draft: false
tags: ["digest", "2026-10", "security", "languages", "agents"]
categories: ["daily"]
summary: "An HTTP/2 supply-chain warning, a no-heap language, and practical boundaries for agent workflows."
---

# October 25 · Today's 8 Dev Picks

## Today at a glance

Today is less about shiny capability claims than operational boundaries. Whether the system is an HTTP dependency, a programming language, or an agent workflow, the durable questions are the same: what can it touch, how do we observe it, and how do we recover?

## Picks

### 1. Goose, a memory-safe language with no heap [HN]

[Read the project](https://aardappel.github.io/goose/)

Goose proposes a systems-language model built around data stacks, inline dynamic values, and static safety checks instead of a heap allocator, GC, or lifetime annotations. Its reported benchmarks are striking, but the more useful reading is the contract: some containers give up random access, and closures and dynamic dispatch are deliberately constrained. That makes it a crisp case study in where performance claims actually get their budget.

### 2. HTTP2Shell turns patching into inventory work [HN]

[Read the report](https://www.aikido.dev/blog/python-packages-vulnerable-node2shell-brotli-cve-2026-111497)

The Node2Shell-to-HTTP2Shell warning is a reminder that network libraries are often buried beneath frameworks, base images, and transitive dependencies. Start by mapping internet-facing services to their real HTTP stacks before racing to change a lockfile. A safe response includes staged rollout signals and a rollback path, not just a version bump.

### 3. Twelve years of distributed SQLite [HN]

[Read the retrospective](https://philipotoole.com/twelve-years-of-distributed-sqlite/)

This long-view account of distributed SQLite is a useful antidote to the idea that a smaller database makes distributed concerns disappear. Replication, consistency, and incident response remain; the question is whether they live in places operators can understand and inspect. It is particularly relevant for teams weighing edge persistence or embedded replication.

### 4. Kimi K3.1 Pro meets real usage limits [V2EX]

[Read the discussion](https://www.v2ex.com/t/1251425)

The V2EX thread focuses on Kimi K3.1 Pro's speed and how quickly a usage allowance can be consumed. That is closer to an engineering procurement question than a leaderboard: context size, concurrency, retry behavior, and regional availability all shape useful cost. Measure completed workflows per budget unit, not just tokens per minute.

### 5. What should a personal agent actually do? [V2EX]

[Read the discussion](https://www.v2ex.com/t/1251415)

Developers are comparing practical uses for personal agents and scheduled automations. The strongest starting point is boring on purpose: read-oriented tasks with reviewable results and low consequence if they fail. Expanding authority after notification and reversal paths are clear produces a far more reliable assistant.

### 6. prpr, a parser generator for Rust [Zenn]

[Read the article](https://zenn.dev/tanakh/articles/prpr-packrat-parser)

This Zenn post introduces prpr, a compact, fast parser generator for Rust. Parser tooling earns adoption through diagnostics and debuggability as much as raw throughput; users need to locate a malformed construct, not merely learn that parsing failed. It is a useful candidate to compare when maintaining a DSL, a config language, or code-analysis tooling.

### 7. Making vulnerability management continuous [Zenn]

[Read the article](https://zenn.dev/dress_code/articles/be5550254695cd)

The article describes building a vulnerability-management mechanism instead of relying on one-off incident heroics. Ownership, remediation SLAs, exceptions, and accepted risk need durable records if prioritization is to survive staff and vendor changes. That operational data model matters as much as the scanner producing the alerts.

### 8. Anthropic donates Agent Skills to a foundation [Anthropic]

[Read the announcement](https://www.anthropic.com/news/donating-agent-skills-to-the-agentic-ai-foundation)

Anthropic says it is donating Agent Skills, a way to express specialized agent knowledge and workflows, to the Agentic AI Foundation. Standardization is only one part of the practical story: teams need portable records of permissions, provenance, versions, and review decisions too. Treating skills like dependencies is a sensible default for any organization that distributes them internally.

## Editor's note

Start with HTTP2Shell and Goose: one makes a supply-chain boundary concrete, while the other shows how a language can trade flexibility for verifiability. The source mix is HN 3, V2EX 2, Zenn 2, and Anthropic 1. GitHub Trending did not parse reliably, and Simon Willison, Publickey, and Anthropic had no additional verifiable fresh technical item, so this edition stops at eight rather than padding the list.
