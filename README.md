# Claude Code for Product Managers

Transform Claude Code into your AI-native product management copilot. A Claude Code plugin with 17 specialized PM skills, 3 orchestration agents, and proven frameworks like Continuous Discovery Habits, PRISM, and Evidence-Guided product development.

Originally inspired by the [Maven course on AI-native PMs](https://maven.com/p/0a96cb/cursor-isn-t-just-for-coding-how-ai-native-p-ms-work), [AI Dev Tasks](https://github.com/snarktank/ai-dev-tasks/tree/main), and [Lee Robinson's demo](https://www.youtube.com/watch?v=8QN23ZThdRY).

## Why this toolkit?

Product management involves complex workflows across research, discovery, and delivery. This toolkit brings structure, clarity, and AI-native efficiency to the process:

1. **Unified context management** -- Centralize all PM knowledge, frameworks, and insights in one AI-accessible workspace
2. **Structured discovery** -- Run systematic user research with Continuous Discovery Habits (Teresa Torres) built in
3. **AI-native workflows** -- Create PRDs, 1-pagers, design briefs, and strategy reviews through natural conversation
4. **Iterative improvement** -- Documents and insights grow smarter with every AI interaction

## Quick start

### Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) **v1.0.33 or later** installed (`npm install -g @anthropic-ai/claude-code`)
- Logged in to Claude Code (`claude` to start, then `/login`)

### Install as a plugin

Run these two commands **one at a time** inside Claude Code:

```bash
# Step 1: Add the marketplace
/plugin marketplace add jinjin1/Claude-Code-for-Product-Managers
```

```bash
# Step 2: Install the plugin
/plugin install pm-toolkit@pm-toolkit-marketplace
```

> **Important:** Run each command separately. Wait for Step 1 to complete before running Step 2.

> **SSH authentication failed?** If you see `Permission denied (publickey)`, use the HTTPS URL instead:
> ```bash
> /plugin marketplace add https://github.com/jinjin1/Claude-Code-for-Product-Managers.git
> ```

### Or load directly for local testing

```bash
git clone https://github.com/jinjin1/Claude-Code-for-Product-Managers.git
claude --plugin-dir ./Claude-Code-for-Product-Managers
```

### Start using

| What you want to do | Just type |
|:---------------------|:----------|
| Process interview transcripts | `/pm-toolkit:create-interview-snapshots` |
| Create a PRD | `/pm-toolkit:create-prd` |
| Review product strategy (PRISM) | `/pm-toolkit:product-strategy-review` |
| Start a new initiative | `/pm-toolkit:setup-initiative` |
| Run full discovery research | Request the `discovery-researcher` agent |

## What you can do

### User research & discovery

Run the full Continuous Discovery Habits workflow, from raw interview data to testable assumptions:

```
Interview data > /pm-toolkit:create-interview-snapshots > /pm-toolkit:synthesize-snapshots
> /pm-toolkit:create-opportunities > /pm-toolkit:generate-solutions > /pm-toolkit:identify-test-assumptions
```

Or let the `discovery-researcher` agent run the entire flow for you.

| Skill | What it does |
|:------|:-------------|
| `/pm-toolkit:create-interview-snapshots` | Extract structured snapshots from qualitative interviews |
| `/pm-toolkit:synthesize-snapshots` | Find patterns and themes across multiple interviews |
| `/pm-toolkit:create-opportunities` | Build an Opportunity Solution Tree (OST) |
| `/pm-toolkit:generate-solutions` | AI-human collaborative solution ideation |
| `/pm-toolkit:identify-test-assumptions` | Surface and test leap-of-faith assumptions |

### Product documents

Create professional product artifacts through guided conversation:

| Skill | What it does |
|:------|:-------------|
| `/pm-toolkit:create-prd` | Generate Product Requirements Documents with clarifying questions |
| `/pm-toolkit:create-one-pager` | Amazon-style decision-focused 1-Pagers |
| `/pm-toolkit:create-design-brief` | Design briefs in JSON + Markdown |
| `/pm-toolkit:generate-figma-prompt` | Figma Make-ready prompts (5000 char limit) |

### Product strategy & OKRs

Review and refine your strategic direction with proven frameworks:

| Skill | What it does |
|:------|:-------------|
| `/pm-toolkit:product-strategy-review` | PRISM framework: Problem Diagnosis, Reframe, Intentional Bets, Systemized Execution, Momentum |
| `/pm-toolkit:product-vision-review` | Evaluate vision on 4 criteria: Lofty, Realistic, Constraint-Free, User-Grounded |
| `/pm-toolkit:okr-sparring-partner` | Context-aware OKR coaching and sparring partner |
| `/pm-toolkit:calculate-ice-score` | ICE prioritization scoring (Impact x Confidence x Ease) |

### Task management

| Skill | What it does |
|:------|:-------------|
| `/pm-toolkit:generate-tasks` | Break PRDs into actionable, granular task lists |
| `/pm-toolkit:setup-initiative` | Create a new initiative folder with standardized structure |

### Meetings & writing

| Skill | What it does |
|:------|:-------------|
| `/pm-toolkit:one-on-one-meeting` | Structure and organize 1:1 meeting notes |
| `/pm-toolkit:writing-guide` | Consistent writing style and tone standards |

## Agents -- multi-step workflows

For complex workflows, agents orchestrate multiple skills end-to-end. They are automatically invoked when Claude detects a matching task, or you can request them explicitly.

| Agent | What it does | How to invoke |
|:------|:-------------|:--------------|
| `discovery-researcher` | Full CDH workflow: interviews, synthesis, opportunities, solutions, assumptions | "Use the discovery-researcher agent to analyze these interviews" |
| `initiative-planner` | End-to-end planning: setup, 1-pager, PRD, design, tasks | "Use the initiative-planner to set up checkout optimization" |
| `strategy-reviewer` | Combined PRISM strategy + vision + OKR review | "Use the strategy-reviewer to review our Q3 strategy" |

Each agent has relevant skills preloaded via the `skills` field, so it can directly apply skill guidelines without needing separate invocations.

## Workflow connections

```
                    discovery-researcher
                           |
    +-----------+----------+-----------+
    v            v                      v
create-interview  synthesize-      create-opportunities
  -snapshots        snapshots              |
                                    +------+------+
                                    v              v
                            generate-       calculate-
                             solutions        ice-score
                                 |
                                 v
                        identify-test-
                          assumptions
                                 |
               ---------- handoff ----------
                                 |
                    initiative-planner
                           |
    +----------+-----------+-----------+----------+
    v          v           v           v          v
setup-    create-    create-   create-   generate-
initiative  one-pager    prd     design-brief  tasks
                                    |
                                    v
                            generate-figma-
                                prompt
```

## Common workflows

### Starting a new product initiative
```
/pm-toolkit:setup-initiative > /pm-toolkit:create-one-pager > /pm-toolkit:create-prd
> /pm-toolkit:create-design-brief > /pm-toolkit:generate-tasks
```
Or request the `initiative-planner` agent to run the full flow.

### Reviewing strategic direction
```
/pm-toolkit:product-strategy-review (PRISM)
+ /pm-toolkit:product-vision-review
+ /pm-toolkit:okr-sparring-partner
```
Or request the `strategy-reviewer` agent for a combined review.

### Prioritizing ideas
```
/pm-toolkit:calculate-ice-score > Score and rank ideas > Select for exploration
```

## Project structure

```
.claude-plugin/               -- Plugin manifest and marketplace
  plugin.json                 -- Plugin identity and metadata
  marketplace.json            -- Marketplace catalog for distribution

skills/                       -- 17 PM skills (SKILL.md format)
  create-prd/SKILL.md
  calculate-ice-score/SKILL.md
  ...

agents/                       -- 3 orchestration agents
  discovery-researcher.md
  initiative-planner.md
  strategy-reviewer.md

CLAUDE.md                     -- PM coaching persona (auto-loaded)

company-level-context/        -- Your organization's strategic documents
  okrs/
  product-vision-and-strategy/
  team-structure/

initiatives/                  -- Active product initiatives
  _templates/                 -- Initiative template structure
  [initiative-name]/          -- Each initiative's workspace
    user-interviews/          -- Snapshots, synthesis, transcripts
    opportunities/            -- Opportunity maps (OST)
    assumptions/              -- Assumption tests
    solutions/                -- Solution ideation
    design/                   -- Design briefs & Figma prompts
    prd/                      -- Product Requirements Documents
    product-analytics/        -- Analytics frameworks
    tasks/                    -- Task breakdowns

meeting-notes/                -- Meeting documentation
  1-1 notes/
  leadership/
  product-trio/
  board-n-investor/
```

## Installation options

### As a Claude Code plugin (recommended)

Run these two commands **one at a time** inside Claude Code:

```bash
# Step 1: Add the marketplace
/plugin marketplace add jinjin1/Claude-Code-for-Product-Managers
```

```bash
# Step 2: Install the plugin
/plugin install pm-toolkit@pm-toolkit-marketplace
```

> **Important:** Run each command separately. Wait for Step 1 to complete before running Step 2.

> **SSH authentication failed?** Use the HTTPS URL instead:
> ```bash
> /plugin marketplace add https://github.com/jinjin1/Claude-Code-for-Product-Managers.git
> ```

### Local development / testing
```bash
git clone https://github.com/jinjin1/Claude-Code-for-Product-Managers.git
claude --plugin-dir ./Claude-Code-for-Product-Managers
```

### Submit to official marketplace
This plugin can also be submitted to the [Anthropic official marketplace](https://claude.ai/settings/plugins/submit).

## Troubleshooting

| Error | Cause | Solution |
|:------|:------|:---------|
| `SSH authentication failed` / `Permission denied (publickey)` | GitHub SSH key not configured | Use HTTPS URL: `/plugin marketplace add https://github.com/jinjin1/Claude-Code-for-Product-Managers.git` |
| `Malformed input to a URL function` | Two `/plugin` commands pasted together | Run each command separately -- wait for Step 1 to finish before running Step 2 |
| `Unknown command: /plugin` | Claude Code version too old | Update to v1.0.33+: `npm update -g @anthropic-ai/claude-code` |
| `zsh: no such file or directory: /plugin` | Running `/plugin` in terminal instead of Claude Code | Start Claude Code first with `claude`, then run `/plugin` inside the session |
| `command not found: claude` | Claude Code not installed | Install with `npm install -g @anthropic-ai/claude-code` |

## Acknowledgments

- **[Cursor isn't just for coding: how AI-native PMs work](https://maven.com/p/0a96cb/cursor-isn-t-just-for-coding-how-ai-native-p-ms-work)** -- Tal Raviv and Hilary Gridley's course on transforming AI tools into a PM copilot
- **[AI Dev Tasks](https://github.com/snarktank/ai-dev-tasks/tree/main)** -- Structured workflow framework for AI-assisted development
- **[Cursor AI Agents Work Like 10 Developers](https://www.youtube.com/watch?v=8QN23ZThdRY)** -- Lee Robinson's demo
- **[Continuous Discovery Habits](https://www.youtube.com/watch?v=9RFaz9ZBXpk)** -- Teresa Torres' framework on continuous user research and discovery
- **[Evidence-Guided](https://www.youtube.com/watch?v=aJWSn-tz3jQ)** -- Itamar Gilad's framework on evidence-guided product development
- **[Agent Skills Standard](https://agentskills.io)** -- Open standard for extending AI agents

## License

MIT
