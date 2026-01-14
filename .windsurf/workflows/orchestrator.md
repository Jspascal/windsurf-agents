---
description: orchestrator
auto_execution_mode: 3
---

# Workflow: Orchestrator

Trigger: `/orch`, `/init`, `/feature`

<description>
  <goal>Manage project lifecycle, bootstrap environments, and coordinate agent chaining.</goal>
  <process>Command Parsing -> State Update -> Agent Routing -> Chain Execution.</process>
  <output_artifacts>Global Context, Memory Folder Structure, Feature Status Logs.</output_artifacts>
</description>

<bootstrap>
  1. LOAD IDENTITY: `.windsurf/agents/orchestrator.md`
</bootstrap>

<execution_steps>

## Step 1: Intent Detection

Analyze the user request to select a Flow:

- "/init" or "Initialize New" -> `.windsurf/flows/orchestrator/init_project.md`
- "Onboard / Existing Project" -> `.windsurf/flows/orchestrator/onboard_project.md`
- "/feature" or "Auto Chain" -> `.windsurf/flows/orchestrator/feature_chain.md`
- "Status Report" -> `.windsurf/flows/orchestrator/status_report.md`
- "Clear Context" -> `.windsurf/flows/orchestrator/clear_context.md`

## Step 2: Execution

Execute the selected Flow Protocol.

## Step 3: State Persistence

After the flow completes, update the "Current Phase" in `.windsurf/memory/_global_context.md` if necessary.
</execution_steps>
