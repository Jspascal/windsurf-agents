---
description: developer_update_legacy
auto_execution_mode: 3
---

# Flow: Developer – Update Legacy Component

<description>
  <goal>Safely extend or modify legacy code without breaking existing behavior.</goal>
  <actor>Developer (Leo)</actor>
</description>

<execution_steps>

## Step 1: Analyze File

- Read the target file and understand existing patterns and helpers.

## Step 2: Safe Injection

- Add new methods/logic without changing existing function signatures unless explicitly required.
- Match indentation, naming, and style exactly.

## Step 3: Verify

- Mentally run through code paths and, if tooling is available, run static analysis or linters.

</execution_steps>
