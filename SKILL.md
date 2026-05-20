# Email Copywriter

> **Agent**: `depositback-agent-email-copywriter`  
> **Group**: Content Production (Group 2)  
> **Product**: DepositBack — Security Deposit Demand Letter Service  
> **Price Points**: $19.99 (demand letter) / $39.99 (small claims prep)

## Purpose

Crafts emails for the entire single-page e-commerce journey: welcome email, purchase confirmation with PDF delivery tips, small-claims upsell ($19.99 → $39.99), 30-day guarantee reminder, and win-back sequence. Integrates with Brevo API.

## DepositBack Context

DepositBack is a single-page, no-signup transactional product for US renters seeking to recover security deposits. The entire customer journey fits on one URL: landing page → 6-question form → Revolut payment → PDF emailed. Conversion rate target: **4% visitor-to-purchase minimum** (median for sub-$60 e-commerce). Content must be state-specific, CCPA-compliant, and optimized for both traditional SEO and Generative Engine Optimization (GEO).

## Inputs (from Group 1 — Discovery)

- Purchase events from operations/purchase-orchestrator
- A/B test results from analytics/funnel-analyst
- Seasonal campaigns from distribution/community-engager

## Outputs (to Group 3 — Distribution)

- Brevo email templates → distribution/email-dispatcher inbox
- A/B subject line variants → analytics/funnel-analyst inbox
- Upsell copy → distribution/email-dispatcher inbox

## Human Escalation Points 🛑

- Financial or legal claims in email copy
- Refund/guarantee language changes
- Promotional discounts requiring margin approval

## Skills

| Skill | Description | Status |
|-------|-------------|--------|
| `noop` | Health check / pipeline verification | ✅ Active |
| `generate` | Primary content generation for this agent | 🔧 Planned |

## Workflow

1. Poll `data/inbox/` for task manifests from upstream agents.
2. Resolve required skills (local `skills/` or ClawHub fallback).
3. Execute content generation workflow.
4. Write artifacts to `data/outbox/`.
5. Update `data/state.json` with status and artifact references.

## Inter-Agent Protocol

```
Discovery (Group 1) → [THIS AGENT] → Distribution (Group 3)
     pain-signals    →   generates    →   publishes
     search-intents  →   content      →   distributes
     competitor-intel→   assets       →   amplifies
```

## Runtime

```bash
pip install -r requirements.txt
python runtime/main.py
```

## Secrets Required

- `OPENAI_API_KEY` — AI content generation
- `GITHUB_TOKEN` — Auto-provided for Actions
