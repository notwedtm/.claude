# wedtm's agents

Here's a dump of my current Claude Code agents setup. I primarly use `/start-task` for large features. It helps to write your prompt to this in a different window.

Make it long (like a feature spec or PRD). Only the first agent will have it in it's context, so you can be verbose.

# `/start-task` command

The key here is that we first open a context-manager agent that manages the task context across all agents (via a file).

The coordinator agent then executes tasks using a specialized agent for each task. Each agent has their own context window, this is the key benefit of this flow.

```
/start-task "Your task description here"
```

## Key Agents

**general-purpose** - Research, search, multi-step tasks  
**frontend-pro** - React components, UI, frontend issues  
**debugger** - Fix bugs, errors, test failures  
**performance-engineer** - Optimize bottlenecks, profiling  
**docs-maintainer** - Create/update documentation  
**codebase-janitor** - Clean up orphaned files, organize code  
**code-reviewer** - Review code quality and security  
**architect-reviewer** - Review architectural consistency  
**forensic-code-analyst** - Analyze existing code (read-only)  
**context-manager** - Manage context for multi-agent workflows  
**javascript-pro** - Modern JS, async patterns, Node.js  
**terraform-specialist** - Terraform modules, IaC best practices  
**Simple Solution Subagent** - Quick, direct solutions

## Examples
```
/start-task "Find JWT authentication implementation"
/start-task "Create responsive navbar with mobile menu"
/start-task "Fix failing user registration tests"
/start-task "Clean up orphaned files from auth feature"
/start-task "Optimize dashboard loading performance"
```

## Running Agents Individually

You can also run specific agents directly without using `/start-task`:

```
Use the @agent-debugger to find out why my tests are failing
```

You can even define the tasks more deterministically:

```
Task("debug auth", "Fix the authentication error in login.js", "debugger")
Task("review PR", "Review the changes in pull request #123", "code-reviewer")
Task("analyze performance", "Find performance bottlenecks in the dashboard", "performance-engineer")
```