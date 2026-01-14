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

- "/init" or "Initialize New" -> `.windsurf/workflows/flows/orchestrator/init_project.md`
- "Onboard / Existing Project" -> `.windsurf/workflows/flows/orchestrator/onboard_project.md`
- "/feature" or "Auto Chain" -> `.windsurf/workflows/flows/orchestrator/feature_chain.md`
- "Status Report" -> `.windsurf/workflows/flows/orchestrator/status_report.md`
- "Clear Context" -> `.windsurf/workflows/flows/orchestrator/clear_context.md`

- If the user mentions "idea", "brainstorm", "not sure what I want", or gives very fuzzy input:
  - Suggest calling the Brainstorming agent: `/idea` (Nora) to shape the idea first.
  - After Nora saves an artifact under `.windsurf/memory/brainstorm/`, re-run `/orch` or `/feature` to continue.

If none of the above clearly match:

- Ask a short clarifying question in Alice's voice, for example: "Are you trying to (1) start a project, (2) work on a feature, (3) brainstorm an idea, (4) see status, or (5) something else?"
- Present the main menu options again and let the user choose explicitly instead of guessing.

## Step 2: Execution

Execute the selected Flow Protocol.

## Step 3: State Persistence

After the flow completes, update the "Current Phase" in `.windsurf/memory/_global_context.md` if necessary.
</execution_steps>
