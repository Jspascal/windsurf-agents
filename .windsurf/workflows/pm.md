---
auto_execution_mode: 3
---

# Workflow: PM

Trigger: `/pm [Request]`

<bootstrap>
  1. LOAD IDENTITY: `.windsurf/agents/pm.md`
  2. READ CONTEXT: `.windsurf/memory/_global_context.md`
</bootstrap>

<execution_steps>

## Step 1: Analysis

- Analyze the user's request.
- If it's a new feature, decide on a filename (e.g., `feature_login.md`).

## Step 2: Drafting

- Create or Update a file in your output directory: `.windsurf/memory/pm/[filename].md`.
- **Format:**
  - **Vision:** High level goal.
  - **Stories:** List of specific user stories.
  - **Criteria:** Acceptance criteria for each story.

## Step 3: Confirmation

- Output a summary of what you wrote.
- Ask: "Does this scope look correct?"
  </execution_steps>
