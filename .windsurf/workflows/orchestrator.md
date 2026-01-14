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

## Step 1: Command Routing

- If `/init` -> Create `.windsurf/memory` structure.
- If `/feature` -> Execute `.windsurf/flows/orchestrator/feature_chain.md`.
- If `/status` -> Read all `active_*.md` files in memory and summarize.

## Step 2: State Update

Update `.windsurf/memory/_global_context.md` with the latest phase.
</execution_steps>
