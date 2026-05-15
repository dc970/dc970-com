---
title: "April Meeting Recap — Malware Analysis Workshop"
date: 2026-04-17
category: meeting
---

Thanks to everyone who came out for April's meeting. We had a great turnout for the malware analysis workshop — roughly 20 attendees working through live samples in an isolated lab environment.

## What We Covered

The evening kicked off with a quick primer on static analysis tools: `strings`, `file`, `pestudio`, and DIE (Detect It Easy). From there we moved into dynamic analysis using a Windows 10 sandbox VM, watching a commodity RAT beacon out in real time.

A few highlights from the group:

- Someone identified a XOR-encoded C2 config buried in a PE resource section — solid catch
- Good discussion on how modern loaders abuse legitimate Windows APIs to avoid behavioral detection
- The Q&A on YARA rule writing ran long (in a good way)

## Resources Shared

Slide deck and sample hashes (VirusTotal links only — no live malware distributed) are posted in the Discord `#resources` channel.

## Next Month

May's meeting topic is TBD — drop suggestions in `#meeting-ideas` on Discord.
