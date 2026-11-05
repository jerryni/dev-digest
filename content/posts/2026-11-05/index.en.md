---
title: "November 5 · Today's 10 Dev Picks"
date: 2026-11-05T07:00:00+09:00
draft: false
tags: ["digest", "2026-11", "ai", "opensource", "developer-tools"]
categories: ["daily"]
summary: "A practical reading list on JSON APIs, agent interfaces, recoverability, and the controls around generated work."
---

# November 5 · Today's 10 Dev Picks

## Today at a glance

The interesting work today is not just more capable models. It is the engineering around them: inspectable data-app workflows, generated-code sandboxes, memory governance, and recovery paths when normal infrastructure fails.

## Picks

### 1. [A new Go API for JSON](https://go.dev/blog/jsonv2)
`HN · Go`

The Go team introduces a new JSON API aimed at more predictable behavior and a cleaner path for future capabilities. For production services, the practical question is migration: identify boundary cases, run old and new encoders side by side, and treat compatibility as a release concern rather than a refactor detail.

### 2. [NVIDIA auto-ontology](https://github.com/NVIDIA/auto-ontology)
`GitHub Trending · Open source`

NVIDIA's auto-ontology is trending as an attempt to automate parts of ontology creation and maintenance. Knowledge systems usually fail at model drift and review, not at embedding calls; a useful evaluation should include provenance, human approval, and diffs for generated concepts.

### 3. [Datasette Agent 0.5a0](https://simonwillison.net/2026/Nov/3/datasette-agent/)
`Simon Willison · AI tools`

Datasette Agent adds a panel that keeps agent chat beside a data table or query page, including support for creating and editing data-backed apps. That layout matters: it keeps the artifact and the evidence in one workspace instead of burying both in a conversation transcript.

### 4. [A native SSH, SFTP, and AI client](https://www.v2ex.com/t/1254583)
`V2EX · Developer tools`

This community launch combines SSH, SFTP, and AI features in a native client for three platforms. Remote-admin tooling lives or dies on credential handling, reconnect behavior, and session portability, so those mundane edges deserve more scrutiny than an impressive feature list.

### 5. [Recovering files after a Synology NAS ransomware incident](https://www.v2ex.com/t/1254586)
`V2EX · Storage security`

A V2EX thread documents an attempt to recover files from SSD cache after a NAS ransomware incident. It is not a universal recovery recipe, but it is a sharp reminder that a backup is only real when restoration has been tested, ideally without depending on the compromised box.

### 6. [EasyEEG, an agent-assisted EEG workflow](https://zenn.dev/hackathons/google-cloud-japan-ai-hackathon-vol5/projects/bf62c6a94633a5)
`Zenn · Agentic AI`

EasyEEG applies agents to research planning, electrode preparation, signal observation, and analysis. Its notable choice is to foreground consent, safety controls, and minimal retention; in research-adjacent systems, those controls are features, not legal footnotes.

### 7. [Hachi Atelier: from plant photos to printable STL](https://zenn.dev/katsunori04/articles/a3fb70431bbb1c)
`Zenn · Generative manufacturing`

Hachi Atelier turns a plant photo into a printable pot design and uses an isolated sandbox for generated code. The design loop—generate, inspect geometry, compare, repair—is the useful pattern here. Physical outputs need measurable acceptance checks, not aesthetic confidence from a model.

### 8. [Octoverse 2026: TypeScript remains the most-used language](https://www.publickey1.jp/blog/26/github2typescriptrustosscc_switchomarchygithub_octoverse_2026.html)
`Publickey · Open source`

Publickey's Octoverse summary says TypeScript held the top spot for a second year, while Rust showed strong pull-request growth. Rankings do not make architecture decisions, but they affect hiring pools, libraries, and the maintenance surface of a stack—real inputs to platform planning.

### 9. [GitHub Copilot Dreaming](https://www.publickey1.jp/blog/26/github_copilot_dreaminggithub_universe_2026.html)
`Publickey · GitHub Universe`

Copilot Dreaming proposes background organization of a developer's activity into personal memory and guidance. The compelling implementation questions are governance questions: what gets retained, how stale conclusions are corrected, and how personal context is kept distinct from company knowledge.

### 10. [Kimi K3.1 Pro model weights](https://huggingface.co/moonshotai/Kimi-K3.1-Pro)
`HN · Open models`

The Kimi K3.1 Pro weights are available for teams that want to evaluate an open model on their own hardware and workloads. A credible test plan should cover license terms, inference stack maturity, memory footprint, tool-call reliability, and adaptation options—not just a leaderboard score.

## Editor's note

Today's through-line is controlled capability: expose the context, sandbox the generated action, and make recovery possible. Start with the Go JSON proposal and Datasette Agent for two very different examples of that discipline. Anthropic's newsroom had no confirmable technical post from the past 24 hours, so older news was not used as filler.
