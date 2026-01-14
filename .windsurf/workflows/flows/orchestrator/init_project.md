---
description: orchestrator_init_project
auto_execution_mode: 3
---

# Flow: Orchestrator – Initialize New Project

<description>
  <goal>Bootstrap a new Windsurf project with the standard memory structure.</goal>
  <actor>Orchestrator (Alice)</actor>
</description>

<execution_steps>

## Step 1: Create Memory Structure

- Ensure the following directories exist:
  - `.windsurf/memory/pm/`
  - `.windsurf/memory/analyst/`
  - `.windsurf/memory/architect/`

## Step 2: Initialize Global Context

- Create or update `.windsurf/memory/_global_context.md` with:
  - Project name
  - Vision
  - Phase = Planning

## Step 3: Report

- Tell the user the system is initialized and ready for the PM phase.

</execution_steps>
