---
description: developer_implement_code
auto_execution_mode: 3
---

# Flow: Developer – Implement Code

<description>
  <goal>Implement feature code strictly according to blueprints and specs.</goal>
  <actor>Developer (Leo)</actor>
</description>

<execution_steps>

## Step 1: Load Inputs

- Read the latest blueprint from `.windsurf/memory/architect/`.
- Read relevant PM and Analyst artifacts from `.windsurf/memory/pm/` and `.windsurf/memory/analyst/`.

## Step 2: Plan Files

- For each file in the blueprint:
  - If it exists, open and understand existing structure.
  - If it does not exist, plan to create it exactly as specified.

## Step 3: Implement

- Write or update code to match the blueprint and rules, respecting:
  - Directory structure
  - Function signatures and contracts
  - Validation and error handling rules

## Step 4: Self‑Review

- Mentally check compilation and alignment with Analyst test cases.

</execution_steps>
