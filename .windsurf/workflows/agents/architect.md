---
description: architect
auto_execution_mode: 3
---

# Workflow: Architect

Trigger: `/arch [Context]`

<description>
  <goal>Translate business requirements into technical blueprints and file structures.</goal>
  <process>Stack Check -> Pattern Matching -> File Tree Generation -> API Design.</process>
  <output_artifacts>System Blueprints, File Trees, Mermaid Diagrams, Tech Stack Configs.</output_artifacts>
</description>

<bootstrap>
  1. LOAD IDENTITY: `.windsurf/agents/architect.md`
  2. READ INPUT: `.windsurf/memory/pm/` and `.windsurf/memory/analyst/`.
</bootstrap>

<execution_steps>

<execution_steps>

## Step 1: Intent Detection

Analyze the user request to select a Flow:

- "Map system / Explain code" -> `.windsurf/workflows/flows/architect/map_existing.md`
- "Design feature / Blueprint" -> `.windsurf/workflows/flows/architect/system_design.md`
- "Visualize flow / Diagram" -> `.windsurf/workflows/flows/architect/visualize_flow.md`
- "Check deps / Stack audit" -> `.windsurf/workflows/flows/architect/dependency_check.md`

## Step 2: Execution

Execute the selected Flow Protocol:

- **Map system / Explain code** → populate or update `.windsurf/memory/architect/system_map.md` with:

  - High-level module overview, entry points, and key flows.
  - Notes on state management and directory structure.

- **Design feature / Blueprint** → create `.windsurf/memory/architect/[feature]_blueprint.md` containing:

  - Context/assumptions, file tree, modules, APIs, and data models.

- **Visualize flow / Diagram** → produce one or more Mermaid diagrams describing the main sequence/flow and reference them from the blueprint or a separate diagram file.

- **Check deps / Stack audit** → write a short dependency report (libraries, versions, risks) under `.windsurf/memory/architect/dependency_report.md`.

## Step 3: Standardization

- Verify that all file paths in the output match the project's existing directory structure.
- Ensure no deprecated libraries are suggested.
- **Critical:** If generating code or trees, always use the Project's established naming conventions (camelCase vs snake_case).
  </execution_steps>
