# MemPalace

## What It Is
MemPalace is a local, open-source AI memory system that stores your conversations, decisions, and project history in a searchable semantic database on your machine. Where the other tools in this stack help you *build* things, MemPalace helps you *remember* what you built and why. It integrates with Claude Code via MCP (19 tools) and as a native Claude Code plugin.

Benchmark note: MemPalace scores 96.6% R@5 on LongMemEval in raw ChromaDB mode with zero API calls -- the highest published score for a free tool. The AAAK compression layer is experimental and currently scores lower (84.2%) -- use raw mode for reliability.

## Cost Profile
- **Free** -- open source, MIT license
- No subscription, no cloud, no API key required after install
- Runs entirely on your machine
- Optional: ~$10/year in API costs if you use the hybrid rerank mode (which hits 100%)

## Speed
- Search: fast (local ChromaDB semantic search)
- Mining conversations: moderate, one-time setup cost
- Wake-up context load: ~170 tokens, near-instant
- No rate limiting (everything is local)

## Best For
- Long-running client projects where decisions need to be traceable
- Teams where multiple people work with the same AI and need shared context
- Any project lasting more than a few weeks where "why did we do this?" is a real question
- Recovering context when Claude's context window runs out or resets
- Cross-project search ("what was our approach to auth in the last three projects?")
- Agent Teams workflows where the orchestrator needs project history before starting

## Not Ideal For
- One-off or throwaway projects (setup cost not worth it)
- Projects with no past history to mine
- Users who want zero local install overhead

## Key Features

### Palace Architecture
Conversations are organized into wings (people/projects), halls (memory types), and rooms (specific topics). This structure gives a 34% retrieval improvement over flat search.

### Memory Layers
- L0: Identity (~50 tokens, always loaded)
- L1: Critical facts -- team, projects, preferences (~120 tokens, always loaded)
- L2: Room recall -- recent sessions and current project (on demand)
- L3: Deep semantic search across all history (on demand)

Total wake-up cost: ~170 tokens. Targeted searches add ~13,500 tokens max.

### MCP Integration (19 Tools)
Claude Code can call MemPalace tools automatically mid-task:
- `mempalace_search` -- semantic search with wing/room filters
- `mempalace_add_drawer` -- save verbatim content
- `mempalace_kg_query` -- entity relationships with time filtering
- `mempalace_traverse` -- walk across wings via tunnels
- `mempalace_diary_read/write` -- specialist agent memory

### Auto-Save Hooks
Two Claude Code hooks that run automatically:
- **Save Hook**: every 15 messages, structured save of decisions and changes
- **PreCompact Hook**: emergency save before context compression fires

### Knowledge Graph
Temporal entity-relationship triples (SQLite, local). Tracks who decided what, when, and whether it's still true. Similar to Zep's Graphiti but free and offline.

## How To Install

```bash
pip install mempalace

# Initialize your world
mempalace init ~/projects/myapp

# Mine existing conversations and project files
mempalace mine ~/projects/myapp                         # code, docs, notes
mempalace mine ~/chats/ --mode convos                   # Claude, ChatGPT, Slack exports

# Connect to Claude Code via MCP
claude mcp add mempalace -- python -m mempalace.mcp_server

# Or via native plugin
claude plugin marketplace add milla-jovovich/mempalace
claude plugin install --scope user mempalace
```

## How To Set Up Auto-Save Hooks

Add to your Claude Code hooks config:

```json
{
  "hooks": {
    "Stop": [{"matcher": "", "hooks": [{"type": "command", "command": "/path/to/hooks/mempal_save_hook.sh"}]}],
    "PreCompact": [{"matcher": "", "hooks": [{"type": "command", "command": "/path/to/hooks/mempal_precompact_hook.sh"}]}]
  }
}
```

## Core Workflow

```
1. INSTALL: pip install mempalace + claude plugin install
2. INIT: mempalace init <project-dir>
3. MINE: point at your chats and project folders
4. HOOK: set up auto-save hooks in Claude Code
5. WORK: Claude calls mempalace_search automatically when it needs context
6. PERSIST: hooks save decisions every 15 messages
```

## Key Commands

```bash
# Search anything you've ever discussed
mempalace search "why did we switch to GraphQL"
mempalace search "auth decisions" --wing myapp

# Load world context for a session
mempalace wake-up
mempalace wake-up --wing driftwood

# Check palace status
mempalace status

# Split large chat export files before mining
mempalace split ~/chats/ --dry-run
mempalace split ~/chats/
```

## Where It Fits in the Stack

MemPalace is a supporting tool, not a primary build tool. It pairs with:
- **Claude Code + Anti-Gravity**: attaches via MCP, hooks fire automatically during coding sessions
- **Agent Teams**: orchestrator agent can query MemPalace for past project decisions before starting
- **Open Router free sessions**: when you switch to a cheaper model mid-project, MemPalace provides the context the new model doesn't have

## Tips
- Mine your existing Claude.ai chat exports before starting a new project phase -- you likely have months of decisions sitting in JSON files
- The `mempalace split` command is important if your exports are concatenated multi-session files
- Don't use AAAK compression mode for retrieval -- raw mode is more accurate (96.6% vs 84.2%)
- Set up the PreCompact hook first -- it protects you from the most painful context loss scenario
- For team use, each person mines their own chats but can share a project wing
