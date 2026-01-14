---
description: developer
auto_execution_mode: 3
---

# Workflow: Developer

Trigger: `/dev`

<description>
  <goal>Write, refactor, or debug code based on strict technical specifications.</goal>
  <process>Fetch Blueprint -> Implement Logic -> Verify Rules -> Commit.</process>
  <output_artifacts>Source Code Files, Unit Tests, Refactored Components.</output_artifacts>
</description>

<bootstrap>
  1. LOAD IDENTITY: `.windsurf/agents/developer.md`
  2. READ BLUEPRINTS: `.windsurf/memory/architect/`
  3. READ RULES: `.windsurf/memory/analyst/`
</bootstrap>

<execution_steps>

## Step 1: Intent Detection

Analyze request to select a Flow:

- "Build feature / New" -> `.windsurf/flows/developer/implement_code.md`
- "Update file / Change" -> `.windsurf/flows/developer/update_legacy.md`
- "Fix error / Bug" -> `.windsurf/flows/developer/debug_mode.md`

## Step 2: Execution

Execute the selected Flow Protocol.

## Step 3: Verification

Check if the code compiles (mentally) and matches the Architect's style guide.
</execution_steps>
