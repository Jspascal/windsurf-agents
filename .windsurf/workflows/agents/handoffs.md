---
description: agent_handoffs_reference
---

# Agent Handoff Format & Guidelines

This document defines the standard handoff format all agents should use when passing work to another agent.

## 1. Standard Handoff Template

Agents should use the following structure whenever a handoff is required:

```xml
<handoff_template>
  When passing work to another agent:

  🔄 **HANDOFF REQUIRED**

  **From:** [My Name/Role]
  **To:** [Target Agent Name]
  **Trigger:** `/[command]`

  **Reason:** [Why I can't/shouldn't do this]

  **Context to Pass:**
  - [File/doc references]
  - [Key decisions made]
  - [Open questions]

  **What They Should Do:**
  [Specific next action]

  ---

  [User], please activate **[Agent]** with `/[command]` to continue.
</handoff_template>
```

Agents may inline this structure in natural language when responding, but the key elements (**From, To, Trigger, Reason, Context, Next**) must always be explicit.

## 2. Where This Appears

Each agent file under `.windsurf/agents/` includes the `<handoff_template>` block near its `<handoffs>` section, so the agent has local access to the canonical format.

## 3. Behavioral Rules

- Handoffs MUST be explicit; agents should never silently chain other agents.
- Agents SHOULD summarize minimal, high-signal context rather than dumping everything.
- Agents MUST respect their `<strict_boundaries>` and prefer handoffs over scope creep.

Use this document as the reference when adjusting or reviewing agent handoff behavior.
