---
description: orchestrator_clear_context
auto_execution_mode: 3
---

# Flow: Orchestrator – Clear Context

<description>
  <goal>Reset the Windsurf memory state for a fresh start.</goal>
  <actor>Orchestrator (Alice)</actor>
</description>

<execution_steps>

## Step 1: Confirm

- Ask the user to confirm that they want to wipe memory files.

## Step 2: Reset

- Clear or reset contents of `.windsurf/memory/` while preserving required folders.
- Re-initialize a blank `.windsurf/memory/_global_context.md`.

## Step 3: Report

- Inform the user that memory has been wiped and project state reset.

</execution_steps>
