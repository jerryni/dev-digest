---
title: "September 26 · Today's 10 Dev Picks"
date: 2026-09-26T07:00:00+09:00
draft: false
tags: ["digest", "2026-09", "ai", "agents", "developer-tools", "security"]
categories: ["daily"]
summary: >-
  Today's thread is agents leaving the demo box: security traces, plugin directories, team dashboards, decision models, and prompt audits. The non-AI picks are just as useful: Go's SIMD experiment and git-bug both point at durable developer infrastructure.
---

## Today at a glance

The agent ecosystem is getting more operational. The interesting questions are no longer just which model is best, but how teams manage plugins, permissions, memory, costs, and upgrades. Meanwhile, Go SIMD and git-bug are good reminders that the developer stack still improves one practical layer at a time.

## Picks

### 1. OpenAI agents attacking Hugging Face, traced in detail

Source: Hacker News  
Link: https://swarmtraces.org/

This HN item walks through traces of OpenAI agents attacking Hugging Face in a security setting. The important lesson is that tool-using agents act like persistent operators: they inspect, try, fail, adapt, and keep moving. If you are deploying agents internally, permissions, sandboxing, audit logs, and kill switches are product requirements, not security garnish.

### 2. Go experiments with platform-independent SIMD

Source: Hacker News / Go Blog  
Link: https://go.dev/blog/simd-experiment

The Go team published an experiment around platform-independent SIMD. That matters because SIMD performance work is often trapped between non-portable low-level code and compiler hope. If Go can make vectorized operations safer and more idiomatic, data processing, compression, graphics, and local inference code all get a cleaner path to speed.

### 3. git-bug brings distributed issue tracking into Git

Source: Hacker News  
Link: https://github.com/git-bug/git-bug

`git-bug` is a distributed, offline-first issue tracker embedded in Git. It is not trying to beat hosted project management suites on polish; it is optimizing for portability, self-hosting, and workflows where the repository should carry more of its own project state. In a cloud-heavy era, that design still has teeth.

### 4. Ollaya brings an Ollama-like shape to Jev-style decision models

Source: Hacker News  
Link: https://ollaya.dev/

Ollaya is pitched as an Ollama-style way to run open-source Jev-like decision models. The interesting angle is narrower than chat: classification, routing, moderation, escalation, and workflow branching. A cheap, testable decision model can be more valuable than a verbose general model when the output space is intentionally small.

### 5. GitHub Trending: paperclip for managing workplace agents

Source: GitHub Trending  
Link: https://github.com/paperclipai/paperclip

`paperclipai/paperclip` is trending as an open-source app for managing agents at work. That category is going to matter as teams accumulate coding agents, research agents, scheduled automations, and plugins across projects. The missing layer is not another chat box; it is visibility, ownership, permissions, run state, and history.

### 6. GitHub Trending: Anthropic's official Claude Code Plugins directory

Source: GitHub Trending  
Link: https://github.com/anthropics/claude-plugins-official

Anthropic's official Claude Code Plugins directory is also trending today. A plugin ecosystem makes agents more useful, but it also introduces supply-chain questions: who maintains the plugin, what can it access, how is it updated, and how do teams roll it back? Enterprises should treat agent plugins more like extensions with privileges than snippets.

### 7. V2EX notices the gap between Muse registration and real usage

Source: V2EX  
Link: https://www.v2ex.com/t/1244766

V2EX had several Muse threads today, and this one captures the useful signal: people see plenty of registration guides, but fewer practical usage reports. That is a common phase for new AI tools, where access mechanics dominate before workflows mature. The retention test is what users do on day two.

### 8. V2EX debates whether an indie developer needs Claude Max

Source: V2EX  
Link: https://www.v2ex.com/t/1244814

This thread asks whether an indie developer with no product revenue should pay for Claude Max. It is a grounded question: AI subscriptions are now part of the developer cost stack, and the ROI depends on task mix, usage frequency, and whether the tool actually ships features faster. For solo builders, the best model is not always the best monthly bill.

### 9. Zenn experiments with Jev, distillation, and game tasks

Source: Zenn  
Link: https://zenn.dev/nwn/articles/e49154653ecea9

Zenn's Jev experiment is useful because it treats decision models as a distinct tool, not a mini chat model. Smaller, cheaper, narrower models can be easier to validate when the job is classification or control flow. Expect more teams to split AI workloads into generative steps and decision steps instead of sending everything to one general-purpose model.

### 10. Zenn audits prompt settings after moving to Claude Opus 5.5

Source: Zenn  
Link: https://zenn.dev/nanora/articles/20260925-claude-prompt-audit-opus55

This Zenn post audits prompt settings after a move to Claude Opus 5.5. Model upgrades are dependency upgrades: prompts, temperatures, tool descriptions, and default reasoning behavior can all drift out of tune. Teams with production AI workflows need migration checklists, not just model-name swaps.

## Editor's note

Today's 10 picks break down as HN 4, GitHub Trending 2, V2EX 2, and Zenn 2. Simon Willison, Publickey, and Anthropic News were reachable; Simon's latest Muse safety item overlapped with today's Muse discussion, Publickey had no fresh article within the 24-hour window, and Anthropic News did not surface a new developer-focused item that had not already been covered. The Dev Digest editor would start with the agent security trace, Go SIMD, and the Claude Plugins directory.
