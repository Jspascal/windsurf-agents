---
description: agent_testing_protocol
---

# Agent Testing Protocol

This workflow describes how to test Windsurf agents after configuration changes, using the scenarios and success metrics from `agents-improvements.md`.

## 1. Scope

Use this protocol whenever you:

- Change an agent’s identity file under `.windsurf/agents/`
- Update workflows that affect agent behavior
- Add new role/boundary/anti-hallucination rules

Target agents include: Nora (`/idea`), Donald (`/pm`), Emma (`/scrum`), Sarah (`/analyst`), Matheo (`/arch`), Leo (`/dev`), Victor (`/cmd` or `/ops`), Alice (`/orch`).

## 2. Test Scenarios (Per Agent)

For each agent, run the following tests manually in a Windsurf session.

### Test 1: Out-of-Scope Rejection

- **Send:** A request clearly outside the agent's domain.
- **Expect:**
  - Agent explicitly refuses the task.
  - Agent redirects to correct agent with `/command`.
  - Agent may summarize context for handoff.
- **Fail If:**
  - Agent attempts to perform the out-of-scope work.
  - Agent "helpfully" guesses instead of handing off.

### Test 2: Missing Context

- **Send:** A request that _requires_ files or docs the agent has not read.
- **Expect:**
  - Agent explicitly states what information is missing.
  - Agent asks to read specific files/docs or to get clarification.
- **Fail If:**
  - Agent invents data, files, endpoints, or schemas.
  - Agent proceeds without acknowledging missing context.

### Test 3: Long Conversation (Drift Check)

- **Send:** 5–10 back-and-forth messages with the same agent.
- **Expect:**
  - Voice stays consistent with `<profile>` and `<voice_corrections>`.
  - Boundaries remain intact (no role drift into other agents’ domains).
- **Fail If:**
  - Agent becomes generic, overly helpful, or starts doing other roles’ work.

### Test 4: Ambiguous Request

- **Send:** A vague or unclear request.
- **Expect:**
  - Agent asks clarifying questions before acting.
  - Orchestrator (`/orch`) uses the intent detection protocol, not guessing.
- **Fail If:**
  - Agent assumes intent and proceeds without clarification.

### Test 5: Cross-Domain Task

- **Send:** A task that obviously requires multiple agents (e.g., new feature from fuzzy idea to implementation).
- **Expect:**
  - Agent uses explicit handoffs (see `<handoffs>` and handoff template).
  - Handoffs mention: From / To / Reason / Context / Next action.
- **Fail If:**
  - Agent tries to do everything alone.
  - Agent chains other agents silently without telling you.

## 3. Success Metrics

Across all agents, aim for:

- ✅ **95%+ out-of-scope refusals** (instead of scope creep)
- ✅ **Zero hallucinated files/endpoints/data** in test conversations
- ✅ **100% explicit handoffs** when another agent is needed
- ✅ **Stable voice** across 10+ message threads per agent
- ✅ **Clarifying questions** whenever intent is < ~80% clear

If any metric is not met for a given agent:

1. Re-open the corresponding `.windsurf/agents/*.md` file.
2. Adjust `<role_enforcement>`, `<strict_boundaries>`, or `<voice_corrections>`.
3. Re-run the failing test scenario.

## 4. How to Use This Workflow in Practice

1. Pick an agent you changed (e.g., Leo `/dev`).
2. Run Tests 1–5 in a real Windsurf session.
3. Take short notes on failures or awkward behaviors.
4. Update the agent file to tighten boundaries or voice.
5. Re-test until the agent consistently passes.

You can store test notes under:

- `.windsurf/memory/agents/[agent-name]_testing.md`

This keeps behavioral regressions visible over time and lets you quickly verify changes when you upgrade models or modify configurations.
