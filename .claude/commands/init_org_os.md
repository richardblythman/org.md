# Init Org OS

## Overview

Guide end-users through setting up an Org Organisation OS that helps operationalize organizational frameworks. This command captures the operator profile, discovers which frameworks the user works with (Lean, OKRs, JTBD, EOS, or combinations), understands their customizations, defines their memory structure, configures state persistence, captures templates, and produces a complete CLAUDE.md with initial directory structure.

## Purpose & Value

### Workflow Being Automated

Setting up an Org Organisation OS requires understanding:
- Who the operator is (name, role, productivity peaks, work style)
- Which product frameworks the user employs
- How they've customized or combined these frameworks
- What artifacts they track (experiments, rocks, milestones, hypotheses, etc.)
- How these artifacts should be organized in memory
- How tasks are routed (AI-supported, human-only, mixed)
- How state is persisted (git-based, markdown logs, or both)
- What templates they use for consistency

This is a complex discovery process that varies significantly based on the user's operational context.

### Time/Effort Savings

- Eliminates guesswork in structuring a product ops agent
- Ensures the memory structure matches the user's mental model
- Creates templates that enforce consistency across artifacts
- Produces a CLAUDE.md that accurately reflects the user's framework

### Target Users

- End-users setting up their own Org Organisation OS
- Product managers, founders, or ops leads who want to operationalize their frameworks
- Teams combining multiple frameworks (e.g., OKRs for direction + Lean for execution)

## Command Invocation

### Command Name
```
/init_org_os
```

### Parameters

None required. This is a conversational discovery command.

### Usage Examples

```bash
# Start the discovery process
/init_org_os
```

## Procedural Requirements

### Prerequisites

- User should have a general idea of which product frameworks they use
- **The agent repository must already exist before running this command**
  - This command assumes you've already created an agent repository (use `/init_agent` first if you haven't)
  - Do NOT ask the user if they have a repository or what to name it - assume it already exists
  - This command configures an existing repository, it does not create one

### Step-by-Step Workflow

---

#### Step 1: Introduction & Framework Discovery

**Purpose**: Understand which frameworks the user works with and set expectations for the conversation.

**Actions**:

1. Welcome the user and explain the process (assume the repository already exists):

```
I'll help you set up an Org Organisation OS tailored to your frameworks and workflows in your existing agent repository. We'll go through a few steps:

1. Get to know you (operator profile)
2. Discover which frameworks you use (Lean, OKRs, JTBD, EOS, or others)
3. Understand how you've customized them or use them together
4. Design your memory structure for tracking artifacts
5. Set up state persistence (work logging)
6. Set up any templates you use
7. Generate your CLAUDE.md and directory structure

Let's start with you.

**Tell me a bit about yourself:**

1. **Who are you?**
   - Name:
   - Role: (e.g., founder, PM, ops lead)
   - Company/Project:

2. **When do you do your best work?**
   - Productivity peaks: (e.g., "mornings for deep work", "afternoons for meetings")
   - Typical time blocks: (e.g., "30-minute slots between meetings", "2-hour focus blocks")

3. **What tools do you currently use?**
   - (e.g., Google Docs, Slack, Notion, Linear, etc.)

4. **How would you describe your work style?**
   - (e.g., "prefer async", "like daily standups", "need structure", "context-switch frequently")

This helps the agent understand how to work *with* you, not just *for* you.
```

2. Wait for user response and capture their operator profile.

**Validation**:
- User has provided at least name and role
- Productivity preferences captured (or noted as "flexible")
- Tools listed (or noted as "various")

**Error Handling**:
- If user wants to skip, note defaults: "flexible schedule, various tools"
- Can always be updated later in CLAUDE.md

---

#### Step 1b: Workflow Discovery & Framework Design

**Purpose**: Understand the user's actual workflow, identify pain points, and design a framework that fits how they work.

**Actions**:

**Part 1: Current Process Discovery**

1. Ask about their current process through a concrete example:

```
Now let's understand how you currently work.

**Walk me through a recent project or initiative:**

1. **What kicked it off?**
   - A goal you wanted to hit? A problem to solve? A hypothesis to test? A customer request? Something else?

2. **What did you do to make progress?**
   - Did you break it into pieces? Run experiments? Set milestones? Just start building?

3. **What artifacts did you create along the way?**
   - Documents? Spreadsheets? Notes? Recordings? Nothing formal?

4. **How did you know when it was "done" or successful?**
   - Hit a metric? Felt complete? Got customer feedback? Shipped something?

Don't worry about using the "right" terminology - just describe what actually happened.
```

2. Wait for user response. Listen for:
   - **Hierarchy signals**: What contains what? (e.g., "We had a goal, broke it into experiments...")
   - **Artifact signals**: What do they create? (e.g., "I wrote up a hypothesis doc...")
   - **Stage signals**: How does work flow? (e.g., "First we tested, then we measured...")
   - **Framework signals**:
     - Lean: hypotheses, experiments, validated learning, pivots, customer interviews
     - OKRs: objectives, key results, quarterly goals, measurable outcomes
     - EOS: rocks, 90-day priorities, milestones, weekly check-ins
     - JTBD: customer jobs, outcomes, hiring/firing products

**Part 2: Pain Points**

3. Ask about improvements:

```
Thanks for walking me through that.

**What would you improve about this process?**

- What gets lost or forgotten?
- Where do you waste time?
- What decisions feel harder than they should be?
- What would make this work better for you?
```

4. Wait for user response and capture their pain points.

**Part 3: Synthesis & Framework Design**

5. Synthesize what you've learned and propose a framework:

```
Based on what you've described, here's what I'm hearing:

**Your current process:**
- [How work gets kicked off]
- [How work progresses - stages/phases]
- [What artifacts you create]
- [How you know when it's done]

**What you'd improve:**
- [Pain point 1]
- [Pain point 2]

**Suggested framework:**

This sounds like a [Framework Name] approach. [1-2 sentences on why it fits and how it addresses their pain points.]

Here's how I'd structure it for you:

**Hierarchy:**
[Top-level concept] → [Mid-level concept] → [Artifact level]
Example: Strategies → Experiments → Learnings

**Stages:**
[Stage 1] → [Stage 2] → [Stage 3]
Example: Build → Measure → Learn

**Key artifacts you'd track:**
- [Artifact 1]: [What fields matter based on their description]
- [Artifact 2]: [What fields matter based on their description]

Does this match how you think about your work? What would you adjust?
```

6. Refine based on user feedback. Ask targeted follow-up questions only for gaps:

**If hierarchy is unclear:**
```
I want to make sure I understand the hierarchy.

When you [do X], does that sit inside a larger [Y]? Or is [X] the top level?

For example: Are experiments part of a strategy? Or do you just run experiments independently?
```

**If stages are unclear:**
```
What stages does work move through for you?

For example, some people think in terms of:
- Build → Measure → Learn (testing ideas)
- Plan → Execute → Review (hitting goals)
- Discover → Define → Deliver (solving problems)

Or you might have your own stages. What feels right?
```

**If artifacts are unclear:**
```
What would you actually want to track in this system?

When you create a new [experiment/rock/initiative], what information matters?
- Name and description?
- Owner?
- Due date or timeframe?
- Success criteria?
- Status?
- Something else?
```

**If success criteria are unclear:**
```
How do you know when a [experiment/rock/initiative] is successful?

- Hit a specific metric?
- Completed all milestones?
- Learned what you needed to learn?
- Shipped something?
```

7. Confirm the framework design before proceeding:

```
Great, here's the framework we've designed:

**Framework type:** [Lean / OKRs / EOS / JTBD / Hybrid / Custom]

**Hierarchy:**
- [Top level]: [Description]
  - [Mid level]: [Description]
    - [Artifact level]: [Description]

**Stages:** [Stage 1] → [Stage 2] → [Stage 3]

**Key artifacts:**
| Artifact | Key Fields |
|----------|------------|
| [Type 1] | [field1, field2, field3] |
| [Type 2] | [field1, field2, field3] |

**Pain points this addresses:**
- [Pain point] → [How the framework helps]

Does this capture how you want to work? Once you confirm, we'll move on to designing your memory structure and templates.
```

**Validation**:
- User has described their actual workflow
- Pain points captured
- Framework type identified (standard or custom)
- Hierarchy confirmed (what contains what)
- Stages confirmed (how work flows)
- Key artifacts and their fields identified
- User has confirmed the framework design

**Error Handling**:
- If user gives very brief answers, probe deeper: "Can you give me a specific example? What was the last thing you worked on?"
- If user's process doesn't map to a known framework, design a custom one based on their concepts
- If user insists on a specific framework despite description suggesting otherwise, respect their choice but note any tensions
- If user isn't sure about stages, suggest they start simple (3 stages) and refine later

---

#### Step 2b: Execution Flow Depth Assessment

**Purpose**: Determine the user's current execution flow depth and identify gaps between having stages and having well-defined activities.

**Actions**:

1. Explain execution flow depth:

```
Now let's understand how well-defined your execution flow is.

Execution flow has different levels of depth:

- **Level 2 - Stages**: You have named stages work moves through (e.g., Build → Measure → Learn)
- **Level 3 - Activities**: Within each stage, you have defined activities that happen
- **Level 4 - Triggers**: You know what triggers each activity to start or complete

Most teams have Level 2 (stages) but haven't explicitly defined Level 3 (activities).
```

2. Assess current depth for their framework:

**If Lean (Build → Measure → Learn)**:
```
For your Lean stages, let's check the depth:

**Level 2 - Stages**: ✅ Build → Measure → Learn

**Level 3 - Activities**: For each stage, what activities happen?

**Build stage activities** - which of these do you do?
- [ ] Problem definition / validation
- [ ] Solution sketching / ideation
- [ ] MVP scoping
- [ ] Plan experiment
- [ ] Development / prototyping
- [ ] Other: ___

**Measure stage activities** - which of these do you do?
- [ ] User interviews
- [ ] Transcript analysis
- [ ] Survey deployment
- [ ] A/B testing
- [ ] Analytics review
- [ ] Other: ___

**Learn stage activities** - which of these do you do?
- [ ] Synthesis / pattern identification
- [ ] Insight documentation
- [ ] Pivot/persevere decision
- [ ] Learnings capture
- [ ] Strategy update
- [ ] Other: ___

**Level 4 - Triggers**: When do activities start?
- "After how many interviews do you synthesize?"
- "What triggers a pivot/persevere decision?"
- "When is an experiment 'done'?"
```

**If EOS (Rocks)**:
```
For your EOS rocks, let's check the depth:

**Level 2 - Stages**: ✅ Planning → Execution → Review

**Level 3 - Activities**: For each stage, what activities happen?

**Planning stage activities** - which of these do you do?
- [ ] Rock identification / brainstorming
- [ ] Prioritization / selection
- [ ] Owner assignment
- [ ] Milestone definition
- [ ] Success criteria definition
- [ ] Other: ___

**Execution stage activities** - which of these do you do?
- [ ] Weekly check-ins
- [ ] Milestone completion tracking
- [ ] Blocker identification
- [ ] Progress updates
- [ ] Other: ___

**Review stage activities** - which of these do you do?
- [ ] Rock completion assessment
- [ ] Learnings capture
- [ ] Carryover decisions
- [ ] Next quarter planning
- [ ] Other: ___

**Level 4 - Triggers**: When do activities start?
- "How often do you check in on rock progress?"
- "What triggers a rock to be marked complete vs. incomplete?"
```

**If OKRs**:
```
For your OKRs, let's check the depth:

**Level 2 - Stages**: ✅ Set → Execute → Review

**Level 3 - Activities**: For each stage, what activities happen?

**Set stage activities** - which of these do you do?
- [ ] Objective brainstorming
- [ ] Key Result definition
- [ ] Alignment review (company/team)
- [ ] Owner assignment
- [ ] Initiative planning
- [ ] Other: ___

**Execute stage activities** - which of these do you do?
- [ ] Weekly/bi-weekly check-ins
- [ ] KR progress updates
- [ ] Initiative tracking
- [ ] Blocker resolution
- [ ] Other: ___

**Review stage activities** - which of these do you do?
- [ ] OKR scoring
- [ ] Retrospective
- [ ] Learnings documentation
- [ ] Next cycle planning
- [ ] Other: ___

**Level 4 - Triggers**: When do activities start?
- "How often do you score OKR progress?"
- "What triggers a KR to be marked complete?"
```

3. Capture their current depth:

```
Based on your responses, here's your current execution flow depth:

**Current Depth**: Level [2/3/4]

**Stages defined**: [Yes/No]
**Activities defined**: [Partial/Yes/No]
**Triggers defined**: [Partial/Yes/No]

Would you like to define any missing activities or triggers now, or proceed and add them later?
```

4. **Task Routing**: For each activity identified, ask about execution:

```
One more thing about activities. For each activity, who performs it?

**Task Routing Categories:**
- **AI-supported** — Agent can do most of it (e.g., transcript analysis, research synthesis)
- **Human-only** — Requires your judgment/action (e.g., stakeholder decisions, customer calls)
- **Mixed** — Collaboration between you and agent (e.g., drafting docs, planning experiments)

For your activities:
| Activity | Who performs it? |
|----------|------------------|
| [Activity 1] | [ ] AI-supported [ ] Human-only [ ] Mixed |
| [Activity 2] | [ ] AI-supported [ ] Human-only [ ] Mixed |
| ... | ... |

This helps the agent know when to act vs. when to prompt you.
```

**Validation**:
- User has identified which activities they perform in each stage
- User has identified any triggers they use (or acknowledged they don't have explicit triggers)
- Task routing captured for key activities (or noted as "mixed" by default)
- You understand their current execution flow depth level

---

#### Step 3: Framework Integration (If Multiple Frameworks)

**Purpose**: Understand how multiple frameworks connect and work together.

**Actions**:

If user selected multiple frameworks:

```
You mentioned using [Framework A] and [Framework B] together. Let's understand how they connect.

1. **Relationship**: How do these frameworks relate?
   - Does one provide direction and the other execution?
   - Do artifacts from one map to artifacts in the other?

2. **Example**: Can you walk me through a concrete example?
   - "An Objective like X leads to experiments like Y..."
   - "A Job like X is addressed by rocks like Y..."

3. **Primary structure**: When organizing your memory, which framework provides the primary hierarchy?
   - Should we organize by Objectives first, then experiments within?
   - Or by Strategies first, with OKRs as context?
```

**Validation**:
- Clear understanding of how frameworks connect
- User has identified which framework provides primary organization

---

#### Step 4: Memory Structure Design

**Purpose**: Design the directory structure for the agent's memory based on discovered frameworks.

**Actions**:

1. Based on the frameworks discovered, suggest a memory structure:

**For Lean**:
```
Based on your Lean approach, here's a suggested memory structure:

memory/
├── strategies/
│   └── {strategy-name}/
│       ├── strategy.md          # Strategy definition
│       └── experiments/
│           └── {experiment-name}/
│               ├── experiment.md
│               └── ...          # Supporting artifacts (transcripts, data, etc.)
└── README.md                    # Overview and index

Activities (like problem definition, user interviews, synthesis) will be implemented as Claude Code commands that guide you through each activity and store outputs in the appropriate experiment folder.

Does this match how you think about organizing your work?
```

**For EOS**:
```
Based on your EOS approach, here's a suggested memory structure:

memory/
├── rocks/
│   └── {rock-name}/
│       ├── rock.md              # Rock definition
│       └── milestones/
│           └── {milestone-name}.md
└── README.md                    # Overview and index

Activities (like weekly check-ins, completion assessments, learnings capture) will be implemented as Claude Code commands that guide you through each activity and store outputs in the appropriate rock folder.

Does this match how you think about organizing your work?
```

**For OKRs + Lean**:
```
Based on your OKRs + Lean approach, here's a suggested memory structure:

memory/
├── objectives/
│   └── {objective-name}/
│       ├── objective.md         # Objective and Key Results
│       └── strategies/
│           └── {strategy-name}/
│               ├── strategy.md
│               └── experiments/
│                   └── {experiment-name}/
│                       ├── experiment.md
│                       └── ...  # Supporting artifacts (transcripts, data, etc.)
└── README.md                    # Overview and index

Activities (like problem definition, user interviews, synthesis) will be implemented as Claude Code commands that guide you through each activity and store outputs in the appropriate experiment folder.

Does this match how you think about organizing your work?
```

**For JTBD**:
```
Based on your JTBD approach, here's a suggested memory structure:

memory/
├── jobs/
│   └── {job-name}/
│       ├── job.md               # Job definition and outcomes
│       └── solutions/
│           └── {solution-name}.md
└── README.md                    # Overview and index

Does this match how you think about organizing your work?
```

2. Refine based on user feedback:
```
What would you adjust?
- Different folder names?
- Additional levels of hierarchy?
- Different organization entirely?
```

3. Confirm final structure before proceeding.

**Validation**:
- User has confirmed the memory structure
- Structure clearly maps to their framework artifacts

---

#### Step 4b: State Persistence (Work Logging)

**Purpose**: Determine how the user wants to track progress and maintain state across sessions.

**Actions**:

1. Explain state persistence and offer options:

```
Now let's talk about state persistence — how you track progress and maintain context.

This is what enables "where was I?" when you come back after interruption. There are two main approaches:

**Option A: Git-based (automatic)**
- Every interaction automatically creates a commit via hooks
- Access history via `git log`
- No extra files to manage
- Requires git setup

**Option B: Markdown-based (explicit)**
- Log completions to markdown files (like git commits, but human-readable)
- Visible in your file system
- Agent writes to log after each activity
- Works without git

**Option C: Both**
- Git for granular automatic history
- Markdown for human-readable summaries

Which approach matches how you like to work?
```

2. **If Option A (Git-based)**:

```
Great! Git-based logging keeps things clean.

I'll add this to your CLAUDE.md:

### Git Workflow
Git branches and commit strategy are automatically handled under the hood.
After every message sent by the user and response by the agent, a commit is
automatically created using hooks. You don't need to manually manage branching
or commit messages.

Note: You'll need to set up git hooks separately. Would you like guidance on that?
```

3. **If Option B (Markdown-based)**:

```
Markdown logging keeps everything visible and human-readable.

Where should work logs live?
A) **Central log** — Single file at `memory/work-log.md`
B) **Per-artifact logs** — Each artifact folder has its own log (e.g., `rock/work-log.md`)
C) **Both** — Central summary + detailed per-artifact logs

What format do you prefer for log entries?
- **Git-commit style**: `| Date | Activity | Artifact | Notes |`
- **Simple list**: `- [date] Completed X for Y`
- **Other**: Describe your preference
```

4. **If Option C (Both)**:

```
Using both gives you the best of both worlds.

I'll set up:
- Git hooks for automatic granular history
- Markdown log at `memory/work-log.md` for human-readable summaries

The agent will write to the markdown log after completing activities, and git will capture everything automatically.
```

5. Confirm state persistence approach:

```
Here's your state persistence setup:

**Approach**: [Git-based / Markdown-based / Both]
**Log location**: [N/A / memory/work-log.md / per-artifact]
**Log format**: [N/A / git-commit style / simple list]

This enables:
- ✅ "Where was I?" resumption
- ✅ Progress tracking over time
- ✅ Audit trail of completed work

Does this work for you?
```

**Validation**:
- User has selected a state persistence approach
- Log location confirmed (if markdown-based)
- Log format confirmed (if markdown-based)

**Error Handling**:
- If user is unsure, suggest Option B (Markdown-based) as the simplest starting point
- Can always add git hooks later

---

#### Step 5: Template Discovery & Creation

**Purpose**: Understand what templates the user needs and either capture existing ones or help create them.

**Actions**:

1. Ask about templates:
```
Now let's talk about templates. Templates help ensure consistency when creating new artifacts.

Do you have existing templates for any of these? (Or would you like to create them?)

Based on your framework, you might want templates for:
[List relevant artifact types based on discovered framework]

For example:
- experiment.md - Template for new experiments
- strategy.md - Template for new strategies
- rock.md - Template for new rocks

Do you:
A) Have existing templates you'd like to use?
B) Want to create templates together now?
C) Skip templates for now (you can add them later)?
```

2. **If user has existing templates**:
```
Please share your template for [artifact type]. You can:
- Paste the markdown content here
- Or tell me the structure and I'll help format it
```

3. **If user wants to create templates**:

For each artifact type, guide them through creation:

```
Let's create a template for [artifact type].

What information should every [artifact] include?

Here's a starting point - adjust as needed:

---
# {Name}

## Overview
{Brief description}

## [Field 1]
{Description}

## [Field 2]
{Description}

## Status
- [ ] {Stage 1}
- [ ] {Stage 2}
- [ ] {Stage 3}
---

What would you add, remove, or change?
```

4. **Confirm template storage location**:
```
Templates will be stored in:

templates/
├── {artifact-type}.md
├── {artifact-type}.md
└── README.md

These will be referenced in your CLAUDE.md so the agent knows to use them.
```

5. **Offer Activity Commands** (if user defined activities in Step 2b):

Based on the execution flow depth discovered earlier, offer to create Claude Code commands for activities:

```
Activities are best implemented as Claude Code commands. Each command guides you through the activity and stores the output in the right place.

Based on your execution flow, you might want commands for these activities:
```

**If Lean with activities defined**:
```
**Build stage commands:**
- /define_problem - Guide through problem definition, store in experiment folder
- /scope_mvp - Guide through MVP scoping, store in experiment folder
- /plan_experiment - Guide through experiment planning, define hypothesis and success criteria

**Measure stage commands:**
- /conduct_interview - Guide through user interview, create interview notes
- /analyze_transcript - Guide through transcript analysis
- /synthesize - Guide through synthesis of findings

**Learn stage commands:**
- /capture_learnings - Guide through documenting experiment learnings
- /decide_pivot_persevere - Guide through pivot/persevere decision

Would you like to create commands for any of these activities? We can create them now or you can add them later using `/create_agent_command`.
```

**If EOS with activities defined**:
```
**Planning stage commands:**
- /define_rock - Guide through rock definition
- /set_success_criteria - Guide through defining success criteria

**Execution stage commands:**
- /add_milestone - Create a new milestone for a rock
- /weekly_checkin - Guide through weekly rock check-in

**Review stage commands:**
- /assess_completion - Guide through rock completion assessment
- /capture_rock_learnings - Guide through capturing learnings

Would you like to create commands for any of these activities?
```

**If OKRs with activities defined**:
```
**Set stage commands:**
- /define_objective - Guide through objective definition
- /add_key_result - Add a key result to an objective

**Execute stage commands:**
- /okr_checkin - Guide through OKR check-in
- /track_initiative - Track progress on an initiative

**Review stage commands:**
- /score_okrs - Guide through OKR scoring
- /run_retrospective - Guide through cycle retrospective

Would you like to create commands for any of these activities?
```

6. **If user wants activity commands**, note them for creation after the agent is set up:

```
Great! I'll note that you want these activity commands:
- [List selected commands]

After we finish setting up your agent, you can create these commands using `/create_agent_command` in your new agent repository. Each command will:
1. Guide you through the activity step-by-step
2. Ask for the relevant information
3. Store the output in the correct location in your memory structure
```

**Validation**:
- User has confirmed which templates they want
- Template content has been captured or created
- User understands where templates will be stored
- Activity commands identified if user has defined activities

---

#### Step 6: Generate CLAUDE.md

**Purpose**: Create the CLAUDE.md file that defines the Org Organisation OS.

**Framework-Specific Titles**:

Before generating, select an appropriate title based on the frameworks chosen:

- **Lean** → "Lean Agent" or "Lean Product Agent"
- **OKRs** → "OKR Agent"
- **JTBD** → "Jobs-to-be-Done Agent"
- **EOS** → "Rocks Agent" or "EOS Agent"
- **OKRs + Lean** → "Lean OKR Agent"
- **OKRs + EOS** → "OKR-EOS Agent"
- **Custom/Multiple** → Use the primary framework name + "Agent" (e.g., "Hybrid Product Agent")

**Actions**:

1. Generate the CLAUDE.md with all discovered information, using the appropriate title:

```markdown
# {Framework-Specific Title}

A Claude Code agent that helps operationalize {framework-specific description} by managing artifacts, tracking progress, and maintaining organizational memory.

## Operator Profile

- **Name**: [User's name]
- **Role**: [User's role]
- **Company/Project**: [Company or project name]
- **Productivity peaks**: [When they do best work]
- **Work style**: [How they prefer to work]
- **Tools**: [Tools they use]

## Framework

This agent supports the following framework(s):

### [Framework Name]

[User's description of how they use this framework]

**Key Concepts**:
- [Concept 1]: [Definition]
- [Concept 2]: [Definition]
- [Concept 3]: [Definition]

**Hierarchy**:
[Description of how artifacts relate]

[Repeat for each framework]

### Framework Integration

[If multiple frameworks, describe how they connect]

## Memory Structure

The agent maintains memory in the following structure:

```
memory/
├── [structure as designed in Step 4]
```

### Directory Purposes

- **`memory/[dir1]/`**: [Purpose]
- **`memory/[dir1]/[subdir]/`**: [Purpose]

### File Naming Conventions

- Use kebab-case for all file and folder names
- [Any other conventions discovered]

## Execution Flow

**Current Depth:** Level [2/3/4] ([Stages/Activities/Triggers])

### Stages

1. **[Stage 1]**: [Description of what happens in this stage]
2. **[Stage 2]**: [Description of what happens in this stage]
3. **[Stage 3]**: [Description of what happens in this stage]

### Activities by Stage

| Stage | Activity | Command | Trigger | Routing |
|-------|----------|---------|---------|---------|
| [Stage 1] | [Activity 1] | `/[command]` | [When this activity starts] | [AI/Human/Mixed] |
| [Stage 1] | [Activity 2] | `/[command]` | [When this activity starts] | [AI/Human/Mixed] |
| [Stage 2] | [Activity 1] | `/[command]` | [When this activity starts] | [AI/Human/Mixed] |
| [Stage 2] | [Activity 2] | `/[command]` | [When this activity starts] | [AI/Human/Mixed] |
| [Stage 3] | [Activity 1] | `/[command]` | [When this activity starts] | [AI/Human/Mixed] |
| [Stage 3] | [Activity 2] | `/[command]` | [When this activity starts] | [AI/Human/Mixed] |

### Task Routing

- **AI-supported**: Agent can perform with minimal input (e.g., transcript analysis, research)
- **Human-only**: Requires operator judgment or action (e.g., decisions, customer calls)
- **Mixed**: Collaboration between operator and agent (e.g., drafting, planning)

### Activity Commands

Activities are implemented as Claude Code commands in `.claude/commands/`:

| Command | Purpose | Output Location |
|---------|---------|-----------------|
| `/[command]` | [What this command guides the user through] | `memory/[path]/` |

[Note: Commands can be created using `/create_agent_command`]

## Templates

Templates are stored in `templates/` and should be used when creating new artifacts.

| Template | Purpose | Used For |
|----------|---------|----------|
| [template-name.md](./templates/template-name.md) | [Description] | Creating new [artifact type] |

### Using Templates

When the user asks to create a new [artifact]:
1. Copy the template from `templates/[artifact].md`
2. Place it in the appropriate memory location
3. Fill in the template fields based on user input

## State Persistence

[If Git-based]:
### Git Workflow
Git branches and commit strategy are automatically handled under the hood. After every message sent by the user and response by the agent, a commit is automatically created using hooks. You don't need to manually manage branching or commit messages.

[If Markdown-based]:
### Work Log
After completing any activity, log it to the work log:
- **Location**: `memory/work-log.md` [or per-artifact]
- **Format**: `| Date | Activity | Artifact | Notes |`
- **Purpose**: Enables "where was I?" resumption and audit trail

When resuming work, check the work log to restore context.

[If Both]:
### Git Workflow
Git branches and commit strategy are automatically handled under the hood. After every message sent by the user and response by the agent, a commit is automatically created using hooks.

### Work Log
Additionally, maintain a human-readable log at `memory/work-log.md`:
- **Format**: `| Date | Activity | Artifact | Notes |`
- **Purpose**: Quick summary view and "where was I?" resumption

## Agent Capabilities

### Core Functions

- **Create artifacts**: Create new [experiments/rocks/strategies/etc.] using templates
- **Track progress**: Update status and track progress on artifacts
- **Navigate memory**: Help users find and reference existing artifacts
- **Maintain consistency**: Ensure all artifacts follow the established structure

### Common Commands

- "Create a new [artifact]" - Creates artifact using template in correct location
- "Show me all [artifacts]" - Lists artifacts from memory
- "Update [artifact name]" - Opens and updates an existing artifact
- "What's the status of [artifact]?" - Summarizes artifact status

## Workflows

### Creating a New [Primary Artifact Type]

1. User requests a new [artifact]
2. Ask for required information: [list fields]
3. Create file at `memory/[path]/[name].md` using template
4. Confirm creation with user

### [Additional workflows based on framework]

## Conventions

- Always use templates when creating new artifacts
- Maintain the memory structure - don't create files outside defined paths
- Use kebab-case for file and folder names
- Update artifact status as work progresses
- Keep memory README.md updated as an index
```

2. Select the appropriate title based on frameworks discovered:

Based on the frameworks you selected, here are some title options:
- [Option 1]: [Description of what this emphasizes]
- [Option 2]: [Description of what this emphasizes]
- [Option 3]: [Description of what this emphasizes]

Which resonates best with how you think about this agent, or would you prefer something different?

3. Once title is confirmed, show the generated CLAUDE.md to the user:
```
Here's the CLAUDE.md I've generated based on our conversation:

[Show full content with confirmed title]

Does this accurately capture your framework and how you want the agent to work?

What would you adjust?
```

4. Refine based on feedback until user approves.

**Validation**:
- User has reviewed and approved the CLAUDE.md
- All frameworks are accurately represented
- Memory structure matches what was designed
- Templates are correctly referenced

---

#### Step 7: Create Directory Structure & Files

**Purpose**: Create the initial memory structure, templates directory, and all files.

**Actions**:

1. Create the directory structure:
   - Create `memory/` directory with subdirectories as designed
   - Add `.gitkeep` files to empty directories
   - Create `memory/README.md` as an index

2. Create templates directory and files:
   - Create `templates/` directory
   - Create each template file with the content designed in Step 5
   - Create `templates/README.md` listing all templates

3. Create the CLAUDE.md file at the repository root

4. Report what was created:
```
I've created the following structure:

[Show tree of created directories and files]

Files created:
- CLAUDE.md - Your agent's system prompt
- memory/README.md - Index for your memory structure
- templates/[name].md - Template for [artifact type]
- [etc.]

Your Org Organisation OS is ready to use!
```

**Validation**:
- All directories created successfully
- All template files created with correct content
- CLAUDE.md created with approved content
- memory/README.md created as index

**Error Handling**:
- If files already exist, ask user whether to overwrite or merge
- If directory creation fails, report error and suggest manual creation

---

#### Step 7.5: Generate README Dashboard

**Purpose**: Create a visually engaging README.md at the repository root that serves as a progress dashboard for the user's product framework.

**Actions**:

1. Generate the README.md dashboard based on the discovered framework:

```markdown
# 🎯 {Project/Agent Name}

> {One-line description based on framework - e.g., "Operationalizing Lean experimentation for validated learning" or "Driving quarterly rocks to completion with EOS"}

**Current Period**: {Suggest appropriate period - Q1 2025, Sprint 1, etc.}

---

## 🎯 Active {Top-level concept}

> **{Name of active top-level item}**
>
> {Brief description or strategic intent}

**Hypotheses:**
- {Hypothesis 1 - what you believe to be true}
- {Hypothesis 2 - what you're testing}
- {Hypothesis 3 - key assumption to validate}

> 💡 _To get started: migrate an existing {top-level concept} doc to `memory/{top-level-concept}/`, or ask the agent "Create a new {top-level concept}"_

---

## 📊 Progress Overview

| Status | {Mid-level artifact} | Progress | Due | Owner |
|--------|----------------------|----------|-----|-------|
| 🟢 | _Example: Pricing page A/B test_ | ████░░░░░░ 40% | Jan 31 | @team |
| 🟡 | _Example: Onboarding flow experiment_ | ██░░░░░░░░ 20% | Feb 15 | @team |
| ⏸️ | _Example: Referral program test_ | ░░░░░░░░░░ 0% | TBD | — |

> 💡 _Add your {mid-level artifacts} here as you create them_

---

## 🔄 Execution Flow

**{Stage 1}** → **{Stage 2}** → **{Stage 3}**

| Stage | Activities | Command |
|-------|------------|---------|
| **{Stage 1}** | {Activity 1} | `/[command]` |
| | {Activity 2} | `/[command]` |
| **{Stage 2}** | {Activity 1} | `/[command]` |
| | {Activity 2} | `/[command]` |
| **{Stage 3}** | {Activity 1} | `/[command]` |
| | {Activity 2} | `/[command]` |

> 💡 _Run activity commands to guide you through each step and store outputs in the right place_

---

## 🗂️ Structure

```
memory/
├── {top-level-concept}/           # {Description - e.g., "Strategies", "Rocks", "Objectives"}
│   └── {mid-level-concept}/       # {Description - e.g., "Experiments", "Milestones", "Key Results"}
│       └── {artifact}.md          # {Description - e.g., "Individual experiment files"}
└── README.md                      # Memory index
```

---

## 📈 Quick Stats

| Metric | Value |
|--------|-------|
| 📊 {Top-level} Active | 0 |
| 🧪 {Mid-level} Running | 0 |
| ✅ Completed This Period | 0 |
| 🎯 Days Remaining | — |

---

## 🚦 Status Legend

| Icon | Status | Meaning |
|------|--------|---------|
| 🟢 | On Track | Progressing as expected |
| 🟡 | At Risk | Needs attention, may slip |
| 🔴 | Blocked | Cannot progress, needs intervention |
| ✅ | Complete | Successfully finished |
| ⏸️ | Paused | On hold, not currently active |

---

## 📝 Recent Activity

| Date | Activity |
|------|----------|
| {Today's date} | 🎉 Agent initialized with {framework} framework |

---

## 🔗 Resources

| Resource | Purpose | Link |
|----------|---------|------|
| System Prompt | Agent specification | [CLAUDE.md](./CLAUDE.md) |
| Memory | Artifacts & progress | [memory/](./memory/) |
| Templates | Artifact templates | [templates/](./templates/) |
| Commands | Custom workflows | [.claude/commands/](./.claude/commands/) |

---

_Dashboard generated by Product Ops Agent • {Framework name}_
```

2. **Customize the dashboard based on framework**:

**For Lean**:
- Top-level: Strategies
- Mid-level: Experiments
- Artifact: Hypothesis/Learning
- Period suggestion: "Q1 2025" or "Month: January 2025"
- Execution Flow:
  - Stages: Build → Measure → Learn
  - Build activities: `/define_problem`, `/scope_mvp`, `/plan_experiment`
  - Measure activities: `/conduct_interview`, `/analyze_transcript`, `/synthesize`
  - Learn activities: `/capture_learnings`, `/decide_pivot_persevere`

**For EOS**:
- Top-level: Rocks
- Mid-level: Milestones
- Artifact: To-dos
- Period suggestion: "Q1 2025 (90-Day Rocks)"
- Execution Flow:
  - Stages: Planning → Execution → Review
  - Planning activities: `/define_rock`, `/set_success_criteria`
  - Execution activities: `/add_milestone`, `/weekly_checkin`
  - Review activities: `/assess_completion`, `/capture_rock_learnings`

**For OKRs**:
- Top-level: Objectives
- Mid-level: Key Results
- Artifact: Initiatives
- Period suggestion: "Q1 2025" or "Annual 2025"
- Execution Flow:
  - Stages: Set → Execute → Review
  - Set activities: `/define_objective`, `/add_key_result`
  - Execute activities: `/okr_checkin`, `/track_initiative`
  - Review activities: `/score_okrs`, `/run_retrospective`

**For JTBD**:
- Top-level: Jobs
- Mid-level: Outcomes
- Artifact: Solutions
- Period suggestion: Omit or use "Current Focus"
- Execution Flow:
  - Stages: Discover → Define → Deliver
  - Discover activities: `/interview_for_jobs`, `/map_job`
  - Define activities: `/define_outcomes`, `/prioritize_outcomes`
  - Deliver activities: `/propose_solution`, `/validate_solution`

**For OKRs + Lean (combined)**:
- Top-level: Objectives
- Mid-level: Strategies → Experiments
- Artifact: Learnings
- Period suggestion: "Q1 2025"
- Execution Flow:
  - Stages: Build → Measure → Learn (within experiments)
  - Build activities: `/define_problem`, `/scope_mvp`, `/plan_experiment`
  - Measure activities: `/conduct_interview`, `/synthesize`
  - Learn activities: `/capture_learnings`, `/decide_pivot_persevere`

3. **Ask user for customization**:

```
I've generated a README dashboard for tracking your {framework} progress.

A few questions to customize it:

1. **Project/Agent Name**: What should the header say? (e.g., "Growth Experiments", "Q1 Rocks", "Product Discovery")

2. **Current Period**: What timeframe are you tracking? (e.g., "Q1 2025", "Sprint 3", "January 2025")

3. **Adjust the structure?** Does the folder structure description match your mental model?
```

4. **Finalize and create the README.md** at the repository root after user confirmation.

**Validation**:
- README.md created at repository root
- Dashboard reflects the discovered framework structure
- Status legend matches artifact lifecycle
- Quick stats section ready for tracking
- User has confirmed the project name and period

**Example Output** (for Lean framework):

```markdown
# 🎯 Product Discovery

> Operationalizing Lean experimentation for validated learning

**Current Period**: Q1 2026

---

## 🎯 Active Strategy

> **{Your strategy name here}**
>
> {Brief description of what you're trying to learn or achieve}

**Hypotheses:**
- {What you believe about your customers}
- {What you believe about the problem}
- {What you believe about the solution}

> 💡 _To get started: migrate an existing strategy doc to `memory/strategies/`, or ask the agent "Create a new strategy"_

---

## 📊 Progress Overview

| Status | Experiment | Progress | Due | Owner |
|--------|------------|----------|-----|-------|
| 🟢 | _Add your first experiment_ | ░░░░░░░░░░ 0% | — | — |

> 💡 _Create experiments with: "Create a new experiment called X"_

---

## 🔄 Execution Flow

**Build** → **Measure** → **Learn**

| Stage | Activities | Command |
|-------|------------|---------|
| **Build** | Define problem | `/define_problem` |
| | Scope MVP | `/scope_mvp` |
| | Plan experiment | `/plan_experiment` |
| **Measure** | Conduct interview | `/conduct_interview` |
| | Analyze transcript | `/analyze_transcript` |
| | Synthesize findings | `/synthesize` |
| **Learn** | Capture learnings | `/capture_learnings` |
| | Decide pivot/persevere | `/decide_pivot_persevere` |

> 💡 _Run activity commands to guide you through each step and store outputs in the right place_

---

## 🗂️ Structure

```
memory/
├── strategies/                    # Strategic focus areas
│   └── {strategy-name}/
│       ├── strategy.md           # Strategy definition
│       └── experiments/          # Experiments testing this strategy
│           └── {experiment}.md
└── README.md                      # Memory index
```

---

## 📈 Quick Stats

| Metric | Value |
|--------|-------|
| 📊 Strategies Active | 0 |
| 🧪 Experiments Running | 0 |
| ✅ Completed This Quarter | 0 |
| 🎯 Days Remaining in Q1 2026 | — |

---

## 🚦 Status Legend

| Icon | Status | Meaning |
|------|--------|---------|
| 🟢 | On Track | Experiment progressing as planned |
| 🟡 | At Risk | May not complete in time, needs attention |
| 🔴 | Blocked | Cannot proceed, dependency or issue |
| ✅ | Complete | Experiment finished, learning captured |
| ⏸️ | Paused | On hold, not currently running |

---

## 📝 Recent Activity

| Date | Activity |
|------|----------|
| Jan 6, 2026 | 🎉 Agent initialized with Lean framework |

---

## 🔗 Resources

| Resource | Purpose | Link |
|----------|---------|------|
| System Prompt | Agent specification | [CLAUDE.md](./CLAUDE.md) |
| Memory | Strategies & experiments | [memory/](./memory/) |
| Templates | Strategy & experiment templates | [templates/](./templates/) |

---

_Dashboard generated by Lean Product Agent_
```

---

#### Step 8: Confirmation & Next Steps

**Purpose**: Confirm success and guide user on next steps.

**Actions**:

```
Your Org Organisation OS is set up and ready!

**What was created:**
- README.md dashboard for tracking progress on your [framework]
- CLAUDE.md defining your Org OS framework and capabilities
- Memory structure at `memory/` matching your [framework] approach
- Templates at `templates/` for creating consistent artifacts

**Next steps:**

1. **Test the agent**: Try asking it to create a new [artifact type]
   - "Create a new experiment called X"
   - "Start a new rock for Q1"

2. **Customize further**: You can always edit:
   - CLAUDE.md to refine agent behavior
   - Templates to add/remove fields
   - Memory structure as your needs evolve

3. **Populate memory**: Start adding your existing [artifacts] to the memory structure

Would you like help with any of these next steps?
```

**Output Format**:
```
Org Organisation OS initialized successfully!

Framework(s): [Lean, OKRs, etc.]
Memory structure: memory/[top-level-dir]/...
Templates: templates/[list]

Your Org OS is ready to help operationalize your organizational workflow.
```

## File Structure & Paths

### Files Created

```
{repo-root}/
├── README.md                    # Progress dashboard
├── CLAUDE.md                    # Agent system prompt
├── memory/
│   ├── README.md               # Memory index
│   └── {framework-specific}/   # Directories per framework
│       └── .gitkeep
└── templates/
    ├── README.md               # Template index
    └── {artifact-type}.md      # Template files
```

### Path Conventions

- **Repository root**: All paths relative to where command is invoked
- **Memory directory**: Always `memory/` at repo root
- **Templates directory**: Always `templates/` at repo root
- **File names**: kebab-case (e.g., `my-experiment.md`)

## Validation & Testing

### Success Criteria

- [ ] Operator profile captured in CLAUDE.md
- [ ] User's frameworks accurately captured in CLAUDE.md
- [ ] Memory structure matches user's mental model
- [ ] Task routing defined for key activities
- [ ] State persistence approach configured
- [ ] Templates created for relevant artifact types
- [ ] Directory structure created and ready to use
- [ ] README.md dashboard created with framework-specific structure
- [ ] User understands how to use the agent

### Test Cases

1. **Single framework (Lean)**: Should produce strategies/experiments structure
2. **Single framework (EOS)**: Should produce rocks/milestones structure
3. **Combined frameworks (OKRs + Lean)**: Should produce integrated hierarchy
4. **Custom framework**: Should adapt to user-defined concepts
5. **With templates**: Should create template files in templates/
6. **Without templates**: Should skip template creation gracefully

## Conversation Guidelines

### Be Patient & Exploratory

- Users may not have precise language for their framework
- Ask clarifying questions without judgment
- Offer examples to help users articulate their approach

### Validate Understanding

- Summarize back what you've heard before moving on
- "So if I understand correctly, you organize by X, then Y within that?"
- Give users opportunity to correct misunderstandings

### Suggest, Don't Prescribe

- Offer suggested structures based on frameworks
- Always ask "Does this match how you think about it?"
- Be ready to adapt to user's mental model

### Make It Concrete

- Use examples: "So an experiment might be called 'Test pricing page headline'?"
- Show actual directory structures, not abstract descriptions
- Create real template content, not placeholders

## Integration Notes

### Related Commands

- `/init_agent`: Use first if the agent repository doesn't exist yet
- `/create_agent_command`: Add custom commands to the Product Ops Agent after setup
- `/create_agent_feature`: Add additional capabilities to the agent

### Prerequisites

This command assumes a repository already exists. If not, guide user to run `/init_agent` first.
