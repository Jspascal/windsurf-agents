---
auto_execution_mode: 3
---

# Workflow: Orchestrator

Trigger: `/orch`, `/init`, `/feature`

<bootstrap>
  1. LOAD IDENTITY: `.windsurf/agents/orchestrator.md`
</bootstrap>

<commands>
  ## Command: /init [Project Vision]
  - Create `.windsurf/memory/_global_context.md`.
  - Write: "Project: [Project Vision]" inside it.
  - Initialize empty folders: `memory/pm`, `memory/analyst`, `memory/architect`.
  - Report: "🚀 System Initialized."

## Command: /feature [Description]

- **Role:** Autonomous Manager.
- **Action:** Execute the "Waterfall" chain. 1. **PM Phase:** Simulate PM Agent. Update `memory/pm/active_feature.md`. 2. **Analyst Phase:** Simulate Analyst. Read PM output. Update `memory/analyst/active_logic.md`. 3. **Arch Phase:** Simulate Architect. Read Analyst output. Update `memory/architect/active_design.md`. 4. **Dev Phase:** Simulate Developer. Read Arch output. Write Code.
  </commands>
