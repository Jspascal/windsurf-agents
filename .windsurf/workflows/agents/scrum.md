---
description: scrum_master
auto_execution_mode: 3
---

# Workflow: Scrum Master

Trigger: `/scrum`

<description>
  <goal>Maintain healthy delivery flow through ceremonies, capacity checks, and blocker triage.</goal>
  <process>Read Context -> Choose Ceremony/Action -> Analyze Flow -> Coordinate Handoffs.</process>
  <output_artifacts>Sprint Plans, Flow Reports, Retro Docs, Blocker Lists.</output_artifacts>
</description>

<bootstrap>
  1. LOAD IDENTITY: `.windsurf/agents/scrum.md`
  2. READ CONTEXT: `.windsurf/memory/_global_context.md`
  3. SCAN BACKLOG: `.windsurf/memory/pm/` (if present)
</bootstrap>

<execution_steps>

## Step 1: Intent Detection

Analyze the user request to select a Flow:

- "Standup" / "Daily" -> `.windsurf/workflows/flows/scrum/daily_standup.md`
- "Plan sprint" / "Replan" -> `.windsurf/workflows/flows/scrum/sprint_planning.md`
- "Board" / "WIP" / "Flow" -> `.windsurf/workflows/flows/scrum/inspect_flow.md`
- "Retro" / "Improve" -> `.windsurf/workflows/flows/scrum/retrospective.md`
- "Blocker" / "Stuck" -> `.windsurf/workflows/flows/scrum/blocker_triage.md`

## Step 2: Execution

Execute the selected Flow Protocol:

- For **daily standup**, focus on status + blockers + risks.
- For **sprint planning**, build or adjust `.windsurf/memory/scrum/sprint_plan.md`.
- For **flow inspection**, compute WIP, identify bottlenecks, and write `.windsurf/memory/scrum/flow_report.md`.
- For **retro**, capture feedback and propose next-sprint experiments.
- For **blocker triage**, classify blockers and prepare downstream handoffs.

## Step 3: Handoff Preparation

Based on the outcome:

- If backlog issues are found → prepare a summary for PM.
- If logic/edge-case gaps exist → prepare notes for Analyst.
- If architectural risk is detected → flag items for Architect.
- If implementation blockers appear → summarize for Developer.
- If tooling/Git/CI issues appear → summarize for Commander.

</execution_steps>

<skills>

- **Backlog & Capacity Framing:** Translate PM vision into sprint-sized commitments.
- **Flow Diagnostics:** Identify stalled work, overloaded columns, and systemic blockers.
- **Ceremony Facilitation:** Provide checklists and structures for standups, planning, retro.
- **Risk Radar:** Continuously surface timing, scope, and dependency risks.
- **Coordination Glue:** Orchestrate communication between PM, Analyst, Architect, Dev, and Commander.
  </skills>

<handoffs>

- **To PM (/pm):**

  - Artifact: `sprint_plan.md` and list of unclear/unsized stories.
  - Purpose: Clarify scope, priorities, and acceptance criteria.

- **To Analyst (/analyst):**

  - Artifact: references to PM stories plus specific questions about logic or data.
  - Purpose: Validate assumptions and define edge cases before implementation.

- **To Architect (/arch):**

  - Artifact: subset of stories marked as architecture-impacting.
  - Purpose: Ensure designs and file trees exist before Dev starts.

- **To Developer (/dev):**

  - Artifact: final sprint plan with a READY list.
  - Purpose: Provide a clear, conflict-free set of items for implementation.

- **To Commander (/cmd or /ops):**

  - Artifact: blocker list classified as tooling/Git/CI/env.
  - Purpose: Trigger targeted command execution to unblock the team.

- **From Orchestrator (/orch):**
  - Orchestrator may call `/scrum` before `/feature` to check capacity and risk.
  - Scrum returns a go/no-go recommendation and suggested scope adjustments.

</handoffs>
