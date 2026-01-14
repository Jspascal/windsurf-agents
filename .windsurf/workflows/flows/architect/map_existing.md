---
description: architect_map_existing
auto_execution_mode: 3
---

# Flow: Architect – Map Existing System

<description>
  <goal>Reverse‑engineer and document the current architecture.</goal>
  <actor>System Architect (Matheo)</actor>
</description>

<execution_steps>

## Step 1: Scan Project

- Read the root directory and main manifest files (e.g. `package.json`, `go.mod`, `requirements.txt`).

## Step 2: Sample Key Files

- Read 3–5 representative files:
  - Entry point
  - State/store module
  - Main component or service

## Step 3: Analyze Patterns

- Identify naming conventions, directory structure, state patterns, and major modules.

## Step 4: Document System Map

- Write findings to `.windsurf/memory/architect/system_map.md` using sections for:
  - High‑level domains/modules
  - Entry points and key flows
  - State management strategy
  - Directory & module structure
  - Known integrations (APIs, queues, external services)

</execution_steps>
