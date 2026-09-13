---
title: "Algorithmic Futures Market Trading System"
subtitle: "A statistically rigorous platform for backtesting and trading futures strategies"
role: "Solo developer"
status: "Summer 2026 – present"
tech: ["Python", "TypeScript / Node.js", "Quantitative Finance", "Statistical Testing", "AI-Assisted Development"]
repo_url: ""
demo_url: ""
cover_image: ""
order: 2
---

## Overview

Built an algorithmic trading platform for futures markets: a large Python trading
engine paired with a statistically rigorous strategy-validation pipeline and a
TypeScript/Node.js execution gateway for order routing.

## Approach

- Engineered a ~20,000-line Python platform to trade futures markets, backtesting 45
  candidate strategies across tens of thousands of simulated fills.
- Built a separate TypeScript/Node.js execution gateway to handle live order routing
  and market connectivity.
- Designed a statistical evaluation pipeline — pre-registered hypotheses, sequential
  probability ratio testing (SPRT), and false-discovery-rate control — to guard
  against overfitting and false positives across the 45-strategy search.
- Used the pipeline to systematically retire negative-expected-value strategies
  before risking any capital.

## AI-Assisted Development

Used Claude Code as part of the engineering process itself: orchestrated multi-agent
code audits, built and used custom skills and subagent systems, and iterated on
strategy design directly with LLM agents.

## Results

The statistical evaluation pipeline filtered the 45 candidate strategies down to a
validated subset, systematically retiring negative-EV strategies before any were
traded live.
