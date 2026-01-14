# Flow: Status Report

**Actor:** Orchestrator

<execution_protocol>

1. **Scan:** Read the `active_*.md` files in:
   - `.windsurf/memory/pm/` (Active Feature)
   - `.windsurf/memory/architect/` (Active Blueprint)
2. **Context:** Read `.windsurf/memory/_global_context.md` for current phase.
3. **Summarize:** Generate a bulleted report:
   - **Current Phase:** [Phase]
   - **Active Feature:** [Feature Name]
   - **Last Update:** [Timestamp/File modified]
4. **Output:** Display the summary to the user.
   </execution_protocol>
