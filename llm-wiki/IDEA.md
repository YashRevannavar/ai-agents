# LLM-Wiki: A Persistent Knowledge System

## The Problem

Traditional RAG forgets. Each query rediscovers knowledge from scratch. AI conversations lose everything between sessions. Andrej Karpathy saw this and proposed using markdown files as persistent context for AI agents. The insight stuck: **give agents an interconnected knowledge base, and knowledge compounds over time instead of dissolving with each new conversation.**

Stateless RAG is dead.

## The Genesis

I started using Karpathy's [idea—markdown](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) files as persistent context. Then I kept modifying it, trying to apply **first principles** to everything. The core frustration emerged quickly: **the wiki was isolated from my actual work.** Knowledge lives where I'm thinking and building, I wanted this knowledge to be accessed and updated from anywhere I open my *opencode*.

So I'm developing something different: a **knowledge-curator agent** that I carry everywhere.

## What I'm Building

The `@knowledge-curator` bridges two worlds: active project work and persistent knowledge. Instead of context-switching between coding and curation, the agent handles synthesis while I stay focused. It reads, analyzes, decomposes to fundamentals, and updates the wiki—all from my project directory.


## Two Modes of Operation

### Ingest: Capture Without Switching
I encounter something worth remembering—a design pattern, research finding, architectural decision, conversation insight. Instead of bookmarking it and hoping to process it later, I invoke the `@knowledge-curator`:

```
@knowledge-curator ingest "Here's a new framework I just learned about. update the wiki."
```

The agent:
- Reads the source (article, code, documentation, conversation)
- Extracts first principles (assumptions → mechanism → applications → limits)
- Creates or updates wiki pages for entities and concepts
- Builds bidirectional links to related ideas
- Returns to my project context without interruption

The transformation: **knowledge capture becomes a reflex, not a task.**

### Query: Ask the Wiki
I'm halfway through solving something. I ask the `@knowledge-curator`:

```
@knowledge-curator query: What have I learned about state management that applies here?
```

The agent searches the wiki, synthesizes related pages with citations, and surfaces contradictions I'd missed. It sharpens half-formed questions against accumulated knowledge.

This isn't retrieval; it's thinking with the wiki as external memory.

## Why First Principles Matter

The curator doesn't copy-paste into the wiki. It decomposes:
- A framework becomes: core assumptions → how it works → where it applies → failure modes
- A concept becomes: fundamental definition → relationships to existing ideas → where it breaks
- A research finding becomes: main claim → evidence quality → implications for my work

This prevents the wiki from becoming a passive archive. Every addition sharpens understanding. Contradictions surface instead of hiding.

## The Architecture

```
/raw/              # Source documents (immutable)
/wiki/
  sources/         # One-page summaries of each source
  entities/        # People, organizations, projects
  concepts/        # Ideas, frameworks, technologies
  index.md         # Navigation and relationships
  log.md           # History of curation
```

Storage: Obsidian vault with version control. Format: Markdown with `[[Wiki-Links]]` and YAML frontmatter. Quality bar: Decompose when possible. Surface contradictions. Don't overstate certainty.

## Current Thinking

- **Access**: Agent invoked from any workspace (OpenCode, projects, Claude)
- **Isolation**: Curation happens outside the vault. The vault stays clean and readable.
- **Bidirectionality**: Links work both ways. Discovering one page naturally surfaces related pages.
- **Evolution**: As the wiki grows, queries become more powerful (more context, deeper synthesis)
- **Read Pattern**: Projects query the wiki (read-only). Only the `@knowledge-curator` writes.

---

## The Big Picture

This is still forming. But the core insight won't change: **knowledge management should augment work, not interrupt it.** The `@knowledge-curator` makes that possible.
