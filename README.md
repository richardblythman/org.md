# ORG.md

**A simple, open format for organizational operating systems.**

Like [AGENTS.md](https://agents.md) tells coding agents how to work on your codebase, ORG.md tells operational agents how to work within your organization.

## The Problem

Every AI conversation about your work starts from scratch. The agent doesn't know:
- Your methodology (EOS? OKRs? Custom?)
- Your vocabulary ("rock" means 90-day priority, not geology)
- Where things live (file structure, naming conventions)
- When you work (deep work hours, meeting days)
- What format you expect (your templates, not generic output)

## The Solution

One file. Seven sections. Machine-readable context for organizational AI.

```
ORG.md
├── Operator      # Who's running this OS
├── Framework     # Your methodology and vocabulary
├── File System   # Where artifacts live
├── Scheduler     # Time blocks and task routing
├── State         # Progress tracking and persistence
├── Templates     # Artifact structures
└── Commands      # Defined operations
```

## Quick Start

### Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/richardblythman/org.md.git
   cd org.md
   ```

2. Run Claude Code in the directory:
   ```bash
   claude
   ```

3. Initialize your organizational OS:
   ```
   /init_org_os
   ```

This will create an `ORG.md` file at your workspace root configured for your organization.

### Learn More

- Read the [full specification](SPEC.md)
- See a [complete example](examples/eos-product.md)

## Why This Matters

| Without ORG.md | With ORG.md |
|----------------|-------------|
| "Create a quarterly goal doc" | `/new-rock "Launch mobile app"` |
| Generic template output | Your format, your fields |
| "Where should I save this?" | Predictable file locations |
| Context lost between sessions | State persistence and restoration |
| Same explanations every time | Methodology encoded once |

## Specification

See [SPEC.md](SPEC.md) for the complete specification.

## Examples

- [EOS Product Team](examples/eos-product.md) - Full example for a product team using modified EOS
- [Lean Startup](examples/lean-startup.md) - Strategy validation through structured experimentation

## Contributing

ORG.md is an open specification. Contributions, feedback, and real-world examples welcome.

## License

CC BY 4.0
