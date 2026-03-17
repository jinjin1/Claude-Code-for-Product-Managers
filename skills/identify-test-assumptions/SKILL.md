---
name: identify-test-assumptions
description: >
  Identifies and tests assumptions from opportunities and solutions across desirability,
  usability, feasibility, viability, and ethical dimensions. Use when preparing to validate
  ideas, surfacing leap-of-faith assumptions, or designing lightweight tests.
---

# Identify and Test Assumptions

## When to Use
- Use when a PM needs to validate ideas before investing in development
- After creating opportunities with [Create Opportunities](/create-opportunities) or after synthesizing interviews with [Synthesize Snapshots](/synthesize-snapshots)
- Before or after [Generate Solutions](/generate-solutions) in the workflow
- When any new initiative requires systematic risk assessment

## Input
- **Required:** Prioritized opportunities from `opportunities/`, solution sketches from `solutions/`, interview snapshots/synthesis
- **Context:** Reference `company-level-context/` for company-level OKR and strategy alignment
- **Minimum:** 1 target opportunity with evidence + 2-3 candidate solutions (or 1 solution with key user journeys)

## Output
- **Format:** Markdown, saved to `assumptions/[topic]/`
- **Filename:** `assumptions-[opportunity-name]-v[version].md` (kebab-case, auto-increment version)
- **Template structure:** Each file has required sections: Story Map, Assumption Log, Assumption Map, Test Cards, Results
- **Version management:** Check existing files before creation; never overwrite previous versions

## Process

### Step 1: File management (mandatory pre-step)
1. Extract topic from opportunity document content
2. Check existing `assumptions-[topic]-v*.md` files; find highest version
3. Generate new filename with incremented version; verify no conflict

### Step 2: Prepare context
1. Confirm target opportunity and desired outcomes
2. Identify key actors (end-users, systems, third parties)

### Step 3: Story-map candidate ideas
1. Assume the solution exists; map what users do to get value
2. Sequence steps by actor; highlight critical moments

### Step 4: Generate assumptions (five categories)
For each pivotal step, enumerate assumptions across: Desirability, Usability, Feasibility, Viability, Ethical.
- Phrase positively and specifically (what must be true)
- Tie to behavior, not opinions; attach evidence where available

### Step 5: Pre-mortem
"Six months later, launch failed. What went wrong?" Convert reasons into testable assumptions.

### Step 6: Walk OST lines (Outcome-Opportunity-Solution)
Write why the solution addresses the opportunity. Extract each inference as a testable assumption.

### Step 7: Normalize and deduplicate
Rewrite assumptions to be positive, specific, single-concept. Link supporting quotes/data.

### Step 8: Map and prioritize (Assumption Mapping)
1. Plot on 2D grid: X=Evidence (strong left, weak right), Y=Importance (high top, low bottom)
2. Select max 3 Leap-of-Faith Assumptions (LoFA) from top-right quadrant (weak evidence + high importance)
3. If more than 3 in quadrant, prioritize by impact, test complexity, dependencies

### Step 9: Design test cards for LoFA
For each LoFA, define: simulation, method, audience, sample size, time window, and success criteria (absolute numbers, e.g., "3/10 do X").

### Step 10: Run tests, record results, update map
Move assumptions leftward as evidence grows. Iterate or proceed based on findings.

## Success Criteria
- At least 3 LoFA identified with clear test designs (success metric: 3/3 test cards complete)
- Each test card has absolute-number success criteria (not percentages)
- All five assumption categories covered
- Evidence citations linked to each assumption where available

## Decision Support
Based on test results, recommend one of these options:
- **Option A: Proceed** — Recommend when 70% or more of LoFA pass their tests
- **Option B: Iterate** — Suggest when some LoFA pass but others need refinement
- **Option C: Pivot** — Suggest when critical assumptions fail; explore alternative opportunities

## Context Preservation
- Always reference `company-level-context/` for strategic alignment and OKR context
- Review previous assumption versions to track how understanding evolved over time
- Ensure assumptions connect to existing company-level strategy and product vision

## Self-Evaluation
- Review and validate assumption quality: Are they specific, behavioral, and testable?
- Evaluate test design: Is the simulation minimal? Is the audience correct?
- After results, improve the process: What false positives/negatives occurred? How to iterate?
- Use feedback from test outcomes to refine future assumption identification

## Skill Integration
- **Before this skill:** Run after [Create Opportunities](/create-opportunities) or [Generate Solutions](/generate-solutions)
- **After this skill:** Feed results into [Generate Solutions](/generate-solutions) for solution refinement
- **Workflow:** Opportunities > Solutions > Assumptions > Test > Iterate

## Output Template Structure

```markdown
# Assumptions — [Opportunity Name]
**Topic:** [topic] | **Version:** [vN] | **Target Opportunity:** [statement]

## Story Map Snapshot
- **Actors:** [types] | **Key Steps:** 1. [Actor] — [Step] ...

## Assumption Log
| ID | Category | Assumption | Evidence | Importance | Evidence Known | LoFA |
|----|----------|------------|----------|------------|----------------|------|

## Assumption Map Summary
- **LoFA (max 3):** [IDs] | **Notable clusters:** [notes]

## Test Cards (per LoFA)
- **Assumption / Simulation / Method / Audience / Sample & Window / Success Criteria / Next if Pass-Fail**

## Results and Decisions
- Outcomes / Map updates / Decisions

## Next Steps
- [ ] Run next test | [ ] Evolve idea | [ ] Share with stakeholders
```

## Time Efficiency
- Complete assumption identification within 60 minutes per opportunity
- Test card design should take no more than 30 minutes per LoFA
- Start with the smallest viable simulation; scale only with positive signals
