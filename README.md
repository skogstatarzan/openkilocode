# OpenKiloCode

Multi-agent configuration for OpenCode and KiloCode CLI with 7 specialized agents and MCP integration.

```
▄████▄ ▄▄▄▄  ▄▄▄▄▄ ▄▄  ▄▄ ██ ▄█▀ ▄▄ ▄▄     ▄▄▄  ▄█████  ▄▄▄  ▄▄▄▄  ▄▄▄▄▄ 
██  ██ ██▄█▀ ██▄▄  ███▄██ ████   ██ ██    ██▀██ ██     ██▀██ ██▀██ ██▄▄  
▀████▀ ██    ██▄▄▄ ██ ▀██ ██ ▀█▄ ██ ██▄▄▄ ▀███▀ ▀█████ ▀███▀ ████▀ ██▄▄▄ 
                                                                  
```

This configuration works with **both OpenCode and KiloCode CLI**.

> **Credit**: Built on top of [oh-my-opencode-slim](https://github.com/alvinunreal/oh-my-opencode-slim) by [@alvinunreal](https://github.com/alvinunreal)

## Quick Start

```bash
curl -fsSL https://raw.githubusercontent.com/skogstatarzan/openkilocode/main/install | bash
```

**That's it!** The installer handles everything:

- ✅ Detects your operating system (macOS, Linux, Windows)
- ✅ Installs missing dependencies (git, Node.js, npm)
- ✅ Installs OpenCode or KiloCode CLI if not present
- ✅ Installs agent-browser for web automation
- ✅ Configures all agents and MCP servers

You'll be asked to choose between **OpenCode** or **KiloCode CLI**. Models are auto-selected per agent.

> **Note**: Connect to OpenCode Zen or Kilo Gateway for the default models to work.

## How It Works

This configuration comes pre-configured with **orchestrator** as the default agent, which automatically delegates tasks to specialist subagents based on the task:

- **@explorer** → Codebase search & discovery
- **@librarian** → Documentation lookup
- **@oracle** → Architecture & high-level decisions
- **@designer** → UI/UX improvements
- **@fixer** → Fast implementation
- **@mapper** → Repository mapping

The orchestrator also uses **skills** when beneficial:
- **cartography** → Maps codebase structure (automatically when you ask to understand/map the codebase or by simply input 'cartography')
- **simplify** → Automatically refines code after changes for clarity

**MCP Servers** are integrated and used by agents when needed:
- **websearch** → Web search (Exa)
- **context7** → Official documentation lookup
- **grep_app** → GitHub code search

Most users only need to interact with the orchestrator—it handles delegation and MCP/skills automatically.

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

Agent prompts are stored in markdown files with frontmatter:

```bash
# For OpenCode
vim ~/.config/opencode/agents/orchestrator.md

# For KiloCode CLI
vim ~/.config/kilo/agents/orchestrator.md
```

For advanced customization (custom agents, models, skills), see the [OpenCode Agents Docs](https://opencode.ai/docs/agents) and [OpenCode Skills Docs](https://opencode.ai/docs/skills).

## Skills

Skills are reusable instructions that can be enabled per agent.

| Skill | Description |
|-------|-------------|
| **cartography** | Repository mapping & codemap generation |
| **simplify** | Code simplification & refinement |
| **agent-browser** | Browser automation for testing |

## API Keys

Add API keys in `opencode.json` if experiencing issues (optional):

```json
{
  "mcp": {
    "websearch": {
      "headers": {
        "x-api-key": "your-exa-key"
      }
    },
    "context7": {
      "headers": {
        "CONTEXT7_API_KEY": "your-context7-key"
      }
    }
  }
}
```

## Directory Structure

```bash
# For OpenCode
~/.config/opencode/
├── opencode.json       # Main configuration
├── agents/             # Agent prompts with frontmatter
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

# For KiloCode CLI
~/.config/kilo/
├── opencode.json       # Main configuration
├── agents/             # Agent prompts with frontmatter
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

> **Note**: On Windows, `~/.config` translates to `%USERPROFILE%\.config\`

## Default Models

| Agent | OpenCode Model | KiloCode Model |
|-------|----------------|----------------|
| orchestrator | `opencode/glm-5` | `kilo/z-ai/glm-5` |
| explorer | `opencode/minimax-m2.5` | `kilo/minimax/minimax-m2.5` |
| oracle | `opencode/claude-sonnet-4-6` | `kilo/anthropic/claude-sonnet-4.6` |
| librarian | `opencode/gemini-3-flash` | `kilo/google/gemini-3-flash-preview` |
| designer | `opencode/gemini-3-flash` | `kilo/google/gemini-3-flash-preview` |
| fixer | `opencode/minimax-m2.5` | `kilo/minimax/minimax-m2.5` |
| mapper | `opencode/minimax-m2.5` | `kilo/minimax/minimax-m2.5` |

## License

MIT
