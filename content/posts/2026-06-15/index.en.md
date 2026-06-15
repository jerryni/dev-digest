---
title: "June 15 · Today's 10 Dev Picks"
date: 2026-06-15T07:00:00+09:00
draft: false
tags: ["digest", "2026-06", "ai", "agents", "security", "webassembly", "postgres", "rag"]
categories: ["daily"]
summary: "Today is about agent-era engineering: securing reusable skills, rethinking IDE-centered workflows, making RAG more structural, treating deletes as lifecycle design, and pushing WASI forward as a safer execution substrate."
---

## Today at a glance

The interesting thread today is not a single model release. It is the infrastructure around autonomous development: skills need scanning, IDE workflows are being decomposed, RAG systems are getting more structure, and runtime isolation keeps getting more important. V2EX was reachable, but its hot page had no strong developer item today, so the list leans English and Japanese.

---

### 1. Kage packages a website into one offline binary — `[Hacker News · Show HN]`
<https://github.com/tamnd/kage>

Kage snapshots a website into a single binary for offline viewing. That sounds small, but it is useful for docs archiving, field demos, air-gapped environments, and reproducible references for internal systems. The value is less about scraping and more about making a web surface portable without a messy directory of assets.

### 2. Jane Street on formal methods and the future of programming — `[Hacker News]`
<https://blog.janestreet.com/formal-methods-at-jane-street-index/?from_theconsensus=1>

Formal methods are getting more relevant, not less, as AI writes more code. Specifications, types, model checking, and property tests give generated code something firmer to satisfy than a reviewer’s intuition. This is the kind of engineering discipline teams should revisit before giving agents broader write access.

### 3. PlanetScale argues the only scalable delete in Postgres is DROP TABLE — `[Hacker News]`
<https://planetscale.com/blog/the-only-scalable-delete>

Large deletes in Postgres stress indexes, WAL, autovacuum, and replication. The article’s practical lesson is to model retention as table or partition lifecycle, then drop whole units when they age out. For logs, events, metrics, and audit trails, the deletion strategy should be part of the schema design, not an emergency cleanup job.

### 4. NVIDIA SkillSpector scans AI agent skills — `[GitHub Trending]`
<https://github.com/NVIDIA/SkillSpector>

SkillSpector targets a new software supply-chain surface: reusable agent skills. It looks for malicious patterns, risky permissions, and security issues in skill packages. If teams are going to copy skills from public repos into agents that can read files, run tools, or touch credentials, they need scanners and review gates just like they do for dependencies.

### 5. Simon Willison: why AI has not replaced software engineers — `[Simon Willison]`
<https://simonwillison.net/2026/Jun/14/why-ai-hasnt-replaced-software-engineers/>

Simon highlights Arvind Narayanan and Sayash Kapoor’s argument that coding is not the only bottleneck in software engineering. Deciding what to build, verifying the result, and understanding the business and codebase context still dominate the hard parts. The piece is a useful antidote to simplistic headcount-replacement narratives.

### 6. WASI 0.3 reaches stable status — `[Publickey]`
<https://www.publickey1.jp/blog/26/wasi_03webassembly_component.html>

WASI 0.3 brings stable async support to the WebAssembly Component Model. That matters for server-side WASM, plugin systems, edge runtimes, and sandboxed execution. As agents increasingly need to run untrusted or semi-trusted code, standardized isolation layers become part of the developer platform story.

### 7. Gartner predicts many coding-agent teams will stop treating IDEs as essential — `[Publickey]`
<https://www.publickey1.jp/blog/26/2027ai65ide.html>

The exact percentage is less important than the direction: coding agents are moving beyond editor plugins into issues, PRs, CLIs, queues, and browser workflows. IDEs will remain useful, but they may no longer be the only place where software work happens. Teams should focus on ownership, review gates, credentials, and audit trails rather than just choosing the smartest extension.

### 8. PageIndex explores reasoning-based RAG — `[Zenn]`
<https://zenn.dev/snaga/articles/2026-06-14-doctools-with-pageindex>

PageIndex treats documents as structured trees and uses dense LLM summaries as navigational keys. That shifts RAG from pure similarity search toward structured reasoning over long, messy enterprise material such as PDFs, slide decks, and spreadsheets. It is a good read for teams whose RAG systems retrieve plausible chunks but miss the actual path through a document.

### 9. OpenCode Go as a Copilot Chat custom provider — `[Zenn]`
<https://zenn.dev/kusuke/articles/82129236caa5f8>

After GitHub Copilot’s pricing changes, this Zenn post walks through using OpenCode Go as a VS Code Copilot Chat custom endpoint. The specific setup may be niche, but the broader pattern is important: developers are separating model access, IDE integration, and monthly cost. Predictable spend is becoming a product feature for coding assistants.

### 10. Anthropic’s statement on Fable 5 and Mythos 5 access — `[Anthropic]`
<https://www.anthropic.com/news/fable-mythos-access>

Anthropic says it must suspend access to Fable 5 and Mythos 5 under a US government directive, while other models are unaffected. Whatever your view of the policy issue, it is a reminder that frontier-model availability is not just a technical variable. Production systems should have fallback models, vendor-risk notes, and a clear plan for sudden capability loss.

---

## Editor's note

Today’s 10 picks break down as EN 5, JA 4, and one official Anthropic item. V2EX was reachable, but the hot page was mostly ads or weakly technical posts, so Dev Digest editor did not force a Chinese-source slot. Start with **SkillSpector** and **WASI 0.3**: one covers the near-term risk of agent skills, the other points at the runtime substrate those agents will need.

— Dev Digest editor
