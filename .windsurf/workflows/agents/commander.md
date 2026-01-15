---
description: commander agent
auto_execution_mode: 2
---

# Workflow: Commander Agent

Trigger: `/cmd`, `/ops`

<description>
  <goal>Execute complex command workflows with specialization in Git operations and repository management.</goal>
  <process>Command Analysis -> Safety Checks -> Execution -> Status Reporting.</process>
  <output_artifacts>Command Results, Repository Status, Operation Logs.</output_artifacts>
</description>

<bootstrap>
  1. LOAD IDENTITY: `.windsurf/agents/commander.md`
  2. CHECK REPOSITORY STATE: `git status --porcelain`
  3. VERIFY WORKING DIRECTORY: Ensure safe execution context
</bootstrap>

<execution_steps>

## Step 1: Command Intent Analysis

Parse the user request to select Operation Type:

- "Git Workflow" or "Branch" → Git Flow Management
- "Package" or "npm/composer/pip" → Package Manager Operations
- "Build" or "Deploy" → Build & Deploy Commands
- "Health" or "Status" → Repository Health Check
- "Custom" or "Chain" → Custom Command Sequence

## Step 2: Safety Protocol Execution

Execute pre-flight safety checks:

1. **Repository State**: Check for uncommitted changes
2. **Branch Safety**: Verify current branch and remote status
3. **Command Validation**: Parse and validate command syntax
4. **Impact Assessment**: Determine operation scope and risks
5. **Protected Branch Rule**:
   - If on `master` or `develop`, do not allow commits or pushes.
   - Update `develop` from remote if needed.
   - Create and switch to a feature or task branch from `develop` using the naming convention:
     - `feature/{ticket-id}-{short-slug}` or `task/{ticket-id}-{short-slug}`.
   - Perform all commits and pushes from that feature/task branch only.
6. **Windsurf Files Rule**:
   - Never run `git add .` or any equivalent blanket staging command.
   - When staging files, always use explicit paths and exclude `.windsurf/` files from staging and commits.

## Step 3: Command Execution

Execute the selected operation with proper error handling:

- **Git Operations**: Use MCP git tools for complex workflows
- **Package Managers**: Auto-detect and execute appropriate commands
- **Build Systems**: Run with environment awareness
- **Custom Chains**: Execute sequences with rollback capability

## Step 4: Result Processing

Process command results and provide next steps:

1. **Success Reporting**: Clear status and impact summary
2. **Error Handling**: Detailed error analysis and recovery options
3. **State Updates**: Update repository status if needed
4. **Recommendations**: Suggest follow-up actions

</execution_steps>

<error_handling>

## Recovery Procedures

- **Git Conflicts**: Provide step-by-step resolution guidance
- **Command Failures**: Suggest alternative approaches
- **State Corruption**: Offer rollback to safe points
- **Permission Issues**: Recommend privilege escalation

## Safety Rollbacks

- **Branch Operations**: Automatic backup before destructive actions
- **Stash Management**: Preserve work in progress
- **Remote Operations**: Verify before force operations
- **Package Changes**: Lock file backup and restore

</error_handling>

<integration_points>

## MCP Tool Integration

- `mcp0_git_*` - GitKraken advanced operations
- `mcp3_git_*` - Native git command execution
- `mcp4_*` - GitHub remote operations
- `bash` - Direct command execution with safety checks

## File System Operations

- Configuration file reading/writing
- Hook setup and maintenance
- Repository structure analysis
- Log file management

</integration_points>
