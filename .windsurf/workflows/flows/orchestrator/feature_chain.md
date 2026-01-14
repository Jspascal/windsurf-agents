---
description: orchestrator_feature_chain
auto_execution_mode: 3
---

# Flow: Orchestrator – Feature Chain (The Waterfall)

<description>
  <goal>Run the end‑to‑end feature delivery chain across PM, Scrum, Analyst, Architect, Developer, and Commander.</goal>
  <actor>Orchestrator (Alice)</actor>
</description>

<execution_steps>

## Step 1: PM Phase

- Execute `.windsurf/workflows/flows/pm/define_feature.md` to define the feature spec.

## Step 2: Scrum Phase (Optional)

- Optionally invoke the `/scrum` workflow (Emma) to:
  - Check capacity and WIP
  - Surface blockers and risks
  - Update or create `sprint_plan.md`

## Step 3: Analyst Phase

- Execute `.windsurf/workflows/flows/analyst/define_schema.md` to:
  - Validate the PM spec
  - Derive the data schema and surface risks

## Step 4: Architect Phase

- Execute `.windsurf/workflows/flows/architect/system_design.md` to:
  - Blueprint the validated schema and flows
  - Produce `[feature]_blueprint.md`

## Step 5: Developer Phase

- Execute `.windsurf/workflows/flows/developer/implement_code.md` to:
  - Implement code strictly according to the blueprint and specs

## Step 6: Commander Phase

- When git/CI/package or environment work is required, delegate to Commander (`/cmd` or `/ops`) to perform safe operations.

</execution_steps>
