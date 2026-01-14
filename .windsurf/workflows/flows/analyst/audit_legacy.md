---
description: analyst_audit_legacy
auto_execution_mode: 3
---

# Flow: Analyst – Audit Legacy Code

<description>
  <goal>Review existing code for correctness, risks, and edge cases.</goal>
  <actor>Business Analyst / QA (Sarah)</actor>
</description>

<execution_steps>

## Step 1: Select Target

- Ask the user which file or module to audit.

## Step 2: Analyze Logic

- Read the target file.
- Identify assumptions, missing validations, and hidden coupling.

## Step 3: Record Findings

- Write an audit report to `.windsurf/memory/analyst/[target]_audit.md` with:
  - Risks, edge cases, and suggested checks.

</execution_steps>
