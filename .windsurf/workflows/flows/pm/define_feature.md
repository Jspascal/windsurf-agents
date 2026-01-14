---
description: pm_define_feature
auto_execution_mode: 3
---

# Flow: PM – Define New Feature

<description>
  <goal>Define a new feature specification ready for Analyst, Architect, and Developer.</goal>
  <actor>Product Manager (Donald)</actor>
</description>

<execution_steps>

## Step 1: Ingest Request

- Ask the user for the high-level goal and feature name.

## Step 2: Draft Spec File

- Create or update `.windsurf/memory/pm/[feature_name].md`.
- Populate sections:
  - **Vision** – why this matters.
  - **User Stories** – `As a..., I want..., So that...`.
  - **Acceptance Criteria** – Gherkin (`Given/When/Then`).

## Step 3: Review & Confirm

- Read back a concise summary of the spec.
- Ask the user to confirm or refine scope before considering the spec READY.

</execution_steps>
