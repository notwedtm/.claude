# Search Memories by Tags and Content

I'll help you search through your stored memories using tags, content keywords, and semantic similarity. This command is perfect for finding specific information across all your stored memories regardless of when they were created.

## What I'll do:

1. **Tag-Based Search**: I'll search for memories associated with specific tags, supporting both exact and partial tag matching.

2. **Content Search**: I'll perform semantic search across memory content using the same embedding model used for storage.

3. **Combined Queries**: I'll support complex searches combining tags, content, and metadata filters.

4. **Smart Ranking**: I'll rank results by relevance, considering both semantic similarity and tag match strength.

5. **Context Integration**: I'll highlight how found memories relate to your current project and session.

## Usage Examples:

```bash
claude /memory-search --tags "architecture,database"
claude /memory-search "SQLite performance optimization"
claude /memory-search --tags "decision" --content "database backend"
claude /memory-search --project "mcp-memory-service" --type "note"
```

## Implementation:

I'll connect to your MCP Memory Service and use its search capabilities:

1. **Query Processing**: Parse your search criteria (tags, content, filters)
2. **Search Execution**: Use appropriate MCP search functions:
   - `search_by_tag` for tag-based queries
   - `retrieve_memory` for content-based semantic search
   - Combined searches for complex queries
3. **Result Aggregation**: Merge and deduplicate results from multiple search methods
4. **Relevance Scoring**: Calculate combined relevance scores
5. **Context Highlighting**: Show why each result matches your query

For each search result, I'll display:
- **Content**: The memory content with search terms highlighted
- **Tags**: All associated tags (with matching tags emphasized)
- **Relevance Score**: How closely the memory matches your query
- **Created Date**: When the memory was stored
- **Project Context**: Associated project and file context
- **Memory Type**: Classification (note, decision, task, etc.)

## Search Types:

### Tag Search
- **Exact**: `--tags "architecture"` - memories with exact tag match
- **Multiple**: `--tags "database,performance"` - memories with any of these tags
- **Partial**: `--tags "*arch*"` - memories with tags containing "arch"

### Content Search
- **Semantic**: Content-based similarity using embeddings
- **Keyword**: Simple text matching within memory content
- **Combined**: Both semantic and keyword matching

### Filtered Search
- **Project**: `--project "name"` - memories from specific project
- **Type**: `--type "decision"` - memories of specific type
- **Date Range**: `--since "last week"` - memories within time range
- **Author**: `--author "session"` - memories from specific session

## Arguments:

- `$ARGUMENTS` - The search query (content or primary search terms)
- `--tags "tag1,tag2"` - Search by specific tags
- `--content "text"` - Explicit content search terms
- `--project "name"` - Filter by project name
- `--type "note|decision|task|reference"` - Filter by memory type
- `--limit N` - Maximum results to return (default: 20)
- `--min-score 0.X` - Minimum relevance score threshold
- `--include-metadata` - Show full metadata for each result
- `--export` - Export results to a file for review

## Advanced Features:

- **Fuzzy Matching**: Handle typos and variations in search terms
- **Context Expansion**: Find related memories based on current project context
- **Search History**: Remember recent searches for quick re-execution
- **Result Grouping**: Group results by tags, projects, or time periods

If no results are found, I'll suggest alternative search terms, check for typos, or recommend broadening the search criteria. I'll also provide statistics about the total number of memories in your database and suggest ways to improve future searches.