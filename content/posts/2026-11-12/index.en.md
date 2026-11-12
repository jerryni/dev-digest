---
title: "November 12 · Today's 10 Dev Picks"
date: 2026-11-12T07:00:00+09:00
draft: false
tags: ["digest", "2026-11", "agents", "testing", "infrastructure"]
categories: ["daily"]
summary: "Today's signal is operational: agents, test runners, and infrastructure all need explicit boundaries."
---

# November 12 · Today's 10 Dev Picks

## Today at a glance

The interesting stories today are less about a single capability jump than about making powerful systems survivable in production. Agent tooling is getting easier to adopt, while incidents and sandboxing remind us that isolation, observability, and ownership are still the real work.

## Picks

### 1. [AWS Emulator](https://github.com/aws/aws-emulator)
`Hacker News · Cloud tooling`

AWS Emulator is a Rust and Docker-based local emulator for AWS services, with a focus on agent-driven development and testing. Local cloud doubles are useful when they make tests deterministic and cheap, but their value depends on clearly documenting what they do not emulate. Keep a small set of integration tests against the real service; that boundary is where IAM, timing, and billing surprises live.

### 2. [A false smoke alarm nearly drowned Jane Street's NYC datacenter](https://michael.bacarella.com/2026/11/10/false-smoke-alarm-jane-street-datacenter/)
`Hacker News · Incident analysis`

An incident report on a false alarm and a datacenter flood is a sharp reminder that physical failure modes remain software reliability problems. The useful lesson is not simply redundancy, but rehearsing the awkward handoffs between facilities systems, responders, and operators. Incident reviews should cover the sensors and runbooks around a service, not just its code path.

### 3. [Gemini Decisions API](https://simonwillison.net/2026/Nov/11/gemini-decisions-api/)
`Simon Willison · AI APIs`

Simon Willison highlights Google's Decisions API, aimed at structured decision tasks. A structured interface can reduce the amount of fragile parsing around a model, but it does not remove the need to validate inputs, outputs, and escalation paths. Treat the decision record as an audit artifact rather than an opaque answer.

### 4. [agent-browser on GitHub Trending](https://github.com/vercel-labs/agent-browser)
`GitHub Trending · Agent tooling`

agent-browser exposes browser automation through a CLI for AI agents. That is compelling because it can work with real browser state, and risky for exactly the same reason. Start with isolated accounts, explicit domain allowlists, and logs that make every consequential navigation reproducible.

### 5. [Two 16 GB Mac minis or one 32 GB Mac mini?](https://www.v2ex.com/t/1256326)
`V2EX · Developer community`

This V2EX discussion is a practical hardware-planning question with a familiar answer: capacity is not interchangeable with aggregate capacity when the workload has a single memory-hungry process. For local models, builds, and containers, measure peak working sets before spreading tasks across machines. A second box can improve throughput; it cannot rescue a process that will not fit.

### 6. [Reverse-engineering an automated workflow for Magpie](https://www.v2ex.com/t/1256327)
`V2EX · Developer community`

A community thread asks how the author yetone's automated Magpie workflow is assembled. The important engineering instinct is to study the workflow as a system: trigger, context capture, action, and verification. Copying a visible prompt without those boundaries usually copies only the least reliable part.

### 7. [ISUCON 2026 solo run with a near-unattended Claude Code harness](https://zenn.dev/5alt_nacl/articles/isucon2026-solo-ai-agent)
`Zenn · AI-assisted development`

This competition write-up describes using a custom harness to keep Claude Code moving through a solo ISUCON entry. The interesting part is the harness, not the claim of unattended operation: it turns an agent into a loop with constraints and feedback. Teams experimenting with this pattern should make the stop conditions and benchmark checks first-class artifacts.

### 8. [Using Bedrock AgentCore Gateway Web Search from Claude Desktop](https://zenn.dev/aws_japan/articles/agentcore-gateway-websearch-cognito)
`Zenn · Cloud integration`

AWS Japan walks through wiring AgentCore Gateway web search into Claude Desktop with Cognito. It is a useful example of agent capability becoming ordinary integration work: identity, delegated permissions, and request scope matter more than the demo. Keep gateway policies narrow and test the denied cases as carefully as the happy path.

### 9. [Playwright officially supports Bun](https://www.publickey1.jp/blog/26/playwrightbun.html)
`Publickey · Testing`

Publickey reports that Playwright 1.65.0 officially supports running its test runner on Bun. That can be attractive to teams standardizing on Bun's TypeScript toolchain, but browser-test stability still depends on browser binaries, CI images, and retry discipline. Benchmark startup time and run the existing suite before swapping runners in a shared pipeline.

### 10. [AWS launches Nitro Sandboxes for AI agents](https://www.publickey1.jp/blog/26/awsaiec2vmaws_nitro_sandboxes.html)
`Publickey · Cloud security`

AWS Nitro Sandboxes packages stronger isolation with native EC2 performance for agent workloads. This makes the security boundary more concrete, but it does not decide what the agent is allowed to reach or retain. Pair sandboxing with least-privilege credentials, egress controls, and a short-lived data policy.

## Editor's note

Read the Jane Street incident next to Nitro Sandboxes: both are about the boundaries that let a complex system fail without becoming a catastrophe. Anthropic's newsroom was reachable today but did not surface a new same-day technical announcement, so its wildcard slot went to the operationally stronger infrastructure stories.
