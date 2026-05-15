---
title: "March Meeting Recap — Network Defense & Packet Analysis"
date: 2026-03-20
category: meeting
---

March's meeting focused on network defense — specifically, what you can learn from packet captures before an attacker establishes encryption.

## Session Summary

We worked through a series of PCAP files sourced from public CTF archives. The goal was to identify attacker activity using only Wireshark and Zeek logs, no EDR telemetry.

Key things the group practiced:

- Spotting C2 beaconing patterns by graphing connection intervals
- Extracting files from HTTP streams and identifying them by magic bytes
- Correlating DNS queries with suspicious outbound connections
- Reading Zeek `conn.log` and `dns.log` to reconstruct a timeline

## Tools Demonstrated

- **Wireshark** — display filters, stream following, export objects
- **Zeek** — running against a PCAP offline, parsing logs with `zeek-cut`
- **NetworkMiner** — quick artifact extraction for less experienced members

## Attendance

About 15 people came out. Mix of blue teamers and a few folks newer to networking concepts — the varied skill levels made for good discussion.

## Next Up

April will shift to the offensive side with a malware analysis workshop. Details posted soon.
