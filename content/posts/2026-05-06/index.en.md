---
title: "May 6 · Today's 10 Dev Picks"
date: 2026-05-06T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "AI", "Cloudflare", "Anthropic", "AWS", "Steam"]
categories: ["daily"]
summary: "Cloudflare lets agents create accounts, buy domains, and deploy on their own; Anthropic raises Claude limits and signs a SpaceX compute deal; Valve open-sources Steam Controller CADs under CC; AWS Middle East UAE region still months from full recovery."
---

## Today at a glance

The thread today: agents are no longer features bolted onto your platform — they're a first-class principal. Cloudflare gave agents the ability to register accounts, buy domains, charge a Stripe card, and deploy. Anthropic raised Claude usage limits and announced a major SpaceX compute partnership in the same breath. Valve, in a rare burst of hardware generosity, open-sourced Steam Controller CADs under Creative Commons. The hard infra story is still AWS's Middle East UAE region: months more before recovery.

---

## 1. Cloudflare: agents can now create accounts, buy domains, and deploy

Tag: [EN · Cloudflare Blog]
Link: <https://blog.cloudflare.com/agents-stripe-projects/>

The end-to-end loop is the actual news. Give an agent a budget; it registers a Cloudflare account, buys a domain, charges a Stripe card you own, and ships a service. This is the first hyperscaler making "agent as paying customer" a documented product surface rather than a hackathon demo. Worth reading for the trust-and-safety implications alone — what happens when an agent buys a domain it shouldn't?

## 2. Higher usage limits for Claude and a compute deal with SpaceX

Tag: [EN · Anthropic]
Link: <https://www.anthropic.com/news/higher-limits-spacex>

Anthropic raised user-facing rate limits and announced an expanded compute partnership with SpaceX. The latter is significant: SpaceX has been quietly building out terrestrial AI data centers, and this contract confirms they're competing with the existing hyperscalers as Anthropic's compute supplier. Practical takeaway for engineers: rate-limit anxiety on Claude API should ease for the next quarter or two.

## 3. Valve releases Steam Controller CAD files under Creative Commons

Tag: [EN · HN Top]
Link: <https://www.digitalfoundry.net/news/2026/05/valve-releases-steam-controller-cad-files-under-creative-commons-license>

Valve open-sourced the 3D CAD files for the discontinued Steam Controller. Maker community wins. The original Steam Controller had genuinely novel input ideas — capacitive trackpads, dual haptics — that never got proper second-generation iteration. Hopefully someone forks it well.

## 4. Red Squares — GitHub outages as contributions

Tag: [EN · HN]
Link: <https://red-squares.cian.lol/>

A developer rendered GitHub's outage history as red squares overlaid on a contribution graph. Funny, but the data is sobering: 2026 GitHub has nearly weekly incidents. Pair with #5 from yesterday's "GitHub incident with Issues and Webhooks" — these are not isolated.

## 5. V2EX debate: Podman or Docker in 2026

Tag: [ZH · V2EX]
Link: <https://www.v2ex.com/t/1208359>

The Chinese dev community keeps relitigating the container runtime question. Consensus is the same as on this side of the firewall: greenfield → Podman, existing Docker setups → leave alone. Useful as a sanity check that the runtime conversation has converged globally.

## 6. V2EX: still wasting half a day on CORS in 2026

Tag: [ZH · V2EX]
Link: <https://www.v2ex.com/t/1207904>

The recurring CORS-as-time-sink thread, with a high-quality top reply outlining a debugging checklist that's actually useful. The deeper observation is the unchanged one: CORS pain is rarely about the protocol, it's about ambiguous ownership across API gateway / Nginx / CDN.

## 7. AWS Middle East (UAE) region: months more before full recovery

Tag: [JA · Publickey]
Link: <https://www.publickey1.jp/blog/26/awsuae2.html>

ME-CENTRAL-1 took physical-layer damage from regional conflict; AWS broke a two-month silence to confirm full restoration is still months away. This is unprecedented in scale and duration for a hyperscaler. If you have prod in UAE, your DR runbook needs an update this week — realistic options are ME-SOUTH-1 (Bahrain) or EU-WEST-1.

## 8. Cloudflare Artifacts — git-compatible filesystem for agents

Tag: [JA · Publickey]
Link: <https://www.publickey1.jp/blog/26/cloudflareaicloudflare_artifactsgitrestful_api.html>

The other half of #1's story. Git-compatible versioned storage exposed via REST, designed for agents that need persistent file state across runs. If you've been wiring up S3+vector-store as the default agent persistence stack, this is worth a look — different shape, different tradeoffs.

## 9. Telus uses AI to alter call-center agent accents

Tag: [EN · HN]
Link: <https://letsdatascience.com/news/telus-uses-ai-to-alter-call-agent-accents-a3868f63>

Canadian telco Telus is running offshore call-center agents through a real-time AI accent shifter. HN comments are nearly unanimous: this is the cynical use case. The ethical line — augmentation versus erasure — is going to come up everywhere AI touches customer-facing humans, and the answer is going to define which products people are proud to ship.

## 10. BYD overtakes Tesla and Kia in key overseas markets

Tag: [EN · HN]
Link: <https://electrek.co/2026/05/05/byd-overtakes-tesla-kia-best-selling-ev-brand-key-overseas-markets/>

BYD now leads Tesla and Kia in EV sales across multiple non-China markets in Europe, Southeast Asia, and Latin America. The interesting story isn't the unit count — it's how fast BYD localized service, financing, and charging in each market. A reference case for any hardware-first company thinking about international expansion.

---

## Editor's note

If you only read two: #1 (Cloudflare agents end-to-end) and #2 (Anthropic + SpaceX). They're the same story told from two angles — agents are now part of the infrastructure planning surface, not just an SDK call. The operational item to escalate today is #7 if your team has anything running in AWS UAE.
