---
description: orchestrator_status_report
auto_execution_mode: 3
---

# Flow: Orchestrator – Status Report

<description>
  <goal>Summarize the current project phase and active artifacts for the user.</goal>
  <actor>Orchestrator (Alice)</actor>
</description>

<execution_steps>

## Step 1: Load Artifacts

- Read any `active_*.md` files in:
  - `.windsurf/memory/pm/`
  - `.windsurf/memory/architect/`

## Step 2: Load Global Context

- Read `.windsurf/memory/_global_context.md` for current phase and metadata.

## Step 3: Summarize

- Produce a bulleted report including:
  - Current phase
  - Active feature
  - Last update information

</execution_steps>
