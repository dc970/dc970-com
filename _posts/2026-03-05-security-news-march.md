---
title: "Security News — March 2026"
date: 2026-03-05
category: news
---

A roundup of notable security news and research from the past few weeks.

## Critical Vulnerabilities

**CVE-2026-1337 — OpenSSH Pre-Auth RCE**
A pre-authentication remote code execution bug in OpenSSH's server-side key exchange handling. Affects versions prior to 9.8p2. Patch immediately — this is being actively exploited in the wild against internet-exposed SSH servers. Shodan shows millions of potentially vulnerable hosts.

**CVE-2026-0891 — Chrome V8 Type Confusion**
Google patched a type confusion bug in the V8 JavaScript engine that allows sandbox escape. Delivered via malicious web pages. Update Chrome/Chromium if you haven't already.

## Interesting Research

**"eBPF Rootkits in the Wild"** — Aqua Security published a detailed analysis of a threat actor using eBPF to hook system calls and hide network connections at the kernel level. The rootkit survived reboots via a malicious kernel module. Worth reading for defenders thinking about container security.

**Passkey Adoption Report** — FIDO Alliance released data showing passkey adoption crossed 2 billion accounts across major platforms. Phishing-resistant auth is finally starting to hit scale.

## Tools & Resources

- `nuclei` v3.4 released — significant speed improvements and new template syntax
- MITRE ATT&CK v16 dropped with several new cloud-specific techniques
- VulnHub added 12 new boot-to-root VMs this month — good practice material
