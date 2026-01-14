# Flow: Clear Context

**Actor:** Orchestrator

<execution_protocol>

1. **Confirm:** Ask the user: "WARNING: This will wipe all memory files. Are you sure?"
2. **Wipe:** If confirmed, delete contents of `.windsurf/memory/` (preserving the folders).
3. **Reset:** Re-initialize a blank `.windsurf/memory/_global_context.md`.
4. **Report:** "Memory wiped. Project state reset."
   </execution_protocol>
