---
description: orchestrator_onboard_project
auto_execution_mode: 3
---

# Flow: Orchestrator – Onboard Existing Project

<description>
  <goal>Discover the tech stack and initialize context for an existing project.</goal>
  <actor>Orchestrator (Alice)</actor>
</description>

<execution_steps>

## Step 1: Scan Stack

- Read root configuration files to detect languages, frameworks, and tooling.

## Step 2: Initialize Context

- Create or update `.windsurf/memory/_global_context.md` with detected stack details.

## Step 3: Delegate Mapping

- Suggest or trigger the Architect's "Map Existing System" flow (`/arch`).

## Step 4: Report

- Summarize the project structure and stack in the final output.

</execution_steps>
