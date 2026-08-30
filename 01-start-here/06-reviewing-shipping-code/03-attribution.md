---
title: Attribution
source: https://www.onorca.dev/docs/review/attribution
---

## Overview

Orca implements a tracking system that records which lines agents modify during code editing. The diff viewer displays AI-originated lines with a subtle marker in the gutter, while human edits on top of AI code restore human attribution.

## How it works

When an agent writes to a file through its tooling, Orca records the ranges. The diff viewer renders AI-originated lines with a subtle marker in the gutter. Human edits on top of AI code flip the attribution back to human.

## Why it matters

- You can identify which sections of a pull request warrant careful review
- Security and compliance teams can distinguish between code written by AI versus human developers
- Review cycles accelerate since reviewers skip re-examining code they personally wrote

## Scope

Attribution is local to Orca — it doesn't get committed to git. For permanent attribution records, users can export the diff metadata from the diff toolbar.
