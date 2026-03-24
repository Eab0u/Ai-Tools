# Claude Code

## What It Is
Claude Code is Anthropic's agentic coding framework — described as an "F1 car" where the model (Claude, Gemini, etc.) is the engine. It runs inside Anti-Gravity (or VS Code) and provides an agentic loop, skills system, sub-agents, agent teams, and deep coding capabilities. It's the most powerful AI coding tool currently available.

## Cost Profile
- **Claude Max plan**: $200/month (recommended for heavy use — think of it as hiring a digital employee)
- **Claude Pro**: $20/month (good starting point)
- **Free option**: Use via Open Router with free models (DeepSeek V3, Qwen, etc.) — same framework, different engine
- **Cheap option**: Gemini Flash via Open Router = ~10% of Claude cost for ~85% of performance
- **API pricing** (per million tokens):
  - Claude Opus 4.6: ~$15
  - Claude Sonnet 4.6: ~$9
  - Gemini Flash: ~$1.50
  - DeepSeek V3: Free (rate limited)
  - Qwen: Free (rate limited)

## Speed
- Opus 4.6: Best quality, slightly slower
- Sonnet 4.6: Fast, great for everyday tasks
- Gemini Flash: Very fast, 10% cost
- Free models: Can be slow due to rate limiting

## Best For
- Building complex full-stack websites and apps
- Running skills (packaged instruction sets) for repeatable tasks
- Agentic workflows: sub-agents, agent teams, parallel execution
- SEO optimization, website building, asset generation
- Connecting to GitHub, Vercel, external APIs via MCP

## Not Ideal For
- Quick one-off questions (use Claude.ai chat instead)
- Projects where token cost needs to be near-zero (use free model alternatives)
- Client projects involving sensitive data (use Claude Opus/Sonnet, not free models)

## Skills System
Skills are packaged instruction sets that give Claude Code specific capabilities. Think of them as a "mech suit" for the model.

### Why Skills Matter
- Without skills: Claude is a brilliant but undisciplined junior developer
- With skills: Claude has codified expertise, stops winging it, stops compounding bugs, stops hallucinating

### Key Skills (from Jack Roberts' stack)
| Skill | Purpose |
|---|---|
| `/skillcreator` | Create new skills from scratch |
| `/scrollstopbuilder` | Generate scroll-stop website prompts + HTML views |
| `/assetgeneration` | Generate prompts for 3D image generation |
| `/3dwebsitebuilder` | Build 3D animated responsive websites |
| `/seooptimizer` | Full SEO audit + strategy + HTML report |
| `/bitly` | Convert URLs to Bitly links |

### How To Install Skills
```bash
# Option 1: From community/GitHub
1. Download skill folder
2. In Anti-Gravity: "Install these skills" + paste GitHub link
3. Skills appear in left panel

# Option 2: Manual
1. Import skill folder into your Anti-Gravity project folder
2. Activate: /skillname in Claude terminal

# Option 3: Build your own
/skillcreator → follow the prompts → Claude builds + tests it
```

### How To Use Skills
```bash
/skillname          ← activates the skill
/seo strategy       ← runs SEO strategy skill
/scrollstopbuilder  ← runs scroll stop website builder
```
- Claude will usually auto-detect which skill to use based on context
- You can explicitly invoke with `/` if needed
- Skills auto-trigger based on their description — no need to manually call them most of the time

## Sub-Agents (Parallel Execution)
Run multiple independent tasks simultaneously — 3x faster than sequential.

### How To Use
```
Prompt: "3 sub-agents running in parallel:
- Agent 1: [task A] → save as /research/output-a.md
- Agent 2: [task B] → save as /research/output-b.md  
- Agent 3: [task C] → save as /research/output-c.md"
```
- Each agent has its own context window (up to 1M tokens)
- Agents do NOT communicate with each other
- Best for: independent research, parallel file generation, batch tasks

## Agent Teams (Multi-Agent Orchestration)
Agents that communicate with each other — for complex interdependent projects.

### When To Use
- Complex full-stack apps with multiple interdependent layers
- Projects needing discussion and collaboration between specializations
- NOT for simple tasks (communication overhead makes it slower + more expensive)

### Example Team Structure
```
Orchestrator (Claude Opus 4.6)
├── Copy Agent (writes all text/content)
├── UI/Design Agent (builds visual components)
└── Features Agent (implements functionality)
```

### Cost-Saving Strategy
- Use Opus as the orchestrator brain
- Use Sonnet 4.6 or Haiku for sub-tasks
- Keeps quality high while reducing token spend

### Install Agent Teams
```bash
# In Anti-Gravity terminal:
[paste agent teams install page content]
Anti-Gravity installs it automatically
```

## Running Claude Code for Free (Open Router Method)

### Setup
1. Go to openrouter.ai > API Keys > Create new key
2. Deposit $10 (prevents rate limiting even on free models)
3. Set credit limit: $15, reset: monthly
4. Copy the API key
5. In Anti-Gravity: paste the model-switching prompt + API key
6. Anti-Gravity updates settings.json automatically
7. Restart terminal to apply

### Model Comparison
| Model | Cost/1M tokens | Performance | Speed | Security |
|---|---|---|---|---|
| Claude Opus 4.6 | $15 | 10/10 | Good | High |
| Claude Sonnet 4.6 | $9 | 9/10 | Fast | High |
| Gemini Flash | $1.50 | 8.5/10 | Very fast | Medium |
| DeepSeek V3 | Free | 7/10 | Slow (rate limited) | Low |
| Open Router Free | Free | Varies | Varies | Low |

### Switching Models
```bash
# To switch to Gemini Flash:
[copy Gemini Flash config prompt from resource site]
Paste into Anti-Gravity → it updates config → restart terminal

# To revert to Claude:
[copy Claude reset prompt from resource site]  
Paste into Anti-Gravity → restart terminal
```

### Settings.json
- Can be edited at project level (affects only that project)
- Or at global level (affects all terminals)

## Building a Website: Full Workflow

### Step 1: Brand Extraction
```
Go to firecrawl.dev > Scrape > Markdown > Branding
Extract: colors, logo, typography, brand voice
```

### Step 2: Asset Generation
```
/scrollstopbuilder
Prompt: "Build me an HTML view from [company] which is [description], 
visuals: [what you want to see]"
Copy the assembled image prompt
```

### Step 3: Image Generation
```
→ Nano Banana 2 (see nano-banana-2.md)
```

### Step 4: Video Generation
```
→ Hailuoai with Kling 3.0 (see nano-banana-2.md)
```

### Step 5: Build the Website
```
In Anti-Gravity + Claude Code:
"Which file would you like me to use for the scroll-driven animation?"
→ Select your downloaded video file
→ Allow all permissions
→ Claude builds the MVP
```

### Step 6: HTML Reference (replicate existing site structure)
```
1. Find the client's existing site
2. Google "HTML website extractor" → download as HTML
3. In Anti-Gravity: "I've downloaded the HTML from the original website. 
   Use it to recreate with new copy and scroll-stopping animation."
```

### Step 7: Multiple Pages + SEO
```
Prompt: "Look at my current site and understand the existing design language.
Ask me which pages I want to create. For each page, match the existing design exactly.
Add full SEO optimization. Include structured data. Make it fully responsive.
Update navigation across all pages. After creating all pages, run a full SEO audit
across every page, giving me a report. Show what's optimized and ranking improvements."
```

### Step 8: Deploy
```
"Create a GitHub repo. Publish it. Create a brand new website for this on Vercel."
→ Returns GitHub link + live Vercel URL
```

### Step 9: Buy Domain
```
vercel.com → find your project → Domains → type domain → assign
```

### Step 10: Analytics
```
vercel.com → project → Analytics → Enable → copy snippet
In Anti-Gravity: "I would like the analytics on my website in Vercel please." + paste snippet
```

## SEO Optimization Skill Workflow
```
/seo strategy
→ Choose: full site or article/page
→ Enter URL
→ Skill runs: fetch homepage → discover pages → fetch robots.txt/sitemap 
  → analyze each page → cross-page analysis → score → HTML report → open in browser
→ Get score out of 100 + breakdown: executive summary, page breakdown, 
  keywords, internal linking, action plan
```

## Key Claude Code Hacks
- `Scroll + Shift`: toggle between ask-before-edits / edit-automatically / plan mode
  - Use "edit automatically" to save time on large builds
- Multiple terminals: spin up as many Claude instances as you want
- Open Code: install for access to 100+ frontier models (`install open code` in terminal)
- Project context: open a specific project folder → Claude already knows the full context
