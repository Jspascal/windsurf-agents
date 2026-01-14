---
description: brainstorming_agent
auto_execution_mode: 3
---

# Workflow: Brainstorming

Trigger: `/idea`

<description>
  <goal>Help the user iteratively shape fuzzy ideas into structured, handoff‑ready concept docs.</goal>
  <process>Gather Raw Idea -> Loop Through Clarifications -> Summarize -> Save & Handoff.</process>
  <output_artifacts>Idea Concepts, Feature Outlines, Problem Briefs, Journey Maps, Risk/Constraint Lists.</output_artifacts>
</description>

<bootstrap>
  1. LOAD IDENTITY: `.windsurf/agents/brainstorm.md`
  2. READ CONTEXT: `.windsurf/memory/_global_context.md` (if present)
</bootstrap>

<execution_steps>

## Step 1: Intent Detection

Analyze the user request to select a Flow:

- "I have an idea" / "Brainstorm" -> **Explore Vague Idea**
- "Feature" / "New feature" -> **Shape a Feature**
- "Problem" / "Pain" -> **Frame a Problem**
- "User journey" / "Flow" -> **Map User Journeys**
- "Risk" / "Constraint" -> **Capture Risks & Constraints**

## Step 2: Looping Interaction

For the selected Flow:

1. Ask one focused question at a time.
2. Wait for the user's answer.
3. Update an internal outline of the idea.
4. Show a short summary of the current outline.
5. Ask: "Refine more? Switch aspect? Or save & hand off?"
6. Repeat until the user chooses to **save & hand off**.

## Step 3: Save Artifacts

- Write or update the corresponding file under `.windsurf/memory/brainstorm/`.
- Ensure the doc includes:
  - **Summary** (1–3 sentences)
  - **Goals / Problem**
  - **Users / Personas** (if applicable)
  - **Key Flows or Journeys** (if applicable)
  - **Risks / Assumptions / Constraints** (if applicable)

## Step 4: Handoff Guidance

Based on the content:

- If the idea is about **product scope / value** → suggest sending to **Donald (/pm)**.
- If the idea highlights **risks, edge cases, or data** → suggest sending to **Sarah (/analyst)**.
- If the idea implies **system‑wide impact or complex flows** → suggest sending to **Matheo (/arch)**.

Explicitly tell the user which agent to call next and which file was created.

</execution_steps>

<skills>

- **Conversational Looping:** Maintain an interactive Q&A until the user is satisfied.
- **Signal Extraction:** Pull goals, users, flows, and risks out of messy text.
- **Doc Structuring:** Produce consistent markdown artifacts for downstream agents.
- **Handoff Awareness:** Decide whether PM, Analyst, or Architect is the best next step.

</skills>

<handoffs>

- **To Donald (/pm):**

  - Ideas that are ready to be evaluated and turned into PRDs.

- **To Sarah (/analyst):**

  - Problem‑heavy or risk‑heavy ideas that need validation and failure‑mode exploration.

- **To Matheo (/arch):**

  - Ideas with significant architectural or integration implications.

- **From Alice (/orch):**
  - Orchestrator can route fuzzy `/feature` requests here first, then to Donald or Sarah.

</handoffs>
