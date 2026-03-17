---
name: product-strategy-review
description: >
  Conducts PRISM-based product strategy self-review with evidence gates and scoring.
  Use when reviewing product strategy documents, validating strategic options, or
  conducting CPO-level strategy assessments with structured frameworks.
---

# CPO Self-Review Partner — PRISM Strategy

## When to Use
- Use when a PM or product manager needs to review and validate a product strategy document
- For CPO-level strategy self-assessment with structured evidence-based evaluation
- During quarterly strategy reviews or when comparing strategic options for an initiative
- When preparing strategy documents for leadership or board review

## Inputs (required fields)
- `doc_link`: strategy document to review
- `evidence_hub_link`: evidence folder (e.g., `initiatives/<name>/`)
- `product_or_area`, `owner`, `review_window_start/end` (YYYY-MM-DD)
- `riskiest_assumptions`: minimum 2 tagged assumptions
- Optional: `baseline_metric`, `north_star`, `capacity_window`, `runway_months`

If inputs are missing, return HOLD status with a 1-Day Evidence Sprint proposal.

## Context and References
- Read from `company-level-context/` for company-level strategy, OKR, and product vision alignment
- Reference previous review versions for context continuity
- Citation format: `[[ev-id|path#line-range|YYYY-MM-DD]]` (missing citations = 1-step score deduction)

## Process

### Step 1: Evidence readiness check (gate)
Evaluate core evidence items (need 4+ to proceed):
1. Last-180-day signals (3+ founder/customer notes, tickets, competitor moves)
2. Riskiest assumptions (2+) clearly tagged
3. Success criterion (OMTM or qualitative heuristic) defined
4. 1-2 week discovery plan or OKR draft
5. Versioned evidence hub link

**Decision rules:** HOLD if core items <=3. PROCEED if core >=4 (must include #2 and #3). AUTO-ESCALATE if PROCEED + 2+ advanced items.

### Step 2: PRISM scoring (0-5 per dimension)
Score each dimension using evidence citations:

1. **P — Problem Diagnosis:** Causal analysis with recent behavioral data, JTBD mapping, broken assumptions
2. **R — Reframe Opportunity:** Strategic opportunity with timing rationale, competitive whitespace, user/business shift
3. **I — Intentional Bets:** Bold, testable choices with explicit trade-offs, non-goals, success/failure thresholds
4. **S — Systemized Execution:** OKRs reflecting bets, discovery loops, leading indicators, operating rhythm
5. **M — Momentum & Meta-Reflection:** Quarterly retros, stopped work examples, updated assumptions, learning culture

Scale: 0=no evidence, 1=memo level, 2=fragmentary, 3=solid/recent, 4=strong (metrics-connected), 5=exemplary (reproducible). Overall = equal-weighted average.

### Step 3: Mode analysis (evaluate each)
- **Mode 0 — Principle alignment:** Mission/vision coherence, 1-3yr narrative, value thesis
- **Mode 1 — Socratic checklist:** Thesis, outcomes, opportunity, causality, alternatives (3+), trade-offs, unit economics, disconfirming evidence
- **Mode 2 — Bias guardrails:** Address all 6: Confirmation, Availability, Sunk Cost, Survivorship, Overconfidence, Anchoring
- **Mode 3 — Options & capital allocation:** Assumptions, investment, impact, risks, decision rules per option
- **Mode 4 — Scenarios & runway:** Base/Upside/Downside sensitivity, quarterly sequencing
- **Mode 5 — Pre-mortem & kill-switch:** Top-5 failure causes, leading indicators, kill criteria, pivot/market triggers, adaptation plan
- **Mode 6 — Stakeholder lens:** Investor/Board, Engineering, GTM, Customer Support perspectives

### Step 4: Generate outputs and recommend improvements
Produce review.json first, then review.md (max 900 words). Include decision, improvements with owners, and next review date.

## Output
- **Format:** `review.md` (max 900 words) + `review.json` (machine-readable)
- **Template structure:** Required sections: Executive Summary, Impact x Confidence table, PRISM Scores, Pre-mortem/Kill-Switch, Next Review Date
- **Location:** Same directory as the strategy document

## Success Criteria
- All 5 PRISM dimensions scored with evidence citations (metric: 5/5 dimensions scored)
- Evidence gate completed with clear PROCEED/HOLD decision
- At least 3 strategic options compared (Options < 3 triggers warning)
- Improvements are actionable with assigned owners and due dates
- Success metric: Overall PRISM score reported with 0-5 precision

## Decision Support
Based on PRISM scores, recommend one option:
- **Option A: Approve** — Recommend when PRISM overall score >= 3.5/5
- **Option B: Conditional approve** — Suggest when specific dimensions need strengthening
- **Option C: Revise and resubmit** — Suggest when critical evidence gaps exist or score < 2.5/5

## Self-Evaluation
- Review whether all evidence citations are valid and current (not hallucinated)
- Evaluate scoring consistency: Are anchor descriptions applied uniformly?
- Validate that improvements are prioritized by impact, not just listed
- Iterate on review quality by comparing with previous PRISM reviews for the same area
- Improve by incorporating feedback from strategy document owners
- **AI/ML opportunity:** Consider how AI could enhance strategy review (e.g., automated evidence gathering from multiple sources, competitor signal detection, trend forecasting for scenario analysis). Note relevant opportunities in the output.

## Skill Integration
- **Before this skill:** Gather evidence from initiatives, use [OKR Sparring Partner](/okr-sparring-partner) for OKR validation
- **After this skill:** Feed improvements into strategy revision workflow and next planning cycle
- **Related:** [OKR Sparring Partner](/okr-sparring-partner) for OKR-specific review

## Common Anti-Patterns
- Strategy as feature list with no trade-offs or non-goals
- Lagging metrics only with no leading indicators
- Untested assumptions presented as facts
- Over-expansive scope with unclear target segment
- No stopped work or resource reallocation evidence

## Time Efficiency
- Evidence readiness check should complete within 15 minutes
- Full PRISM scoring should complete within 60 minutes per strategy document
- Keep review.md under 900 words to respect reviewer time constraints
