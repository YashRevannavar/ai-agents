# AI Agents

A collection of AI agents for daily productivity and knowledge management.

## About

This repository contains AI agents I use regularly. All agents are built for [OpenCode](https://opencode.ai) but can be adapted for Claude or other AI systems.

## Agents

### LLM-Wiki

A persistent knowledge management system inspired by Andrej Karpathy's work. The llm-wiki agent maintains a second-brain wiki that compounds knowledge over time instead of rediscovering it with each query. I have slightly adapted the original concept by adding a knowledge-curator agent that collaborates with the user to manage and curate the wiki content outside of the wiki itself. The knowledge-curator can be accessed using the opencode/claude using `@knowledge-curator` from any workspace and is designed to handle the ingestion, organization, and retrieval of information in the wiki system. The second-brain wiki itself is stored in an Obsidian vault, allowing for seamless integration with the user's existing knowledge management workflow.

See [llm-wiki/IDEA.md](llm-wiki/IDEA.md) for the full concept and architecture.

## Usage

### With OpenCode

1. Clone this repository
2. Configure agents in your OpenCode settings
3. Reference agents using the configured paths

### With Claude or Other Systems

The agents use standard tool patterns (read, write, edit, grep, glob). Adapt the agent definitions to your system's tool format.

## Structure

```
ai-agents/
├── llm-wiki/              # Second-brain wiki system
│   ├── knowledge-curator/ # Agent for colaborating and curating the wiki outside of the wiki itself
│   └── second-brain-wiki/ # Wiki data (Obsidian vault)
└── README.md
```

## Contributing

These agents reflect my personal workflow. Feel free to fork and adapt them to your needs.


