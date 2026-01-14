---
description: pm
auto_execution_mode: 3
---

# Workflow: PM

Trigger: `/pm [Request]`

<description>
  <goal>Convert vague user intent into structured, actionable product requirements.</goal>
  <process>Ingest Request -> Gap Analysis -> User Story Definition -> Acceptance Criteria.</process>
  <output_artifacts>PRD (Product Requirement Doc), User Stories, Sprint Backlog.</output_artifacts>
</description>

<bootstrap>
  1. LOAD IDENTITY: `.windsurf/agents/pm.md`
  2. READ CONTEXT: `.windsurf/memory/_global_context.md`
</bootstrap>

<execution_steps>

## Step 1: Intent Detection

Analyze user request to select a Flow:

- "New Feature" -> `.windsurf/workflows/flows/pm/define_feature.md`
- "Missing stuff" -> `.windsurf/workflows/flows/pm/gap_analysis.md`
- "Plan sprint" -> `.windsurf/workflows/flows/pm/plan_sprint.md`

## Step 2: Execution

Execute the selected Flow Protocol.

## Step 3: Handoff

If a feature was defined, ask: "Shall I send this to the Analyst?"
</execution_steps>
