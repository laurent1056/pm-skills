---
description: Turn a PRD, Opportunity Solution Tree, or story set into an engineering-ready build handoff — de-risked, vertically sliced, with testable acceptance criteria and tracker-ready issues
argument-hint: "<PRD, spec, or feature to hand off to engineering>"
---

# /handoff -- Spec to Buildable Plan

Convert an approved product artifact into a package a builder can execute with minimal
back-and-forth — a coding agent working autonomously, or a dev team in a sprint. This is the
bridge from "we know what to build" to "we're building it."

## Invocation

```
/handoff [upload or paste a PRD]
/handoff Break our SSO feature into a build plan for the team
/handoff [paste an Opportunity Solution Tree solution or a set of user stories]
/handoff                      # asks what you want to hand off
```

## Workflow

### Step 1: Ingest the Source

Accept the input in any form — a PRD, an Opportunity Solution Tree, a strategy doc, a set of
user or job stories, a Figma link, or a rough brief. Read any uploaded files first. Separate
what is **decided** (ready to build) from what is **open** (must be resolved before or during
build). If critical inputs are missing, ask — don't manufacture scope.

### Step 2: Learn the Target Environment

Stay platform-agnostic. Read the project's `CLAUDE.md` or `README` for the tech stack, test
command, and issue tracker if present. Otherwise ask:

1. **Tracker:** GitHub Issues, Jira, Linear, or a plain checklist?
2. **Stack / constraints:** anything that shapes the work (existing services, compliance, deadlines)?
3. **Builder:** handing this to a coding agent, or to a human team? (Affects how much context to inline.)
4. **Scope:** the whole feature, or just the first shippable slice?

### Step 3: Generate the Handoff

Apply the **build-handoff** skill to produce the package:

- **Engineering brief** — problem, user, measurable success, constraints, non-goals.
- **Open questions & risks** — the unknowns that could change the shape of the work, each
  with an owner and a note on whether it needs a spike, listed *before* decomposition.
- **Build plan in vertical slices** — epics → stories → tasks, walking skeleton first, then
  thickened, with dependencies mapped. No horizontal "all backend then all frontend" layering.
- **Testable acceptance criteria** — Given / When / Then per story; INVEST-clean; a Definition
  of Ready gate that flags anything not safe to start.
- **Sequencing** — critical path, what runs in parallel, phased milestones (relative, not dated).
- **Tracker-ready issues** — an epic plus child issues with titles, bodies, acceptance,
  sizes, dependencies, and labels, copy-pasteable into the chosen tracker.

### Step 4: Review and Route

After generating, offer natural next steps:

- "Want me to expand the acceptance criteria into full **test scenarios**?"
- "Should I run a **pre-mortem** on this plan before you hand it off?"
- "Want me to **tighten Phase 1** so only the thinnest shippable slice is fully specified?"
- "If your PRD's success metrics are vague, I can strengthen those first."

Save the handoff as a markdown file (e.g. `HANDOFF-[feature-name].md`) to the user's workspace.

## Notes

- Hand off Phase 1 in full detail; keep later phases as titles. A builder should never open
  twenty fully-specified stories at once.
- Every unresolved product decision belongs in Open Questions with an owner — never buried in
  a story for engineering to guess.
- Sizes are relative effort and risk signals, not a schedule. Avoid calendar dates and fake hours.
- The handoff inherits the spec's quality: if success criteria or non-goals are missing, fix
  the spec first — a clean handoff can't rescue a vague PRD.
- Write it so a competent builder could start the first slice without asking a question.
