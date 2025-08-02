# Store Memory with Context

I'll help you store information in your MCP Memory Service with proper context and tagging. This command captures the current session context and stores it as a persistent memory that can be recalled later.

## What I'll do:

1. **Detect Current Context**: I'll analyze the current working directory, recent files, and conversation context to understand what we're working on.

2. **Capture Memory Content**: I'll take the provided information or current session summary and prepare it for storage.

3. **Add Smart Tags**: I'll automatically generate relevant tags based on:
   - Current project directory name
   - Programming languages detected
   - File types and patterns
   - Any explicit tags you provide

4. **Store with Metadata**: I'll include useful metadata like:
   - Timestamp and session context
   - Project path and git repository info
   - File associations and dependencies

## Usage Examples:

```bash
claude /memory-store "We decided to use SQLite-vec instead of ChromaDB for better performance"
claude /memory-store --tags "decision,architecture" "Database backend choice rationale"
claude /memory-store --type "note" "Remember to update the Docker configuration after the database change"
```

## Implementation:

I'll first check if the MCP Memory Service is running and accessible. If it's available, I'll use the mDNS discovery to find the service endpoint, or fall back to the default localhost configuration.

The content will be stored with automatic context detection:
- **Project Context**: Current directory, git repository, recent commits
- **Session Context**: Current conversation topics and decisions
- **Technical Context**: Programming language, frameworks, and tools in use
- **Temporal Context**: Date, time, and relationship to recent activities

If the memory service is not available, I'll provide clear instructions on how to start it and retry the operation.

## Arguments:

- `$ARGUMENTS` - The content to store as memory, or additional flags:
  - `--tags "tag1,tag2"` - Explicit tags to add
  - `--type "note|decision|task|reference"` - Memory type classification
  - `--project "name"` - Override project name detection
  - `--private` - Mark as private/sensitive content

I'll ensure the memory is stored successfully and provide confirmation of the storage operation, including the generated content hash and applied tags.