# OpenKiloCode

Multi-agent configuration for OpenCode and KiloCode CLI with 7 specialized agents and MCP integration.

```
▄████▄ ▄▄▄▄  ▄▄▄▄▄ ▄▄  ▄▄ ██ ▄█▀ ▄▄ ▄▄     ▄▄▄  ▄█████  ▄▄▄  ▄▄▄▄  ▄▄▄▄▄ 
██  ██ ██▄█▀ ██▄▄  ███▄██ ████   ██ ██    ██▀██ ██     ██▀██ ██▀██ ██▄▄  
▀████▀ ██    ██▄▄▄ ██ ▀██ ██ ▀█▄ ██ ██▄▄▄ ▀███▀ ▀█████ ▀███▀ ████▀ ██▄▄▄ 
                                                                 
```

This configuration works with **both OpenCode and KiloCode CLI**.

> **Credit**: Built on top of [oh-my-opencode-slim](https://github.com/alvinunreal/oh-my-opencode-slim) by [@alvinunreal](https://github.com/alvinunreal)

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

Most users only need to interact with the orchestrator—it handles delegation automatically.

## Quick Start

```bash
curl -LfsSL https://raw.githubusercontent.com/skogstatarzan/openkilocode/main/install -o install.sh && bash install.sh
```

The installer will ask you to choose:
- **OpenCode** → Config: `~/.config/opencode`
- **KiloCode CLI** → Config: `~/.config/kilo`

Models are auto-selected per agent. Connect to OpenCode Zen or Kilo Gateway for them to work.

### Requirements

- OpenCode or KiloCode CLI installed (`opencode` or `kilo` in PATH)
- Git for installation

**Linux (Debian/Ubuntu)**
```bash
sudo apt update && sudo apt install git
```

**Linux (Fedora/RHEL)**
```bash
sudo dnf install git
```

**macOS**
```bash
brew install git
```

**Windows (via winget)**
```bash
winget install Git.Git
```

## MCP Servers

| Server | Purpose |
|--------|---------|
| **websearch** | Web search via Exa |
| **context7** | Official docs lookup |
| **grep_app** | GitHub code search |

> **Note**: API keys are added directly in `opencode.json`. See [API Keys](#api-keys) section below.

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

Add API keys directly in `opencode.json`:

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
