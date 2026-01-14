---
description: analyst_generate_test_cases
auto_execution_mode: 3
---

# Flow: Analyst – Generate Test Cases

<description>
  <goal>Produce concrete test cases to validate the feature behavior.</goal>
  <actor>Business Analyst / QA (Sarah)</actor>
</description>

<execution_steps>

## Step 1: Load Inputs

- Read PM specs and any schemas from `.windsurf/memory/pm/` and `.windsurf/memory/analyst/`.

## Step 2: Enumerate Scenarios

- Cover happy paths, edge cases, and failure modes.

## Step 3: Save Test Cases

- Write test cases (e.g., Gherkin or structured list) to `.windsurf/memory/analyst/[feature]_tests.md`.

</execution_steps>
