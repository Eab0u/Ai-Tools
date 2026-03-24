# Google Stitch

## What It Is
Google Stitch is an infinite canvas, AI-powered UI/UX design tool — described as Google's "vibe design tool." It lets you generate, edit, and prototype web and app designs visually without needing Figma or design expertise. Powered by Gemini 3.1 (the world's best design model). Available at stitchwithgoogle.com.

## Cost Profile
- Free to use (Google account required)
- **Redesign credits**: 15 per day (new feature — may increase)
- No subscription required to start
- API key available for connecting to Anti-Gravity/Claude Code

## Speed
- Design generation: 30–60 seconds per screen
- Ideation/research mode: 1–3 minutes
- Redesign (Nano Banana powered): 1–2 minutes
- Multiple queries can run simultaneously (no queue)

## Best For
- Generating UI/UX designs from scratch with no design skills
- Ideating and researching design directions before building
- Redesigning existing websites into new visual styles
- Creating design systems that can be reused across projects
- Exporting design blueprints (design.md) for Claude Code to replicate
- Building out multiple app/website screens consistently (Stitch Loop)

## Not Ideal For
- Final production code (use Claude Code for that)
- Typography-heavy documents
- When you already have a clear design and just need to code it

## Key Features

### 1. Ideation Mode
Research-backed design concepts before committing to anything.
```
How to use:
1. Click "Ideulate" in Stitch
2. Describe your product: "I'm starting a SaaS — find 3 SaaS companies 
   and give me 3 different designs for a pricing page"
3. Stitch researches live + returns 3 strategic design concepts with full briefs
4. Select all concepts you like → "Generate visuals for all three"
5. Pick your favorite → iterate from there
```

### 2. Redesign Mode (Nano Banana powered)
Turn any website screenshot or URL into a new design concept.
```
How to use:
1. Find a website you like (e.g. rocket.net)
2. Screenshot it or copy the URL
3. Click "Redesign" in Stitch
4. Drop in your screenshot/URL
5. Add instructions: "Redesign this for [my company]. Include: hero image, 
   testimonials, how it works, FAQs, CTA, chat interface at bottom"
6. Choose: App (mobile) or Web (desktop) layout
7. Stitch generates concept art using Nano Banana
8. Use this as the visual reference for Claude Code to build from
```
- **15 redesign credits/day** (current limit)
- Works best when you give it layout instructions, not just "redesign this"

### 3. Canvas Editing
Edit designs visually without re-prompting everything.
```
- Click any element → Modify → Edit → change text directly
- Draw annotations on canvas (freehand notes)
- Add comments like "make bigger", "remove trees"
- Click Apply to execute annotation changes
- Multi-select elements across the canvas
- Highlight a page → "Create a landing page for this" → builds next screen in same style
```

### 4. Design.MD Export (Blueprint System)
Extract a reusable design blueprint from any Stitch project.
```
Prompt to Claude (with Stitch MCP connected):
"I would like you to create a design.md based on those designs"

Claude will:
→ Call Stitch MCP list_screens
→ Fetch HTML code from main page
→ Extract design tokens + project metadata
→ Return: color palette, typography, spacing, visual theme, component rules

Use this .md file to:
→ Replicate the exact same style in new pages
→ Ensure consistency across all screens
→ Give Claude Code a style guide to follow
```

### 5. Stitch Loop (Autonomous Multi-Page Generation)
Build out an entire multi-screen app/website without manual involvement.
```
Claude builds screen 1 → passes a "baton file" to itself → builds screen 2 → etc.
Result: consistent multi-page design without you managing each screen
Best for: apps with 5+ screens, multi-page websites
```

### 6. Shading UI Bridge
Converts Stitch designs into Shadcn UI components with best practices baked in.
```
Use when: you want production-ready React components from your Stitch designs
```

## How To Connect Stitch to Anti-Gravity

### Step 1: Get API Key
1. Go to stitchwithgoogle.com
2. Navigate to API Key section
3. Click "Copy Key"

### Step 2: Install in Anti-Gravity
```
1. In Anti-Gravity: click the three dots (•••)
2. Click MCP Servers
3. Type "stitch" in the search
4. Click Install
5. Enter your Stitch API key when prompted
6. Go to Manage Servers > Refresh → Stitch appears in left panel
```

### Step 3: Install Stitch Skills
```
1. Go to the Google official Stitch MCP GitHub repo
2. Click Code > Copy
3. In Anti-Gravity: "Hey, I would like you to add these skills please" + paste link
4. Claude installs skills automatically
```

### Step 4: Verify Connection
```
Prompt: "Could you tell me what the latest design was that I created in Stitch?"
→ Should return: project name, project ID, last updated date
→ If it does, you're fully connected
```

## How To Connect Stitch to Claude Code (VS Code)
```bash
# In Claude Code terminal:
claude mcp add --transport [paste base click code from Stitch docs]
# Provide API key when prompted
# Claude adds it to MCP configuration
# Now usable from Claude Code, Anti-Gravity, or any environment
```

## Full Design-to-Deploy Workflow (with Claude Code)

```
1. IDEATE in Stitch → get 3 design concepts with research
2. GENERATE visuals → pick favorite
3. EDIT on canvas → annotate changes, tweak text, adjust layout
4. REDESIGN images → use Nano Banana (15 credits/day)
5. GET DESIGN.MD → extract blueprint with Claude + Stitch MCP
6. BUILD pages → Claude Code replicates style for all new pages
7. DEPLOY → "Publish to GitHub and Vercel" in Anti-Gravity
```

## Key Prompts

### Ideation
```
"I'm looking to start my own SaaS. Do market research and find 3 SaaS companies. 
Give me 3 different designs for a SaaS pricing page."
```

### Redesign
```
"I would like you to redesign this for me — an entire website based on this URL. 
Beautiful image at the top, testimonials, companies we work with, how it all 
works together, FAQs, and a CTA + chat interface at the bottom."
```

### Get Design Blueprint
```
"I would like you to create a design.md based on those designs."
```

### Build New Page in Same Style
```
"I want the exact same style. Create a new Stitch mock for a SaaS company 
selling VPN subscriptions."
```

### Publish
```
"Publish this to GitHub and Vercel."
```

## Tips
- Use Stitch for concept art first — it's faster to get Claude Code to build from an image than from pure description
- The redesign feature + Nano Banana is an imagination engine — use it for inspiration even if you don't use the output directly
- Run multiple Stitch queries simultaneously — no queue
- Export design.md before switching projects so you always have the style blueprint saved
- Use the Stitch Loop for multi-screen apps so you don't have to babysit every screen
