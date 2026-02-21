---
name: dewey-docs
description: Generate AI-agent-ready documentation using Dewey. Use when asked to "set up docs", "create documentation", "make docs agent-friendly", "generate AGENTS.md", or "add llms.txt".
---

# Dewey Documentation Toolkit

Dewey generates AI-agent-ready documentation for software projects. It creates AGENTS.md, llms.txt, docs.json, and install.md files that AI coding agents can consume effectively.

## When to Use

Activate this skill when the user asks to:
- "Set up documentation for my project"
- "Make my docs AI-friendly"
- "Generate AGENTS.md"
- "Create an llms.txt file"
- "Add agent-ready docs"
- "Set up Dewey"

## Installation

```bash
pnpm add @arach/dewey
# or
npm install @arach/dewey
```

## CLI Commands

| Command | Purpose |
|---------|---------|
| `dewey init` | Create docs/ folder and dewey.config.ts |
| `dewey audit` | Check documentation completeness |
| `dewey generate` | Create AGENTS.md, llms.txt, docs.json, install.md |
| `dewey agent` | Score agent-readiness (0-100 scale) |

## Quick Setup

```bash
# 1. Install
pnpm add @arach/dewey

# 2. Initialize
npx dewey init

# 3. Generate agent files
npx dewey generate
```

## Configuration (dewey.config.ts)

```typescript
import { defineConfig } from '@arach/dewey'

export default defineConfig({
  project: {
    name: 'my-project',
    tagline: 'A brief description',
    type: 'npm-package', // or 'cli-tool', 'macos-app', 'react-library', 'monorepo', 'generic'
  },

  agent: {
    criticalContext: [
      'Always use TypeScript',
      'Run tests before committing',
    ],
    entryPoints: {
      'Source': 'src/',
      'Tests': 'tests/',
      'Config': 'config/',
    },
    rules: [
      { pattern: '*.test.ts', instruction: 'Use vitest for testing' },
    ],
    sections: ['overview', 'quickstart', 'api'],
  },

  docs: {
    path: './docs',
    output: './',
    required: ['overview.md', 'quickstart.md'],
  },
})
```

## Project Types

| Type | Best For |
|------|----------|
| `npm-package` | Published npm packages |
| `cli-tool` | Command-line tools |
| `macos-app` | macOS applications |
| `react-library` | React component libraries |
| `monorepo` | Multi-package workspaces |
| `generic` | Other projects |

## Generated Files

### AGENTS.md
Combined documentation with critical context for AI agents

### llms.txt
Plain text summary optimized for LLM context windows

### docs.json
Structured JSON for programmatic access

### install.md
LLM-executable installation instructions following installmd.org standard

## Agent Content Pattern

Each doc page should have two versions:
```
docs/
├── overview.md           # Human-readable
├── agent/
│   └── overview.agent.md # Agent-optimized (dense, structured)
```

**Agent versions should be:**
- Dense (no prose, just facts)
- Structured (tables, explicit values)
- Self-contained (no URL fetching needed)

## Workflow

1. **Initialize**: `npx dewey init`
2. **Write docs**: Create human-readable markdown in `docs/`
3. **Add agent versions**: Create `docs/agent/*.agent.md`
4. **Configure**: Set critical context in dewey.config.ts
5. **Generate**: `npx dewey generate`
6. **Audit**: `npx dewey audit`
7. **Score**: `npx dewey agent` (target: 80+)

## Resources

- GitHub: https://github.com/arach/dewey
- Docs: https://deweydata.io
