---
title: "October 23 · Today's 10 Dev Picks"
date: 2026-10-23T07:00:00+09:00
draft: false
tags: ["digest", "2026-10", "security", "agents", "developer-tools"]
categories: ["daily"]
summary: "DNS jurisdiction, agent runtimes, and formal verification all make one point: engineering boundaries need explicit ownership."
---

# October 23 · Today's 10 Dev Picks

## Today at a glance

The connective tissue today is boundaries. A public DNS resolver is constrained by jurisdiction, autonomous agents need enforceable execution limits, and formal methods give model-assisted work a deterministic referee. The PHP aftermath is the practical counterpoint: security still begins with knowing what you run.

## Picks

### 1. Quad9 will leave France [HN]

[Read the announcement](https://quad9.net/news/blog/au-revoir-france/)

Quad9 says it will stop serving France because of the legal environment. Resolver location, logging policy, and failover are infrastructure choices with regulatory consequences, not invisible defaults. Teams serving multiple regions should know which resolver assumptions are embedded in their platforms and incident plans.

### 2. OpenShell for fleets of autonomous agents [HN]

[View the project](https://github.com/NVIDIA/OpenShell)

NVIDIA's OpenShell proposes a private runtime for autonomous-agent fleets. The meaningful evaluation is not another agent demo; it is whether permissions, isolation, egress, and audit trails form one operable system. Before production access, make the stop button and human-handoff path boringly reliable.

### 3. Cloudflare's security-audit skill [GitHub Trending]

[View the repository](https://github.com/cloudflare/security-audit-skill)

Cloudflare published a multi-phase security-audit skill for coding agents, with an emphasis on independently verifiable and machine-readable findings. That output becomes useful only when it enters an existing reproduce, triage, and review loop. 'Audited by an agent' is not a control; evidence that a reviewer can re-run may be.

### 4. Arc browser's planned retirement [V2EX]

[Read the discussion](https://www.v2ex.com/t/1251107)

A V2EX thread discusses Arc's planned retirement on December 22. Browser replacements have a hidden migration surface: spaces, extensions, bookmarks, authentication state, and personal workflows. Tool exits are a good prompt to document the habits that a UI had quietly been carrying.

### 5. Is programming a young person's job? [V2EX]

[Read the discussion](https://www.v2ex.com/t/1251106)

This discussion pushes back on treating programming as disposable manual work. As agent tooling makes routine implementation cheaper, problem framing, validation, and system trade-offs become more visible differentiators. The durable response is to turn experience into review heuristics and operational practice, not just chase the next assistant.

### 6. A PHP-vulnerability first-response flowchart [Zenn]

[Read the article](https://zenn.dev/mimi/articles/0a158119a3b501)

This Zenn article lays out the first decisions a maintainer should make after PHP vulnerability news lands. Its value is sequencing: identify affected versions, exposure paths, and ownership before applying a hurried configuration change. For estates with multiple images and vendors, an impact inventory is usually the safest first artifact.

### 7. Learning SELinux through rootless Docker [Zenn]

[Read the article](https://zenn.dev/nexryai/articles/afb828d7dda6b7)

An introductory look at SELinux through rootless Docker. Tightening container privilege is a systems problem spanning user namespaces, mounts, networking, and host policy. When something fails, understanding the denial beats adding a broad exception that erases the boundary you intended to create.

### 8. LLMs and formal software verification at larger scale [Anthropic]

[Read the research](https://www.anthropic.com/research/formal-verification)

Anthropic describes using LLMs to make formal verification feasible across larger software tasks. The key distinction is that the model proposes while a verifier decides. For high-assurance code, generating checkable proof candidates may be a more controllable near-term use than treating generated patches as inherently trustworthy.

### 9. Agent skills donated to the Agentic AI Foundation [Anthropic]

[Read the announcement](https://www.anthropic.com/news/donating-agent-skills-to-the-agentic-ai-foundation)

Anthropic is donating agent skills to the Agentic AI Foundation. Shared descriptions, permission boundaries, and portable tests could reduce workflow lock-in. But portability is not safety: every skill still needs explicit inputs, tool authority, and data-egress behavior.

### 10. An expanded Cyber Verification Program [Anthropic]

[Read the announcement](https://www.anthropic.com/news/cyber-verification-program)

Anthropic expanded its Cyber Verification Program for qualifying security professionals. More capable testing access raises the bar for authorization, scope definition, and evidence retention. Red-team velocity is only useful when the asset owner and operational responders are part of the loop.

## Editor's note

Start with OpenShell and the formal-verification research: both focus on making AI-assisted work governable rather than merely capable. GitHub Trending, V2EX, Zenn, and Anthropic supplied usable items today. Simon Willison and Publickey were reachable, but neither produced a sufficiently fresh, high-priority pick for this edition.
