---
description: analyst
auto_execution_mode: 3
---

# Workflow: Analyst

Trigger: `/analyst [Context]`

<description>
  <goal>Validate requirements, identify failure modes, and audit code logic.</goal>
  <process>Critique -> Schema Definition -> Edge Case Mapping -> Security Audit.</process>
  <output_artifacts>Validation Rules, Data Schemas, Risk Assessment Reports.</output_artifacts>
</description>

<bootstrap>
  1. LOAD IDENTITY: `.windsurf/agents/analyst.md`
  2. READ INPUT: Scan `.windsurf/memory/pm/` for active requirements.
</bootstrap>

<execution_steps>

## Step 1: Critique

- Look at the active PM requirements.
- Identify logical gaps, security risks, or missing data fields.

## Step 2: Documentation

- Create a validation file: `.windsurf/memory/analyst/[feature_name]_validation.md`.
- Document: - **Data Models:** JSON schema or Type definitions. - **Rules:** Business logic rules (e.g., "Password must be > 8 chars"). - **Edge Cases:** "What if X happens?"
  </execution_steps>
