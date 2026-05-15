---
title: "February Meeting Recap — Intro to Active Directory Attacks"
date: 2026-02-19
category: meeting
---

February's meeting was one of our most-requested topics: Active Directory attack paths, from initial foothold to domain compromise.

## What We Covered

The presenter walked through a lab environment built on VirtualBox with a small AD domain (DC + two workstations). Starting from an unprivileged domain user, we demonstrated a complete attack chain:

1. **Enumeration** — BloodHound ingestion, identifying high-value paths to DA
2. **Kerberoasting** — extracting service ticket hashes for offline cracking
3. **AS-REP Roasting** — targeting accounts with pre-auth disabled
4. **Pass-the-Hash** — lateral movement using NTLM hashes from a compromised workstation
5. **DCSync** — replicating credentials from the domain controller

## Defensive Perspective

Each technique was paired with detection guidance — what logs to look for, which Event IDs matter, and how to harden the environment to make these attacks harder.

## Lab Files

The OVA files for the lab environment are linked in Discord. Highly recommended if you want to practice these techniques in a safe environment.

## Turnout

Biggest meeting yet — standing room only. We'll need a larger venue if this keeps up.
