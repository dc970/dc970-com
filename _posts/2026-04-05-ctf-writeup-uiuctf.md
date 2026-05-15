---
title: "CTF Writeup — UIUCTF 2026"
date: 2026-04-05
category: ctf
---

A few DC970 members competed in UIUCTF 2026 last weekend. Here are quick writeups on two challenges we found interesting.

## web/phpmonster (200 pts)

Classic PHP type juggling. The login form compared a user-supplied hash against a stored value using `==` instead of `===`. Supplying a value starting with `0e` followed by digits caused PHP to interpret both sides as scientific notation (both equal zero).

```
username: admin
password: 240610708   # MD5 starts with 0e, triggers magic hash
```

Lesson: always use strict comparison in PHP auth code.

## rev/babyrust (350 pts)

A stripped Rust binary that validated a flag character by character using a lookup table. We loaded it into Ghidra, identified the validation loop, and extracted the table. The flag characters mapped to indices in a shuffled ASCII table — once we had the table it was a direct lookup.

Tools used: Ghidra 11, Python for the table extraction script.

## Final Standing

We finished in the top 30% — not bad for a casual run. If you want to go through any of these challenges together, bring your laptop to the next meeting.
