---
name: synthesize-snapshots
description: >
  Synthesizes multiple interview snapshots to identify common patterns, integrates
  experience maps, and creates comprehensive insights. Use after completing multiple
  interviews on the same topic or when identifying shared patterns across user segments.
---

# Synthesize Interview Snapshots

## When to Use
- Use when a PM or product manager has completed 3-5+ interviews on the same initiative topic
- When identifying shared patterns across different user segments
- Before creating opportunities or generating solutions in the discovery workflow
- When sharing research findings with stakeholders

## Input
- **Required:** Minimum 3-5 interview snapshots from [Create Interview Snapshots](/create-interview-snapshots)
- **Context:** Reference `company-level-context/` for company-level strategic priorities and OKR alignment
- **Quality gate:** All snapshots must follow consistent format with concrete behavioral details

## Output
- **Format:** Markdown, saved to `user-interviews/synthesis/`
- **Filename:** `synthesis-[initiative-name]-v[version].md` (kebab-case, auto-increment)
- **Template structure:** Required sections include Executive Summary, Participant Overview, Top Opportunities, Integrated Experience Map, Key Insights, Research Gaps, Next Steps
- **Version management:** Check existing files before creation; never overwrite previous synthesis versions

## Process

### Step 1: Data preparation
1. Gather all relevant interview snapshots for the initiative
2. Check for existing synthesis files (support incremental updates)
3. If previous synthesis exists, identify only new/unprocessed snapshots
4. Standardize format and verify completeness

### Step 2: Pattern analysis
1. Extract recurring themes, behaviors, and pain points across snapshots
2. Review each snapshot's experience map for overlaps and divergences
3. Document how different segments behave differently
4. Count frequency and assess intensity of each pattern

### Step 3: Experience map integration
1. Overlay individual experience maps; identify common stages
2. Consolidate similar activities into shared stages with logical flow
3. For each stage, document: common actions, shared thoughts, emotional journey, pain points, workarounds, segment variations
4. Attach supporting quotes from multiple participants

### Step 4: Insight development and opportunity identification
1. Synthesize patterns into actionable insights with supporting evidence
2. Write opportunities in user perspective: "I want to... but... because..."
3. Rate each opportunity by frequency, evidence strength, and impact
4. Identify research gaps and unanswered questions

### Step 5: Review and validate
1. Evaluate whether patterns have sufficient multi-participant evidence
2. Check for confirmation bias; actively look for contradictory evidence
3. Validate that insights are actionable, not just descriptive
4. Improve synthesis quality by iterating on weak evidence areas

## Success Criteria
- Minimum 3 common patterns identified across participants (target: 80% coverage)
- Each insight supported by evidence from 2+ participants
- All identified user segments have pattern analysis coverage
- At least 2 actionable opportunities identified per synthesis
- Data quality assessment average score of 70/100 or higher

## Decision Support
When synthesis reveals conflicting patterns, recommend options:
- **Option A: Deepen research** — Suggest additional interviews to resolve ambiguity
- **Option B: Segment the findings** — Recommend splitting insights by user segment
- **Option C: Proceed with caveats** — Document uncertainty and flag for future validation

## Context Preservation
- Reference `company-level-context/` strategy documents to align research direction
- Prioritize patterns that connect to company-level OKR and product vision
- Track which snapshots were included in each synthesis version for context continuity
- Preserve existing synthesis insights when doing incremental updates

## Self-Evaluation
- Review pattern quality: Are they behavioral and specific, or vague generalizations?
- Evaluate evidence strength: Multiple sources? Concrete examples?
- Validate segment coverage: Are all user types represented?
- Improve by checking for common mistakes: over-generalization, confirmation bias, jumping to solutions
- Iterate: Use feedback from opportunity creation to refine future synthesis

## Skill Integration
- **Before this skill:** Complete interviews using [Create Interview Snapshots](/create-interview-snapshots)
- **After this skill:** Use synthesis to feed [Create Opportunities](/create-opportunities) and [Generate Solutions](/generate-solutions)
- **Workflow:** Interviews > Snapshots > Synthesis > Opportunities > Solutions > Assumption Testing

## Output Template Structure

```markdown
# What We Learned: [Topic] Discovery Research

**Date Range:** [dates] | **Participants:** [N] | **Initiative:** [name] | **Version:** [vN]
**Synthesis Type:** [Initial/Incremental] | **Processed Snapshots:** [list]

## Executive Summary
[3-5 key findings with recommendations]

## Participant Overview
| Segment | Count | Key Characteristics |

## Top Opportunities
### 1. [Title]
**Frequency:** X/Y | **Evidence:** Strong/Moderate/Weak | **Impact:** High/Med/Low
**Opportunity:** "I want to... but... because..."
**Supporting Evidence:** [quotes] | **Business Impact:** [description]

## Integrated Experience Map
### Stage [X]: [Title]
- Common Actions / Shared Thoughts / Emotional Journey / Pain Points / Workarounds / Segment Variations / Evidence

## Key Insights
### 1. [Insight]
**What / Evidence / Implications**

## Research Gaps
- [Unanswered questions]

## Next Steps
- [ ] [Actions]
```

## Time Efficiency
- Incremental synthesis (1-2 new snapshots) should complete within 30 minutes
- Full synthesis (3-5 snapshots) should complete within 60 minutes
- Avoid re-processing previously analyzed snapshots; focus time on new data only
