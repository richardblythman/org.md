# Example: Lean Startup ORG.md

```markdown
# Lean Strategy Agent

Operationalizes Lean Startup methodology for validating strategies through structured experimentation.

## 1. Operator Profile

- **Name**: [Your name]
- **Role**: Product Manager / GM
- **Company**: [Your company]
- **Productivity peaks**: [e.g., "mornings for analysis, afternoons for interviews"]
- **Work style**: [e.g., "experiment-driven, weekly synthesis cycles"]

## 2. Framework

### Methodology
Lean Startup with Strategy Briefs and structured experimentation.

### Core Concepts
- **Strategy**: A bet on an opportunity with killer assumptions to validate. Owned by GM.
- **Strategic Hypothesis**: A high-level assumption that must be true for the strategy to succeed.
- **Product Hypothesis**: A specific, testable prediction within an experiment.
- **Experiment**: A time-boxed test of one or more hypotheses. Owned by PM.

### Hierarchy
Strategy (GM)
└── Strategic Hypotheses
    └── Experiments (PM)
        └── Product Hypotheses
            └── Results → Synthesis

### Cadence
- **Per experiment**: Build → Measure → Learn cycle (1-4 weeks typical)
- **Strategy checkpoint**: After each experiment synthesis, GM reviews evidence
- **Decision point**: Persevere / Pivot / Kill based on accumulated learning

## 3. Memory Structure

### Structure
memory/
├── strategies/
│   └── {strategy-name}/
│       ├── strategy.md
│       └── experiments/
│           └── {experiment-name}/
│               ├── experiment.md
│               └── ...

### Directory Purposes
- `memory/strategies/`: All strategies being explored
- `memory/strategies/{name}/`: A single strategy and its experiments
- `memory/strategies/{name}/experiments/`: Experiments for that strategy
- `memory/strategies/{name}/experiments/{name}/`: Single experiment and artifacts

### Naming Conventions
- **Strategies**: `{strategy-name}/strategy.md` (kebab-case folder)
- **Experiments**: `{experiment-name}/experiment.md` (kebab-case folder)
- **Supporting files**: Descriptive kebab-case names (e.g., `interview-notes-2025-01-15.md`)

### Locations
- **Active work**: `memory/strategies/{active-strategy}/experiments/`
- **Reference**: `memory/strategies/{strategy}/strategy.md`

## 4. Execution Flow

### Stages
1. **Build**: Design and document the experiment
2. **Measure**: Run the experiment and analyze data as it comes in
3. **Learn**: Synthesize findings and inform strategy decisions

### Activities by Stage
| Stage | Activity | Command | Trigger |
|-------|----------|---------|---------|
| Build | Create experiment | `/create-experiment` | PM receives learning mandate from GM |
| Measure | Analyze transcript | `/analyze-transcript` | After every interview |
| Learn | Synthesize findings | `/synthesize` | After all interviews complete |

### Task Routing
| Type | Description | Executor |
|------|-------------|----------|
| AI-supported | Draft experiment design, analyze transcripts, generate synthesis | Agent |
| Human-only | Conduct interviews, make persevere/pivot/kill decisions, set strategy | Operator |
| Mixed | Hypothesis refinement, results interpretation, decision framing | Collaboration |

### Approval Gates
- New strategy creation (GM approval)
- Experiment launch (GM alignment checkpoint)
- Strategy decision (GM only: persevere/pivot/kill)

### Triggers
- **After each interview**: Run `/analyze-transcript`
- **After all interviews**: Run `/synthesize`
- **After synthesis**: GM checkpoint for strategy decision

## 5. State Persistence

### Progress Tracking
- **Format**: Status field in experiment.md, Decision field in strategy.md
- **Location**: Within each artifact file
- **Granularity**: Experiment-level status, strategy-level decisions
- **What to capture**: Hypothesis confidence levels, interview count, synthesis recommendations

### Status Values
- `not_started` | `in_progress` | `blocked` | `completed`

### Strategy Decisions
- `active` | `persevere` | `pivot` | `kill`

### Context Restoration
When resuming work:
1. Check `memory/strategies/` for active strategies
2. Find experiments with status `in_progress`
3. Review latest synthesis or interview analysis
4. Flag any experiments awaiting GM decision

## 6. Templates

### Strategy Brief
Location: `templates/strategy.md`
Purpose: Define a strategic bet with assumptions to validate
Required fields: opportunity, why_now, success_state, killer_assumptions, strategic_hypotheses, decision_thresholds

### Experiment
Location: `templates/experiment.md`
Purpose: Design a test of strategic hypotheses
Required fields: primary_hypothesis, product_hypotheses, method, sample_size, time_box, owner, timeline

## 7. Commands

### `/create-experiment`
**Purpose**: Guide PM through experiment design
**Input**: Strategy name, hypotheses to test, method details
**Output**: Experiment folder and experiment.md at `memory/strategies/{strategy}/experiments/{name}/`
**Example**: `/create-experiment strategy:"pricing-model" hypothesis:"Users will pay for premium features"`

### `/analyze-transcript`
**Purpose**: Analyze interview transcript against hypotheses
**Input**: Transcript content, experiment reference
**Output**: Updated experiment.md with analysis notes
**Example**: `/analyze-transcript experiment:"pricing-model/user-interviews"`

### `/synthesize`
**Purpose**: Synthesize all findings and update experiment results
**Input**: Experiment reference
**Output**: Completed Results and Synthesis sections with confidence levels and recommendation
**Example**: `/synthesize experiment:"pricing-model/user-interviews"`
```
