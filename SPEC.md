# ORG.md Specification v0.1

**A simple, open format for organizational operating systems.**

Think of it as an AGENTS.md for how your organization runs—not code, but operations.

---

## What is ORG.md?

ORG.md is a machine-readable specification that describes how a product organization operates. It provides the context AI agents need to assist with planning, execution, and decision-making within your organizational framework.

Just as AGENTS.md tells coding agents how to work on your codebase, ORG.md tells operational agents how to work within your organization.

## Why ORG.md?

README files describe what a project is. ORG.md describes how work gets done:

| README.md | ORG.md |
|-----------|--------|
| Project description | Organizational framework |
| Getting started guide | Operator profile & context |
| Contribution guidelines | Workflows & commands |
| Feature documentation | Templates & artifacts |

Without ORG.md, every AI interaction starts from scratch. With it, agents understand your methodology, respect your time, and produce artifacts in your format.

---

## Specification

An ORG.md file uses standard Markdown. The following sections are recommended but not required—use what fits your organization.

Start your ORG.md with a header block:

```markdown
# {OS Name} Agent

{One-line description of what this agent operationalizes}
```

---

### 1. Operator Profile

Who's running this OS? The agent should know its user.

```markdown
## 1. Operator Profile

- **Name**: [Your name]
- **Role**: [Your role/title]
- **Company**: [Your company/org]
- **Productivity peaks**: [e.g., "mornings for deep work"]
- **Work style**: [e.g., "30-minute time blocks", "async-first"]
```

**Purpose**: Personalization. An agent that knows you're a morning person won't schedule strategy work at 4pm.

### 2. Framework

What methodology are you encoding? Define the core concepts and how they relate.

```markdown
## 2. Framework

### Methodology
[Name of your operating methodology—EOS, OKRs, custom, etc.]

### Core Concepts
- **[Concept 1]**: [Definition and purpose]
- **[Concept 2]**: [Definition and purpose]
- **[Concept 3]**: [Definition and purpose]

### Hierarchy
[How concepts relate: Objectives → Key Results → Tasks, or Rocks → Milestones → Actions]

### Cadence
- **[Cycle type]**: [Duration and purpose]
- **[Review type]**: [Frequency and format]
```

**Purpose**: Shared vocabulary. When you say "rock," the agent knows you mean a 90-day priority, not a geological formation.

### 3. Memory Structure (File System)

Where do artifacts live? Define the directory structure and naming conventions.

```markdown
## 3. Memory Structure

### Structure
memory/
├── {top-level}/
│   └── {name}/
│       ├── {artifact}.md
│       └── ...
└── ...

### Directory Purposes
- `memory/{x}/`: {purpose}
- `memory/{y}/`: {purpose}

### Naming Conventions
- **{Artifact type}**: `{naming-pattern}.md`
- **{Artifact type}**: `{naming-pattern}.md`

### Locations
- **Active work**: [Path to current priorities]
- **Archive**: [Path to completed work]
- **Reference**: [Path to permanent resources]
```

**Purpose**: Predictability. The agent knows where to create files and where to find context.

### 4. Execution Flow (Scheduler)

What triggers activities? How do you match tasks to available time? What stages does work move through?

```markdown
## 4. Execution Flow

### Stages
1. **{Stage 1}**: {description}
2. **{Stage 2}**: {description}
3. **{Stage 3}**: {description}

### Activities by Stage
| Stage | Activity | Command | Trigger |
|-------|----------|---------|---------|
| {Stage} | {Activity} | `/{command}` | {When it fires} |

### Task Routing
| Type | Description | Executor |
|------|-------------|----------|
| AI-supported | {description} | Agent |
| Human-only | {description} | Operator |
| Mixed | {description} | Collaboration |

### Approval Gates
- {What needs sign-off before proceeding}
- {Budget thresholds, public commitments, etc.}

### Triggers
- **Daily**: [What happens each day]
- **Weekly**: [What happens each week]
- **Quarterly**: [What happens each quarter]
```

**Purpose**: Timing intelligence. The agent knows the workflow stages, when to suggest deep work vs. quick tasks, and what it can do autonomously.

### 5. State Persistence (Work Log)

How do you log progress? Without this, "where was I?" doesn't work.

```markdown
## 5. State Persistence

### Progress Tracking
- **Format**: [How completions are logged]
- **Location**: [Where state is persisted]
- **Granularity**: [Task-level, day-level, etc.]
- **What to capture**: {what gets logged—completions, blockers, decisions, etc.}

### Status Values
- `not_started` | `in_progress` | `blocked` | `complete`

### Context Restoration
[How an agent should reconstruct context after a break]
1. Read today's log (if exists)
2. Check active {artifacts} for current status
3. Review last N logs for context
4. Flag any items marked `blocked`
```

**Purpose**: Continuity. Like git commits for your work, this enables resumption without re-explanation.

### 6. Templates

What's the structure of each artifact? Consistent formats let agents create and parse reliably.

```markdown
## 6. Templates

### [Artifact Type]
Location: `templates/[artifact-type].md`
Purpose: [When this template is used]
Required fields: [Fields that must be filled]

### [Artifact Type]
...
```

**Purpose**: Standardization. The agent produces artifacts in your format, not generic output.

### 7. Commands

What operations does the OS support? Define the interfaces for common workflows.

```markdown
## 7. Commands

### `/[command-name]`
**Purpose**: [What this command does]
**Input**: [What the agent needs]
**Output**: [What the agent produces]
**Example**: [Sample usage]

### `/[command-name]`
...
```

**Purpose**: Defined interfaces. Instead of vague requests, you have reliable operations.

---

## File Placement

Place `ORG.md` at the root of your organizational workspace. For complex organizations:

```
/org/
├── ORG.md              # Organization-wide defaults
├── product/
│   └── ORG.md          # Product team specifics
├── engineering/
│   └── ORG.md          # Engineering team specifics
└── operations/
    └── ORG.md          # Ops team specifics
```

Agents read the nearest ORG.md to the current context. Child files inherit from and override parent files.

---

## Best Practices

1. **Keep it under 200 lines.** Long files bury signal.
2. **Be concrete, not abstract.** Show actual paths, actual templates, actual commands.
3. **Update quarterly.** Your OS should evolve with your organization.
4. **Start minimal.** Add sections as you need them, not before.
5. **Test with your agent.** The best spec is one that actually improves agent behavior.

---

## Ecosystem

ORG.md is designed to work with:
- AI assistants (Claude, GPT, etc.)
- Task management tools
- Note-taking systems
- Calendar integrations
- Any tool that can read Markdown

---

## Contributing

ORG.md is an open specification. Contributions, feedback, and real-world examples welcome.

---

## License

Creative Commons Attribution 4.0 International (CC BY 4.0)
