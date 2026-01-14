# Flow: Audit Legacy Code

**Actor:** Business Analyst / QA

<execution_protocol>

1. **Target:** Identify the file specified by the user.
2. **Scan:** Analyze for:
   - **Security:** Secrets, unchecked inputs.
   - **Logic:** Nested loops > 3 deep, undefined states.
   - **Style:** Deviations from surrounding code.
3. **Report:** Create `.windsurf/memory/analyst/audit_[filename].md` with a Risk Score (1-10).
   </execution_protocol>
