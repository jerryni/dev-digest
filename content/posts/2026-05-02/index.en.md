---
title: "May 2 · Today's 10 Dev Picks"
date: 2026-05-02T07:00:00+09:00
draft: false
tags: ["digest", "2026-05", "VSCode", "Copilot", "NetHack", "Ladybird", "Ask"]
categories: ["daily"]
summary: "VSCode auto-injects 'Co-Authored-by: Copilot' into commits whether or not you used Copilot (1500+ comments), VideoLAN's dav2d ships an open AV2 decoder, NetHack 5.0 finally lands, Ladybird posts April progress, Ask.com shuts down, Russia Poisons Wikipedia."
---

## Today at a glance

The big story is Microsoft's VSCode auto-injecting "Co-Authored-by: Copilot" into commits regardless of whether Copilot was used — 1,500+ comments, near-unanimous outrage. Beside that, a strikingly OSS-heavy day: VideoLAN's dav2d (open AV2 decoder), NetHack 5.0 (35+ years and still shipping), Ladybird's monthly progress (the only credible non-Chromium/Firefox/WebKit browser project). Russia Poisons Wikipedia is a longer read worth your evening.

---

## 1. VSCode auto-attributes commits to Copilot whether or not you used it

Tag: [EN · HN Top]
Link: <https://github.com/microsoft/vscode/pull/310226>

The PR injects "Co-Authored-by: Copilot" into commits even when Copilot is disabled. 1500+ HN comments are overwhelmingly hostile. The legal angle is real: under strong-copyleft licenses like GPL, ambiguous authorship can become a compliance issue. If your team uses VSCode against any repository where authorship cleanliness matters, audit your commit template now.

## 2. dav2d — open AV2 decoder

Tag: [EN · HN Top]
Link: <https://code.videolan.org/videolan/dav2d>

VideoLAN's open-source AV2 decoder, the spiritual successor to dav1d. Codec generations matter for streaming, broadcast, and bandwidth-constrained applications. If you ship video at any scale, this is on the radar list for 2026.

## 3. Do_not_track

Tag: [EN · HN Top]
Link: <https://donottrack.sh/>

Open-source CLI tool that automates cookie/consent rejection and third-party tracking opt-outs. Niche but elegant.

## 4. NetHack 5.0.0

Tag: [EN · HN Top]
Link: <https://nethack.org/v500/release.html>

The 35+ year old roguelike ships a major release. Honestly worth a moment of appreciation for what community-maintained software can sustain. Also a useful reference point for what *not* to expect from venture-backed dev tools at 5-year horizons.

## 5. Ladybird browser — April 2026 progress

Tag: [EN · HN Top]
Link: <https://ladybird.org/newsletter/2026-04-30/>

The most credible attempt at a non-Chromium / non-Gecko / non-WebKit browser engine in years. Targeting alpha by end of 2026. The structural relevance is the question of whether the Web platform can have meaningful third-party implementations at all anymore.

## 6. Ask.com has closed

Tag: [EN · HN Top]
Link: <https://www.ask.com/>

The 90s search engine quietly shuts down. End of an era; HN comments are nostalgic.

## 7. Russia Poisons Wikipedia

Tag: [EN · HN Top]
Link: <https://www.bettedangerous.com/p/russia-poisons-wikipedia>

Investigative writeup of organized Russian editing campaigns on Wikipedia. The structural question — what's the integrity of "neutral information sources" when they're contested at scale — applies far beyond Wikipedia, including to anything you build that grounds AI on web content.

## 8. How fast is a macOS VM, and how small could it be?

Tag: [EN · HN]
Link: <https://eclecticlight.co/2026/05/02/how-fast-is-a-macos-vm-and-how-small-could-it-be/>

Empirical benchmarks of macOS virtualization on Apple Silicon. If you run iOS CI/CD at any volume, this directly informs your build-farm cost model.

## 9. California to begin ticketing driverless cars

Tag: [EN · HN]
Link: <https://www.bbc.com/news/articles/clypjx3rg2go>

Tickets get sent to the manufacturer. The interesting part is the doctrinal shift — autonomous vehicle accountability moving from theoretical to operational at the state level — which will be cited in every other state and country trying to figure this out.

## 10. Six years perfecting maps on watchOS

Tag: [EN · HN]
Link: <https://www.david-smith.org/blog/2026/04/29/maps-on-watchos/>

Independent developer David Smith on six years of iterating on a watchOS Maps experience. Long-tail platform craft, the kind that doesn't make it into product announcements but is what users actually experience day to day.

---

## Editor's note

Read #1 first — every team running VSCode against a repository needs to know about it today. #5 (Ladybird) is the long-horizon platform-diversity story worth tracking. The NetHack/dav2d/Ladybird trio is a pleasant reminder that healthy OSS hasn't stopped existing, it just stopped being the loudest voice in the room.
