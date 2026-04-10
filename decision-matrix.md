# Decision Matrix — AI Tool Router

Use this to decide which tool(s) to deploy for a given project.

---

## Step 1: What Are You Trying to Do?

| Task | Primary Tool | Supporting Tools |
|---|---|---|
| Build a website/app | Claude Code + Anti-Gravity | Nano Banana 2, Stitch, Vercel |
| Design UI/UX visuals | Google Stitch | Nano Banana 2 |
| Generate product/brand images | Nano Banana 2 | Firecrawl (brand assets) |
| Generate animated scroll video | Nano Banana 2 + Hailuoai | Claude Code (prompt gen) |
| SEO optimize a website | Claude Code (/seooptimizer) | Anti-Gravity |
| Deploy a website live | Anti-Gravity + Vercel | GitHub |
| Run code for free/cheap | Open Router + Claude Code | Anti-Gravity |
| Scrape brand assets from a website | Firecrawl | — |
| Research design inspiration | Google Stitch (Ideation) | — |
| Build repeatable workflow (skill) | Claude Code (/skillcreator) | Anti-Gravity |
| Remember decisions across sessions | MemPalace | Claude Code (MCP) |
| Search past project history | MemPalace | — |
| Recover context after reset/compaction | MemPalace | — |
| Long-running client project (memory) | MemPalace + Claude Code | Anti-Gravity |

---

## Step 2: What Is Your Priority?

### Priority: Cost (Minimize Spend)
1. **Open Router Free** -- Claude Code framework for $0
2. **Gemini Flash via Open Router** -- 10% of Claude cost, 85% quality
3. **Google Stitch** -- Free (15 redesign credits/day)
4. **MemPalace** -- Free, local, no API required
5. **Nano Banana 2** -- Use sparingly, run 4 iterations only when needed

### Priority: Speed (Get It Done Fast)
1. **Claude Sonnet 4.6** -- Fast everyday coding
2. **Gemini Flash** -- Fastest model option
3. **Sub-agents in Anti-Gravity** -- Parallel execution = 3x speed
4. **Google Stitch** -- 30-60 seconds per screen, multiple queries simultaneously
5. **MemPalace wake-up** -- 170 tokens, near-instant context load

### Priority: Quality (Best Output)
1. **Claude Opus 4.6** -- Best reasoning and code quality
2. **Agent Teams** -- Best for complex multi-layer projects
3. **MemPalace + Agent Teams** -- Orchestrator queries past decisions before building
4. **Nano Banana 2 at 2K, 4 iterations** -- Best image quality
5. **Google Stitch with Ideation** -- Research-backed design decisions

### Priority: Security (Sensitive Data / Client Work)
1. **Always use Claude Opus or Sonnet** -- never free/open models for client data
2. **Avoid Open Router** for anything confidential
3. **Anti-Gravity local** -- code stays on your machine
4. **MemPalace** -- everything local, no cloud, no data leaving your machine

### Priority: Memory / Long-Running Projects
1. **MemPalace** -- install first, mine early, let hooks run automatically
2. **MemPalace + Claude Code hooks** -- auto-save every 15 messages, precompact safety net
3. **MemPalace + Agent Teams** -- orchestrator has full project history

---

## Step 3: How Complex Is the Project?

| Complexity | Recommended Setup |
|---|---|
| Simple (explain in 2 sentences) | Single Claude Code instance |
| Medium (a few independent tasks) | Sub-agents in Anti-Gravity |
| Complex (interdependent systems, multiple layers) | Agent Teams in Anti-Gravity |
| Multi-week or longer | Add MemPalace from day one |
| Client project | Add MemPalace + use Claude Opus/Sonnet only |
| Design-first project | Google Stitch -- Claude Code |
| Visual/brand-heavy | Nano Banana 2 -- Claude Code |

---

## Tool Profiles At a Glance

| Tool | Cost | Speed | Quality | Best Use |
|---|---|---|---|---|
| Claude Code (Opus) | $$$ | Good | 5/5 | Complex builds, client work |
| Claude Code (Sonnet) | $$ | Fast | 4/5 | Everyday coding |
| Claude Code (Gemini Flash) | $ | Very fast | 4/5 | Cost-sensitive long sessions |
| Claude Code (Free via OR) | Free | Variable | 3/5 | Prototyping, low-stakes |
| Anti-Gravity | Free | N/A | N/A | IDE environment (pairs with above) |
| Nano Banana 2 | $ | Moderate | 5/5 | Brand images, animations |
| Google Stitch | Free | Fast | 4/5 | UI/UX design, ideation |
| Open Router | Free-$ | Variable | Variable | Model gateway |
| MemPalace | Free | Fast (local) | 5/5 recall | Project memory, decision history |

---

## Common Project Scenarios

### "Build a website for a client"
```
Priority: Quality + Deployment
Stack: Firecrawl -- Nano Banana 2 -- Hailuoai -- Claude Code (Opus) in Anti-Gravity -- Vercel
Memory: MemPalace installed from day one, auto-save hooks active
Tools: Claude Code, Anti-Gravity, Nano Banana 2, Google Stitch (optional), Vercel, GitHub, MemPalace
```

### "Build a website prototype quickly"
```
Priority: Speed + Cost
Stack: Google Stitch (Ideation + Redesign) -- Claude Code (Sonnet or Gemini Flash) in Anti-Gravity
Tools: Google Stitch, Claude Code, Anti-Gravity
```

### "I've run out of Claude tokens mid-project"
```
Priority: Cost (continue working)
Switch to: Open Router Free or Gemini Flash via Open Router
Context recovery: mempalace wake-up --wing <project> to reload critical facts
Tools: Open Router, Claude Code, MemPalace
```

### "Research and generate multiple outputs in parallel"
```
Priority: Speed
Use: Sub-agents in Anti-Gravity
Tools: Claude Code, Anti-Gravity
```

### "Build a complex full-stack app with auth, payments, dashboard"
```
Priority: Quality + Structure
Use: Agent Teams (Opus orchestrator + Sonnet/Haiku sub-agents)
Memory: MemPalace connected via MCP -- orchestrator queries past decisions before each phase
Tools: Claude Code, Anti-Gravity, MemPalace
```

### "Generate brand visuals for a scroll-stopping website"
```
Priority: Visual quality
Stack: Firecrawl -- Claude Code (/assetgeneration skill) -- Nano Banana 2 -- Hailuoai
Tools: Nano Banana 2, Claude Code, Firecrawl
```

### "Long-running project, multiple sessions, need to track decisions"
```
Priority: Memory + Quality
Stack: MemPalace (mine past chats) -- Claude Code -- Anti-Gravity
Setup: mempalace init, mine existing exports, install auto-save hooks
Tools: MemPalace, Claude Code, Anti-Gravity
```

### "I can't remember why we made an architectural decision"
```
Priority: Memory retrieval
Command: mempalace search "why did we [description of decision]" --wing <project>
Or via Claude Code: Claude calls mempalace_search automatically if MCP is connected
Tools: MemPalace
```
