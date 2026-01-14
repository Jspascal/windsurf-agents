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

## Step 1: Solution Design

- Based on PM Requirements and Analyst Constraints, design the system.
- **Visual:** Generate a textual File Tree or Mermaid Diagram.

## Step 2: Blueprinting

- Create a technical spec: `.windsurf/memory/architect/[feature_name]_spec.md`.
- Content: - **Stack Decisions:** Libs/Frameworks to use. - **File Tree:** Exact paths of files to be created. - **Signatures:** Exported functions/interfaces.
  </execution_steps>
