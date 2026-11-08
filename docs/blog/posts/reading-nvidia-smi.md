---
date:
  created: 2026-09-30
authors: [ehsan]
categories: [GPU]
tags: [gpu]
readtime: 3
---

# Reading `nvidia-smi` output

This post sets its read time by hand (`readtime: 3`) instead of letting the
blog work it out.

<!-- more -->

| Column | Meaning |
|--------|---------|
| `Perf` | Performance state, `P0` is the highest |
| `Pwr:Usage/Cap` | Current draw against the power limit |
| `Volatile Uncorr. ECC` | Uncorrectable memory errors since the last reboot |
