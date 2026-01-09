# Example: EOS Product Team ORG.md

```markdown
# EOS Product Agent

Operationalizes modified EOS methodology for a product team with quarterly rocks and weekly L10 meetings.

## 1. Operator Profile

- **Name**: Sarah Chen
- **Role**: Head of Product
- **Company**: Acme Corp
- **Productivity peaks**: 6am-10am for deep work, 2pm-4pm for creative
- **Work style**: Async-first, 30-minute time blocks, batch meetings Tue/Thu

## 2. Framework

### Methodology
Modified EOS (Entrepreneurial Operating System) with quarterly rocks and weekly L10 meetings.

### Core Concepts
- **Rock**: 90-day priority with measurable outcome. Max 3 per quarter.
- **Experiment**: Time-boxed hypothesis test. 2-4 week sprints.
- **Objective**: North star metric we're moving. One per quarter.
- **Issue**: Blocker or decision needing resolution.

### Hierarchy
Objective (quarterly)
└── Rocks (90-day)
    └── Milestones (2-week)
        └── Tasks (daily)

### Cadence
- **Quarterly**: Rock setting, objective review (Week 1 of quarter)
- **Weekly**: L10 meeting (Monday 10am), rock check-in
- **Daily**: Task completion log, blocker flag

## 3. Memory Structure

### Structure
memory/
├── rocks/
│   ├── 2025-Q1/
│   │   └── launch-mobile-app.md
│   └── 2025-Q2/
├── experiments/
│   ├── active/
│   │   └── EXP-042-pricing-tier-test.md
│   └── archive/
├── decisions/
│   └── DEC-2025-01-15-api-versioning.md
├── reviews/
│   ├── weekly/
│   └── quarterly/
└── state/
    └── daily-logs/
        └── 2025-01-15.md

### Directory Purposes
- `memory/rocks/`: Quarterly priorities with measurable outcomes
- `memory/experiments/`: Hypothesis tests, active and archived
- `memory/decisions/`: Decision logs for the record
- `memory/reviews/`: Weekly and quarterly retrospectives
- `memory/state/`: Progress tracking and daily logs

### Naming Conventions
- **Rocks**: `YYYY-QN-rock-slug.md` (e.g., `2025-Q1-launch-mobile-app.md`)
- **Experiments**: `EXP-NNN-hypothesis-slug.md` (e.g., `EXP-042-pricing-tier-test.md`)
- **Decisions**: `DEC-YYYY-MM-DD-title.md` (e.g., `DEC-2025-01-15-api-versioning.md`)
- **Daily logs**: `YYYY-MM-DD.md`

### Locations
- **Active work**: `memory/rocks/2025-Q1/`
- **Current experiments**: `memory/experiments/active/`
- **Reference**: `memory/decisions/`

## 4. Execution Flow

### Stages
1. **Build**: Define rocks, create experiments, plan milestones
2. **Measure**: Track progress, collect data, log completions
3. **Learn**: Review results, make decisions, adjust course

### Activities by Stage
| Stage | Activity | Command | Trigger |
|-------|----------|---------|---------|
| Build | Create new rock | `/new-rock` | Quarter start |
| Build | Start experiment | `/start-experiment` | As needed |
| Measure | Log daily progress | `/daily-log` | Daily at 5pm |
| Measure | Check rock status | `/rock-status` | Monday 9am |
| Learn | Generate weekly update | `/weekly-update` | Friday 4pm |
| Learn | Log decision | `/decision` | After major choices |

### Task Routing
| Type | Description | Executor |
|------|-------------|----------|
| AI-supported | Draft documents, summarize notes, generate updates, research | Agent |
| Human-only | Final rock selection, hiring, customer escalations, strategy | Operator |
| Mixed | Experiment analysis, decision framing, milestone planning | Collaboration |

### Approval Gates
- Experiments over $5k budget
- Public commitments
- Headcount changes

### Triggers
- **Daily at 5pm**: Log completed tasks, flag blockers
- **Monday 9am**: Generate weekly rock progress summary
- **Friday 4pm**: Draft weekly stakeholder update
- **Quarter end**: Generate rock completion report

## 5. State Persistence

### Progress Tracking
- **Format**: Daily markdown log with task checklist
- **Location**: `memory/state/daily-logs/`
- **Granularity**: Task-level with time spent
- **What to capture**: Completions, blockers, decisions made, tomorrow's priorities

### Status Values
- `not_started` - Queued but not begun
- `in_progress` - Actively working
- `blocked` - Waiting on dependency
- `complete` - Done and verified

### Context Restoration
When resuming work:
1. Read today's daily log (if exists)
2. Check active rocks for current milestone
3. Review last 3 daily logs for context
4. Flag any items marked `blocked`

## 6. Templates

### Rock
Location: `templates/rock.md`
Purpose: Define a 90-day priority
Required fields: objective, success_metric, milestones[], owner

### Experiment
Location: `templates/experiment.md`
Purpose: Define a hypothesis to test
Required fields: hypothesis, success_criteria, duration, budget

### Decision
Location: `templates/decision.md`
Purpose: Log a significant decision
Required fields: context, options[], decision, rationale, reversibility

### Weekly Review
Location: `templates/weekly-review.md`
Purpose: Capture weekly progress and learnings
Required fields: rock_progress, wins[], blockers[], next_week_priorities[]

## 7. Commands

### `/new-rock`
**Purpose**: Create a new quarterly rock
**Input**: Rock name, objective link, success metric
**Output**: Rock document from template in current quarter folder
**Example**: `/new-rock "Launch mobile app" links:OBJ-2025-Q1 metric:"10k downloads"`

### `/start-experiment`
**Purpose**: Kick off a new experiment
**Input**: Hypothesis, duration, success criteria
**Output**: Experiment doc, calendar blocks, tracking setup
**Example**: `/start-experiment "Higher price = higher conversion" 2w criteria:">5% lift"`

### `/daily-log`
**Purpose**: Generate or update today's progress log
**Input**: None (reads from task system)
**Output**: Daily log entry with completions and blockers
**Example**: `/daily-log`

### `/rock-status`
**Purpose**: Generate progress report for all active rocks
**Input**: None
**Output**: Summary with % complete, blockers, next milestones
**Example**: `/rock-status`

### `/weekly-update`
**Purpose**: Draft stakeholder update email
**Input**: None (reads from state)
**Output**: Formatted update ready for review and send
**Example**: `/weekly-update`

### `/decision`
**Purpose**: Log a decision with context
**Input**: Decision title, options considered, choice made
**Output**: Decision document for the record
**Example**: `/decision "API versioning approach" options:"URL,header,query" chose:"URL"`
```
