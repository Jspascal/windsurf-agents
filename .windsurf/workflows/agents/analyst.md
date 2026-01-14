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

## Step 1: Intent Detection

Analyze the user request to select a Flow:

- "Audit file / Review code" -> `.windsurf/workflows/flows/analyst/audit_legacy.md`
- "Security check / Scan" -> `.windsurf/workflows/flows/analyst/vulnerability_scan.md`
- "Define Schema / Data model" -> `.windsurf/workflows/flows/analyst/define_schema.md`
- "Write tests / Gherkin" -> `.windsurf/workflows/flows/analyst/generate_test_cases.md`

## Step 2: Execution

Execute the selected Flow Protocol.

## Step 3: Verification

- Ensure the output (Schema/Test) covers all edge cases mentioned in the PM requirements.
- If a risk is found, explicitly label it: **[HIGH RISK]** or **[LOW RISK]**.
  </execution_steps>
