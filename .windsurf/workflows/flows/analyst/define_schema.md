---
description: analyst_define_schema
auto_execution_mode: 3
---

# Flow: Analyst – Define Data Schema

<description>
  <goal>Derive a precise data schema from PM specs for downstream design and implementation.</goal>
  <actor>Business Analyst / QA (Sarah)</actor>
</description>

<execution_steps>

## Step 1: Load Feature Spec

- Read the active feature spec from `.windsurf/memory/pm/`.

## Step 2: Model Data

- Identify entities, fields, and relationships.
- Choose appropriate types and constraints.

## Step 3: Write Schema

- Save the schema to `.windsurf/memory/analyst/[feature]_schema.md` (JSON/SQL/markdown).

</execution_steps>
