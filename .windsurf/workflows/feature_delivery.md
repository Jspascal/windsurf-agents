---
description: feature_delivery_overview
---

# Feature Delivery & Status Workflow

This document explains how the Windsurf agents, workflows, and flows chain together to deliver a feature from idea to deployed code, and how to check status at each step.

## 1. Key Directories & Concepts

- `.windsurf/agents/`

  - Agent personas (PM, Analyst, Architect, Developer, Scrum, Orchestrator, Commander, Brainstorm).

- `.windsurf/workflows/agents/`

  - Per-agent workflows (what each agent does when invoked via its slash command).

- `.windsurf/workflows/flows/`

  - Reusable, step-based flow workflows used by agents.
  - Each flow file uses `## Step 1 / Step 2 / ...` under `<execution_steps>`.

- `.windsurf/memory/`
  - Long-lived state and artifacts:
    - `pm/` – feature specs, gap analyses.
    - `analyst/` – schemas, test cases, audits, security reports.
    - `architect/` – system maps, blueprints, dependency audits, diagrams.
    - `scrum/` – sprint plans, flow reports, retros.
    - `_global_context.md` – project metadata and current phase.

## 2. End-to-End Feature Chain (Happy Path)

The canonical feature delivery chain is coordinated by the Orchestrator via:

- Flow: `.windsurf/workflows/flows/orchestrator/feature_chain.md`

It runs these phases in order:

1. **PM Phase (Donald /pm)**

   - Flow: `.windsurf/workflows/flows/pm/define_feature.md`
   - Output: feature spec in `.windsurf/memory/pm/[feature_name].md`.

2. **Scrum Phase (Emma /scrum, optional)**

   - Flow: `.windsurf/workflows/flows/scrum/sprint_planning.md` (plus others as needed).
   - Output: `.windsurf/memory/scrum/sprint_plan.md`, blockers, and flow insights.

3. **Analyst Phase (Sarah /analyst)**

   - Flow: `.windsurf/workflows/flows/analyst/define_schema.md` (and optionally `audit_legacy`, `generate_test_cases`, `vulnerability_scan`).
   - Output: `.windsurf/memory/analyst/[feature]_schema.md` and related artifacts.

4. **Architect Phase (Matheo /arch)**

   - Flow: `.windsurf/workflows/flows/architect/system_design.md` (plus `map_existing`, `visualize_flow`, `dependency_check` when useful).
   - Output: `.windsurf/memory/architect/system_map.md`, `[feature]_blueprint.md`, diagrams, dependency audits.

5. **Developer Phase (Leo /dev)**

   - Flow: `.windsurf/workflows/flows/developer/implement_code.md` (plus `update_legacy`, `debug_mode`).
   - Output: Code changes in the repo, aligned to the blueprint and specs.

6. **Commander Phase (Victor /cmd or /ops)**
   - Not a flow file; invoked as needed for git/CI/env operations.
   - Enforces protected branches and branch naming conventions.

Nora (`/idea`) and Emma (`/scrum`) can be called before or during this chain for ideation and planning.

## 3. Checking Status at Any Time

Because each phase writes artifacts to disk, status is always recoverable from files.

### 3.1 Global Project Status

Use the Orchestrator status report:

- Agent workflow: `.windsurf/workflows/agents/orchestrator.md`
- Flow: `.windsurf/workflows/flows/orchestrator/status_report.md`

This reads:

- `.windsurf/memory/_global_context.md` for current phase and metadata.
- Active artifacts in `pm/` and `architect/` (and can be extended to scrum/analyst if desired).

It then outputs a high-level summary:

- Current phase
- Active feature
- Recent updates

### 3.2 Phase-Specific Status

You can also inspect status for a specific phase:

- **PM (/pm)** – Check specs and gap analyses under `.windsurf/memory/pm/`.
- **Scrum (/scrum)** – Check `.windsurf/memory/scrum/sprint_plan.md`, `flow_report.md`, `retro.md`.
- **Analyst (/analyst)** – Check schemas/tests/audits under `.windsurf/memory/analyst/`.
- **Architect (/arch)** – Check `system_map.md`, `[feature]_blueprint.md`, and diagrams under `.windsurf/memory/architect/`.
- **Developer (/dev)** – Source of truth is the repo plus upstream artifacts; use `debug_mode` to address concrete errors.
- **Commander (/cmd, /ops)** – Check git history, branches, CI logs, and any notes you choose to store.

Because flows are idempotent with respect to their artifacts, you can:

- Re-run a phase to update its output.
- Interrupt the chain and resume later.
- Always reconstruct status from the combination of `_global_context.md` + memory files.

## 4. How to Use This in Practice

Typical usage pattern:

1. Call `/idea` (Nora) if your request is fuzzy.
2. Call `/pm` to define or refine a feature.
3. Optionally call `/scrum` to plan and assess capacity.
4. Call `/feature` (via `/orch`) to run the orchestrated feature chain.
5. At any point, call `/orch` and choose **Status Report** to see where you are.
6. When blocked at a specific phase, jump directly to that agent (`/analyst`, `/arch`, `/dev`, `/scrum`, `/cmd`) for focused work.

This structure ensures you can always answer:

- _What is the current phase?_
- _What artifacts exist for this feature?_
- _What’s the next safe step in the chain?_
