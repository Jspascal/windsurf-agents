---
description: architect_dependency_check
auto_execution_mode: 3
---

# Flow: Architect – Dependency Check

<description>
  <goal>Review project dependencies and highlight risks and cleanup opportunities.</goal>
  <actor>System Architect (Matheo)</actor>
</description>

<execution_steps>

## Step 1: Scan Dependency Files

- Read `package.json`, `go.mod`, `requirements.txt`, or equivalents.

## Step 2: Analyze Dependencies

- Look for:
  - Deprecated libraries
  - Version conflicts
  - Redundant packages with overlapping purpose

## Step 3: Advise

- Write recommendations to `.windsurf/memory/architect/dependency_audit.md`.

</execution_steps>
