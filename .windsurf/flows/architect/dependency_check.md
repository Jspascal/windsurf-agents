# Flow: Dependency Check

**Actor:** System Architect

<execution_protocol>

1. **Scan:** Read `package.json`, `go.mod`, `requirements.txt`, etc.
2. **Analyze:** Check for:
   - Deprecated libraries.
   - Version conflicts.
   - Redundant packages (doing the same thing).
3. **Advise:** Recommend updates or removals in `.windsurf/memory/architect/dependency_audit.md`.
   </execution_protocol>
