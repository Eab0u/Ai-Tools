# Anti-Gravity

## What It Is
Anti-Gravity is a VS Code-based IDE environment that runs Claude Code (or other AI models) as its engine. Think of it as the Ferrari — Claude is the engine, Anti-Gravity is the car. It provides a visual interface, file management, terminal access, and agent management on top of whatever AI model you're using.

## Cost Profile
- **Free tier**: Available at anti-gravity.com
- **Usage cost**: Depends on the model connected (Claude, Gemini, free models via Open Router)
- **Token usage**: Claude Opus 4.6 within Anti-Gravity is more limited than Gemini Pro (which is native to Google)
- **Tip**: Use Open Router free models to extend usage when Claude tokens run out

## Speed
- Fast for agentic loops when using powerful models
- Sub-agents run in parallel — significantly faster than sequential Claude Code
- Agent Teams are slower due to communication overhead between agents

## Best For
- Building full-stack websites and apps with AI
- Running Claude skills in a visual IDE environment
- Managing GitHub + Vercel deployments via MCP
- Running multiple AI agent instances simultaneously
- Connecting external tools via MCP (GitHub, Vercel, Stitch, etc.)

## Not Ideal For
- Simple one-off queries (overkill — just use Claude.ai)
- Projects where agent communication overhead isn't worth it (small tasks)
- Users who want a purely cloud-based setup with no local install

## Key Features
- **Multiple Claude terminals**: Open as many Claude instances as you want side by side
- **Agent Manager**: Manage parallel sub-agents from a visual panel
- **MCP Integration**: Connect GitHub, Vercel, Stitch, and more via MCP servers
- **Skills support**: Install and run Claude skills with `/skillname` commands
- **Model switching**: Swap between Claude, Gemini, DeepSeek, and free models on the fly
- **Extensions**: Install Claude Code extension via Extensions panel (search "claude")
- **Open Code**: Install via terminal for access to 100+ frontier models

## How To Install
1. Go to anti-gravity.com and download for your OS
2. Open Anti-Gravity
3. Create a new folder/project: File > Open Folder > Create
4. Activate Claude: double-click center panel OR go to Extensions > search "claude" > install
5. Or use Terminal > New Terminal > type `claude`

## How To Switch Models (to free/cheaper models)
1. Get an Open Router API key at openrouter.ai > API Keys
2. Deposit $10 to avoid rate limiting (even on free models)
3. Use the model switcher prompt from the resource website (copy-paste into Anti-Gravity)
4. Anti-Gravity will update the settings.json config automatically
5. Restart the terminal to apply
6. To revert to Claude: use the reset prompt from the resource website

## How To Install Skills
```
/skillcreator   ← opens skill creator
/skillname      ← activates a specific installed skill
```
- Download skill folder from community/GitHub
- In Anti-Gravity: tell Claude "install these skills" and paste the GitHub link
- Skills appear in the left panel once installed

## How To Connect GitHub + Vercel (MCP)
1. Create a Vercel account at vercel.com (free)
2. Go to vercel.com/account/settings/tokens > create token
3. In Anti-Gravity: tell Claude "I would like you to add this to my MCP config" + paste token
4. Go to MCP Servers > Manage MCP Servers > View Raw Config to verify
5. Prompt: "Create a GitHub repo, publish it, and create a new website on Vercel"

## Sub-Agents (Parallel Mode)
- Best for: focused independent tasks that don't need to communicate
- Example prompt: "3 sub-agents running in parallel. One: 5 production use cases for Python. Two: 5 for Rust. Three: 5 for Go. Save each as its own markdown file in /research folder."
- Each sub-agent has its own context window
- They do NOT communicate with each other
- Much faster than sequential execution

## Agent Teams (Experimental)
- Best for: complex multi-layer projects where agents need to coordinate
- Agents CAN communicate with each other directly
- Higher token cost due to communication overhead
- Example team: copy agent + UI/design agent + features agent
- Rule: only use agent teams if tasks genuinely need intercommunication
- Cost-saving tip: use powerful model (Opus) as orchestrator, cheaper models (Sonnet/Haiku) for sub-tasks

## When To Use Sub-Agents vs Agent Teams
| Situation | Use |
|---|---|
| Task fits in a few sentences | Single Claude instance |
| Multiple independent research tasks | Sub-agents |
| Complex app with interdependent layers | Agent Teams |
| Simple to-do app, single UI layer | Single Claude (Agent Teams = overkill) |

## Key Prompts To Know
```
# Install Claude Code
[paste install page content] → Anti-Gravity will install it

# Connect to GitHub + Vercel
"I would like you to do two things: connect to GitHub so you can create and publish repos, and connect to Vercel."

# Build + Deploy Website
"Create a GitHub repo, publish it, and create a brand new website for this on Vercel."

# Add Analytics
"I would like the analytics on my website in Vercel please." [paste Vercel analytics snippet]

# Switch to free model
[paste Open Router config prompt] → restarts on new model

# Revert to Claude
[paste Claude reset prompt] → restarts on Claude Opus
```

## Useful Shortcuts
- `Cmd + L` — open/close browser panel
- `Scroll + Shift` — cycles through: ask before edits > edit automatically > plan mode
- `↑` in terminal — cycles through previous commands
- Right-click terminal > Panel Position — move terminal to right/left/bottom
