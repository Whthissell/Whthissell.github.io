---
title: "Algorithmic Futures Market Trading System"
subtitle: "A safety-first trading and research platform for crypto, weather, sports, and commodities markets on a decentralized futures exchange"
role: "Solo developer"
status: "May 2026 - September 2026"
tech: ["Python", "FastAPI", "TypeScript / Node.js", "WebSockets", "SQLite", "Statistical Testing", "AI-Assisted Development"]
repo_url: ""
demo_url: ""
cover_image: "/assets/images/covers/ai-in-finance.svg"
order: 3
---

## Overview

I built two paper-trading bots against a decentralized futures exchange, plus the
research process that decides what they're allowed to run. One trades
short-duration crypto markets: BTC, ETH, SOL, XRP, DOGE, BNB and HYPE up/down
windows. The other trades weather, sports, and commodities markets. Everything
runs in simulation. Neither bot has ever placed a real order, and flipping one
into live mode takes a deliberate, multi-step decision rather than a stray click.

## A Research Process, Not Just a Strategy File

Every strategy has to earn its place. I've written around 70 numbered research studies
that argue for enabling, killing, or tuning a given strategy, and from the 38th on,
each one starts with a pre-registration written before any results come in. The code
just reflects whatever the latest study concluded. Between the two bots there are more
than 40 registered strategies, each in its own file, with a comment block that reads
like a decision log and cites the exact study that got it turned on or shut off.

## Making the Simulation Honest

The easiest way for a paper-trading bot to lie to you is to fill your fake orders at
the midpoint price. This one won't fill a resting quote unless a real trade prints
through it or the book itself trades through your price, which gets flagged as an
adverse fill because that's what getting run over in a live market looks like. It
also models the exchange's minimum order size and the latency between deciding to
trade and the exchange actually seeing that decision, including the case where a
cancel arrives too late to help. Settlement comes from the exchange's own market
resolution rather than a spot price feed, after an early version that used spot
prices produced results that turned out to be fiction.

## Keeping the Statistics Honest

Every enable or kill decision runs through proper statistical testing (Clopper-Pearson
confidence bounds, sequential testing, and false-discovery control across the whole
strategy set) instead of a glance at a P&L chart. One lesson that stuck: a longshot
bet paying three cents needs on the order of 550 closed trades before a losing streak
means anything, and I have documented cases of a strategy getting killed too early on
nothing more than a bad run of luck.

## The Part That Could Touch Real Money

A separate TypeScript service handles live order execution, and it has never been
turned on. Its wallet is built without a network connection at all, so it is
physically unable to broadcast a transaction even if the code told it to. It will
only sign the two specific message types the exchange uses to place an order and
refuses everything else, including the kind of signature that could quietly
approve someone else to spend your funds. If the exchange ever changed how those
messages are structured, the signer would simply stop working instead of signing
something it no longer recognizes.

## Built With Claude Code as a Standing Collaborator

I used Claude Code throughout, not just to write code but to run part of the
research process itself: multi-agent audits of my own analysis, and a living rules
document the AI checks before touching anything, covering things like never
restarting the bots without approval and never writing to a live database. A few of
those rules exist because breaking them once produced a conclusion I had to retract.

## By the Numbers

About 20,000 lines of Python run the two bots plus a newer research console for
perpetual futures on the same exchange, which ships with every strategy switched off
and no live order path at all. Another roughly 3,200 lines of TypeScript run the
execution service and its dashboard. Altogether the platform has evaluated 45
strategies across tens of thousands of simulated fills.
