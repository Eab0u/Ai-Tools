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

---

## Step 2: What Is Your Priority?

### Priority: Cost (Minimize Spend)
1. **Open Router Free** → Claude Code framework for $0
2. **Gemini Flash via Open Router** → 10% of Claude cost, 85% quality
3. **Google Stitch** → Free (15 redesign credits/day)
4. **Nano Banana 2** → Use sparingly, run 4 iterations only when needed

### Priority: Speed (Get It Done Fast)
1. **Claude Sonnet 4.6** → Fast everyday coding
2. **Gemini Flash** → Fastest model option
3. **Sub-agents in Anti-Gravity** → Parallel execution = 3x speed
4. **Google Stitch** → 30–60 seconds per screen, multiple queries simultaneously

### Priority: Quality (Best Output)
1. **Claude Opus 4.6** → Best reasoning and code quality
2. **Agent Teams** → Best for complex multi-layer projects
3. **Nano Banana 2 at 2K, 4 iterations** → Best image quality
4. **Google Stitch with Ideation** → Research-backed design decisions

### Priority: Security (Sensitive Data / Client Work)
1. **Always use Claude Opus or Sonnet** — never free/open models for client data
2. **Avoid Open Router** for anything confidential
3. **Anti-Gravity local** → code stays on your machine

---

## Step 3: How Complex Is the Project?

| Complexity | Recommended Setup |
|---|---|
| Simple (explain in 2 sentences) | Single Claude Code instance |
| Medium (a few independent tasks) | Sub-agents in Anti-Gravity |
| Complex (interdependent systems, multiple layers) | Agent Teams in Anti-Gravity |
| Design-first project | Google Stitch → Claude Code |
| Visual/brand-heavy | Nano Banana 2 → Claude Code |

---

## Tool Profiles At a Glance

| Tool | Cost | Speed | Quality | Best Use |
|---|---|---|---|---|
| Claude Code (Opus) | $$$ | Good | ★★★★★ | Complex builds, client work |
| Claude Code (Sonnet) | $$ | Fast | ★★★★☆ | Everyday coding |
| Claude Code (Gemini Flash) | $ | Very fast | ★★★★☆ | Cost-sensitive long sessions |
| Claude Code (Free via OR) | Free | Variable | ★★★☆☆ | Prototyping, low-stakes |
| Anti-Gravity | Free | N/A | N/A | IDE environment (pairs with above) |
| Nano Banana 2 | $ | Moderate | ★★★★★ | Brand images, animations |
| Google Stitch | Free | Fast | ★★★★☆ | UI/UX design, ideation |
| Open Router | Free–$ | Variable | Variable | Model gateway |

---

## Common Project Scenarios

### "Build a website for a client"
```
Priority: Quality + Deployment
Stack: Firecrawl → Nano Banana 2 → Hailuoai → Claude Code (Opus) in Anti-Gravity → Vercel
Tools: Claude Code, Anti-Gravity, Nano Banana 2, Google Stitch (optional), Vercel, GitHub
```

### "Build a website prototype quickly"
```
Priority: Speed + Cost
Stack: Google Stitch (Ideation + Redesign) → Claude Code (Sonnet or Gemini Flash) in Anti-Gravity
Tools: Google Stitch, Claude Code, Anti-Gravity
```

### "I've run out of Claude tokens mid-project"
```
Priority: Cost (continue working)
Switch to: Open Router Free or Gemini Flash via Open Router
Tools: Open Router, Claude Code (framework stays the same)
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
Tools: Claude Code, Anti-Gravity
```

### "Generate brand visuals for a scroll-stopping website"
```
Priority: Visual quality
Stack: Firecrawl → Claude Code (/assetgeneration skill) → Nano Banana 2 → Hailuoai
Tools: Nano Banana 2, Claude Code, Firecrawl
```
