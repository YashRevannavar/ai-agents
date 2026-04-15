# LLM-Wiki: A Persistent Knowledge System

## The Problem

Traditional RAG is stateless. Each query rediscovers knowledge from scratch. AI conversations forget everything between sessions. This problem was fixed by Andrej Karpathy's idea of using markdown files as persistent context for AI agents. The llm-wiki architecture builds on this by creating a second-brain wiki that compounds knowledge over time instead of rediscovering it with each query.

**Stateless RAG is dead.**

## The Solution

A persistent, compounding wiki maintained by an AI agent. Knowledge accumulates instead of being repeatedly rediscovered.

This implementation adapts the original concept with a **knowledge-curator agent** that collaborates with you outside the wiki itself. The curator handles ingestion, organization, and retrieval while you maintain control over what enters your knowledge base.

## Inspiration: Andrej Karpathy

Andrej Karpathy introduced the idea of using markdown files as persistent context for AI agents. His first-principles approach to AI concepts inspired the llm-wiki architecture: give AI agents an interconnected knowledge base, not isolated documents.

## Core Concept

"The wiki is the codebase; you are the programmer."

The knowledge-curator agent collaborates with you from any workspace:
- **You curate** sources and provide context
- **Curator handles** summarizing, cross-referencing, and filing
- **Knowledge compounds** through systematic integration
- **Wiki stays clean** - curation happens outside the vault

Access the curator using `@knowledge-curator` in OpenCode or Claude. Every source is read, summarized, and integrated into entity and concept pages. Links form a knowledge network.

## Architecture

```
/raw/              # Immutable source documents
/wiki/
  sources/         # Summaries of each source
  entities/        # People, organizations, projects
  concepts/        # Ideas, frameworks, technologies
  index.md         # Navigation hub
  log.md           # Operation history
```

## Key Operations

**Ingest**: Add new sources. Agent reads, analyzes context, creates/updates pages, and cross-references.

**Query**: Ask questions. Agent reads index, locates relevant pages, synthesizes answers with citations.

**Lint**: Find broken links, contradictions, stale claims, and research gaps.

## Design Principles

- **Persistence**: Markdown files, version-controlled
- **Compounding**: New information integrates, doesn't replace
- **Cross-Referencing**: Ideas link to related ideas
- **Human-Readable**: Accessible without AI
- **First Principles**: Break complex sources into fundamentals

## Why This Works

Each source enhances understanding of existing concepts. Relationships emerge. Contradictions surface. Knowledge density increases over time.

The system documents its own architecture. This file exists in the wiki it describes.

## Implementation

**Storage**: Obsidian vault with version control

**Format**: Markdown with YAML frontmatter and `[[Wiki-Links]]`

**Agent Access**: The knowledge-curator agent can be invoked from any workspace using `@knowledge-curator`, allowing seamless integration with your existing workflow

**Quality Bar**: Decompose when possible. Don't hide contradictions. Don't overstate certainty.

**Access Pattern**: Projects query (read-only). Only the curator writes (maintains structure).

## The Knowledge-Curator Agent (Evolving)

### Origin of the Idea
I started using Karpathy's concept and kept modifying it. The core innovation I'm developing: **the curator shouldn't be trapped in the wiki context**. It should be accessible from any project directory, any working context. This solves the biggest friction point - context switching between active development and knowledge maintenance.

### The Problem It Solves
When working on a feature or project, I face a choice:
1. Stop work to manually curate wiki updates (context-switching tax)
2. Keep accumulating unorganized notes that never make it to the wiki
3. Lose valuable context and decisions that should compound

The knowledge-curator bridges this gap. It's a collaborator that exists in my workflow, not outside it.

### Two Modes of Operation

#### Ingest Mode
I can invoke the curator while actively working on a project:
- **Trigger**: `@knowledge-curator ingest [source]` from any directory
- **Agent reads**: The source (article, documentation, codebase context, conversation)
- **Analyzes**: Extracts first principles, identifies key concepts
- **Creates/Updates**: Wiki pages for new entities, concepts, or ideas
- **Cross-references**: Automatically suggests and creates bidirectional links
- **No context switching**: Stays in my project flow, updates wiki in background

This transforms how I think about knowledge capture. Instead of "I should document this later," it's "curator, remember this while I keep coding."

#### Query Mode
I can ask the curator questions and get wiki-grounded answers:
- **Trigger**: `@knowledge-curator query [question]` from any workspace
- **Agent reads**: Wiki index and relevant pages
- **Synthesizes**: Provides answer with citations to specific wiki pages
- **Suggests upgrades**: Recommends new connections or missing perspectives
- **Refines thinking**: Takes my half-formed questions and sharpens them against existing knowledge

Example: "Curator, what have I learned about knowledge-state management?" It returns references to relevant pages, surface contradictions, suggests synthesis pages.

### Why First Principles Matters
The curator doesn't just copy-paste. It decomposes every source to first principles:
- A framework becomes: core assumptions → mechanism → application domains → limitations
- A concept becomes: fundamental definition → how it relates to existing ideas → where it breaks
- Research becomes: main finding → evidence quality → implications for my work

This prevents the wiki from becoming a passive archive. Every addition sharpens understanding.

### Current Thinking
- **Access**: Agent invocable from any workspace (OpenCode, projects, Claude)
- **Isolation**: Curation happens outside the vault; the vault stays clean
- **Bidirectionality**: Links work both ways; discovering page A naturally surfaces related pages
- **Evolution**: As the wiki grows, queries get smarter (more context to draw from)

This is still forming, but the core insight holds: **knowledge management should augment work, not interrupt it.**
