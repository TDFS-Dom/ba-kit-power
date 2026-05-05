---
inclusion: manual
---

# BA-kit Skill — ba-notion (Notion Publishing)

Push BA-kit artifacts to Notion through MCP.

## Invocation
```
ba-notion srs --slug warehouse-rfp --module auth-flow --page <url> --mode overwrite
ba-notion frd --slug warehouse-rfp --module auth-flow --parent <url> --mode create
ba-notion backbone.md --page <url> --mode append
ba-notion srs --slug warehouse-rfp --mode fill-gaps
```

## Supported Inputs
Artifact aliases: `intake`, `backbone`, `frd`, `stories`, `srs`, `wireframe-map`
Or explicit file path to markdown artifact.

## Publish Modes
- `create`: new Notion page from source
- `append`: keep existing + append new content below
- `overwrite`: replace existing page body
- `fill-gaps`: compare headings, append only missing sections
- `auto` (default): choose safest operation based on context

## Destination Resolution
1. `--page <url|id>` → target page to update
2. `--parent <url|id>` → create new page under parent
3. Neither → search Notion for exact match
4. One match → use it
5. Ambiguous → ask

## Rules
- Read source artifact from disk first
- Fetch `notion://docs/enhanced-markdown-spec` before creating/updating
- Preserve source language (usually Vietnamese)
- Use source document title as Notion page title
- If updating would delete child pages/databases → confirm first
- After publishing report: source path, destination URL, mode used, created/updated

## Notion Tools
- `notion_fetch` → inspect target page
- `notion_search` → find described destination
- `notion_create_pages` → create new page
- `notion_update_page` → `replace_content` (overwrite) or `update_content` (append/fill-gaps)
