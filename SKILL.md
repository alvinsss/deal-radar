---
name: "deal_radar"
description: "Screen the last 24 hours of new free deals — AI free credits, free VPS, cloud resources, student benefits — from official sources, deduplicated and ranked by claim value. Trigger when the user says 查今天羊毛, 检查最新福利, or 检查最近24小时有什么免费 AI 额度."
---

# Deal Radar

## Purpose
Turn a one-line request ("查今天羊毛") into a verified, ranked list of new free deals from the last 24 hours. No fabricated deals, no rehashed old ones, no ads.

## Workflow
1. Collect candidates from the four sources in order, then vendor official pages:
   1. 懒猫 AI (lanmao.ai)
   2. AIHot Token 羊毛 (aihot.news)
   3. 赛博鸡蛋 (jidan.si)
   4. 白嫖计 (baipiaoji.com)
   Vendor official pages (announcement / pricing / promotion page) are the tie-breaker and the verification source.
2. Filter: keep only items first seen in the last 24 hours. Drop expired, duplicate, and pure-advertising items. Merge the same offer across sources into one record.
3. Verify each kept item against its official announcement or original activity page. Record the official link. If it cannot be verified, keep it only under 待核实, never in the verified list.
4. Classify each item: truly free / free trial / recharge-required / trading-volume-required / invite-required. Flag region, eligibility, and hidden conditions.
5. Rank by claim value (highest first), with nearest deadline breaking ties. Auto-archive anything already expired.
6. Present the ranked list. Do not register, pay, or post anything externally.

## Output Contract
Each deal carries: title, official claim link, amount/value, eligibility, card-binding requirement (yes/no), deadline, status (verified / 待核实), and category (one of the five above). Unverifiable items go in a separate 待核实 section and are excluded from counts and rankings. If nothing new verified in the last 24 hours, say so plainly instead of padding with old items.

## Operating Rules
1. Official or trusted sources first; a secondary guide never settles a deadline — check the live page.
2. Never fabricate a deal, a value, or a deadline. An unverified value stays out of counts and rankings.
3. Never auto-register, auto-pay, or post externally. Claiming is always the user's decision.
4. Keep the skill thin: this file holds the workflow and the contract. Source-specific scraping details live in the caller's working notes, not here.
