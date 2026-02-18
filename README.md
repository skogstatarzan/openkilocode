# OpenCode Pantheon

Multi-agent configuration for OpenCode with 7 specialized agents and MCP integration.

```
▄▄▄▄▄                     ▄▄▄   ▄▄▄     ▄▄        ▄▄▄▄▄▄▄          ▄▄       
▄███████▄                   ███ ▄███▀ ▀▀  ██       ███▀▀▀▀▀          ██       
███   ███ ████▄ ▄█▀█▄ ████▄ ███████   ██  ██ ▄███▄ ███      ▄███▄ ▄████ ▄█▀█▄ 
███▄▄▄███ ██ ██ ██▄█▀ ██ ██ ███▀███▄  ██  ██ ██ ██ ███      ██ ██ ██ ██ ██▄█▀ 
 ▀█████▀  ████▀ ▀█▄▄▄ ██ ██ ███  ▀███ ██▄ ██ ▀███▀ ▀███████ ▀███▀ ▀████ ▀█▄▄▄ 
          ██                                                                  
          ▀▀                                                                  
```

## Quick Start

```bash
curl -fsSL https://raw.githubusercontent.com/skogstatarzan/opencode-config/main/install -o install.sh && bash install.sh
```

The installer will ask you to choose:
- **OpenCode** → Config: `~/.config/opencode`
- **KiloCode CLI** → Config: `~/.config/kilo`

Models are auto-selected based on your choice. Connect to OpenCode Zen or Kilo Gateway for them to work.

## Agents

| Agent | Role | Mode | Description |
|-------|------|------|-------------|
| **orchestrator** | Primary | `primary` | Delegates tasks to specialists |
| **explorer** | Search | `subagent` | Fast codebase navigation |
| **oracle** | Advisor | `subagent` | Architecture & debugging |
| **librarian** | Research | `subagent` | Documentation lookup |
| **designer** | UI/UX | `subagent` | Visual polish |
| **fixer** | Builder | `subagent` | Fast implementation |
| **mapper** | Cartography | `subagent` | Repository mapping |

## MCP Servers

| Server | Purpose | API Key |
|--------|---------|---------|
| **websearch** | Web search via Exa | `EXA_API_KEY` (optional) |
| **context7** | Official docs lookup | `CONTEXT7_API_KEY` (optional) |
| **grep_app** | GitHub code search | None required |

## Usage

```bash
# Start OpenCode
opencode

# Or for KiloCode CLI
kilo

# Switch agents with Tab
# Or invoke subagents directly:
@explorer find all API routes
@librarian look up React hooks docs
@oracle review this architecture
@designer improve the dashboard styling
@fixer implement the auth module
@mapper map the codebase structure
```

## Configuration

### Edit Agent Prompts

```bash
vim ~/.config/opencode/agents/orchestrator.md
```

### Change Models

Edit `~/.config/opencode/opencode.json`:

```json
{
  "agent": {
    "orchestrator": {
      "model": "opencode/gpt-5.1-codex"
    }
  }
}
```

### Add Custom Agent

Create `~/.config/opencode/agents/my-agent.md`:

```markdown
---
description: My custom agent
mode: subagent
model: opencode/gpt-5.1-codex
---

You are a custom agent that does X, Y, Z.
```

## Skills

Skills are reusable instructions that can be enabled per agent.

| Skill | Description |
|-------|-------------|
| **cartography** | Repository mapping & codemap generation |
| **simplify** | Code simplification & refinement |
| **agent-browser** | Browser automation for testing |

### Enable a Skill

In `opencode.json`:

```json
{
  "agent": {
    "designer": {
      "skills": ["agent-browser"]
    }
  }
}
```

## Environment Variables

```bash
# MCP API keys (optional but recommended)
export EXA_API_KEY="your-key"
export CONTEXT7_API_KEY="your-key"
```

## Directory Structure

```
~/.config/opencode/
├── opencode.json       # Main configuration
├── agents/             # Agent prompts (editable)
│   ├── orchestrator.md
│   ├── explorer.md
│   ├── oracle.md
│   ├── librarian.md
│   ├── designer.md
│   ├── fixer.md
│   └── mapper.md
└── skills/             # Skills
    ├── cartography/
    ├── simplify/
    └── agent-browser/
```

## Default Models

| Agent | Default Model |
|-------|---------------|
| orchestrator | `opencode/glm-5` |
| explorer | `opencode/minimax-m2.5` |
| oracle | `opencode/claude-sonnet-4-6` |
| librarian | `opencode/gemini-3-flash` |
| designer | `opencode/gemini-3-flash` |
| fixer | `opencode/minimax-m2.5` |
| mapper | `opencode/minimax-m2.5` |

## Requirements

- OpenCode or KiloCode CLI installed (`opencode` or `kilo` in PATH)
- Git for installation

## License

MIT
