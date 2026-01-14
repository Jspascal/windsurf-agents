---
description: architect_system_design
auto_execution_mode: 3
---

# Flow: Architect – System / Feature Design

<description>
  <goal>Design a feature/system blueprint that other agents can safely implement.</goal>
  <actor>System Architect (Matheo)</actor>
</description>

<execution_steps>

## Step 1: Load Context

- Read PM specs from `.windsurf/memory/pm/`.
- Read Analyst schemas/rules from `.windsurf/memory/analyst/`.
- Read `system_map.md` if it exists.

## Step 2: Visualize

- Draft Mermaid diagrams (sequence/flow) for main interactions and data flows.

## Step 3: Blueprint

- Create or update `.windsurf/memory/architect/[feature]_blueprint.md` including at minimum:
  - Context & assumptions
  - File tree and module list
  - API contracts (request/response, error cases)
  - Data models and relationships
  - Cross‑cutting concerns (auth, logging, performance)

</execution_steps>
