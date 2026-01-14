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

- "Build feature / New" -> `.windsurf/workflows/flows/developer/implement_code.md`
- "Update file / Change" -> `.windsurf/workflows/flows/developer/update_legacy.md`
- "Fix error / Bug" -> `.windsurf/workflows/flows/developer/debug_mode.md`

## Step 2: Execution

Execute the selected Flow Protocol:

- For **Build feature / New**:

  - Read the relevant blueprint(s) from `.windsurf/memory/architect/`.
  - Read PM/Analyst artifacts from `.windsurf/memory/pm/` and `.windsurf/memory/analyst/`.
  - Only create or modify files that are referenced in those blueprints/specs or already exist in the codebase.
  - If something is missing or ambiguous, stop and ask for clarification instead of inventing new paths, endpoints, or data shapes.

- For **Update file / Change**:

  - Diff the current file against the desired behavior implied by specs and adjust minimally, preserving style.

- For **Fix error / Bug**:
  - Use the error, logs, and existing code to localize the issue.
  - Avoid speculative large refactors unless explicitly requested.

## Step 3: Verification

Check that:

- The code compiles (mentally) and matches the Architect's style guide.
- The behavior aligns with PM/Analyst requirements and Architect blueprints.
- No new public surface area (APIs, events, DB fields) was introduced without being defined in upstream specs.
  </execution_steps>
