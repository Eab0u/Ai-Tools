# AI Tool Knowledge Base

A dynamic, living knowledge base for routing between AI coding and design tools. Used as the knowledge source for the **AI Tool Router** Claude skill.

## How This Works

This repo powers a Claude skill that:
1. Reads your project requirements
2. Consults the decision matrix to pick the right tool
3. Pulls step-by-step execution instructions from the relevant tool file
4. Guides you through exactly how to complete the task

## Adding a New Tool

1. Create a new `.md` file in `/tools/` named after the tool (e.g. `my-new-tool.md`)
2. Follow the template structure below
3. Update `decision-matrix.md` to include the new tool in relevant scenarios
4. The skill will automatically pick it up next time it reads the repo

### Tool File Template
```markdown
# Tool Name

## What It Is
[1-2 sentence description]

## Cost Profile
[Pricing details]

## Speed
[How fast is it]

## Best For
[Use cases where this tool shines]

## Not Ideal For
[When to use something else]

## Key Features
[Bullet list of capabilities]

## How To Install / Set Up
[Step-by-step setup]

## Step-By-Step: [Main Workflow]
[The core workflow for this tool]

## Tips
[Anything that saves time or improves results]
```

## Current Tools

| Tool | File | Best For |
|---|---|---|
| Anti-Gravity | `tools/anti-gravity.md` | IDE environment, agent management, deployment |
| Claude Code | `tools/claude-code.md` | Agentic coding, skills, full-stack builds |
| Nano Banana 2 | `tools/nano-banana-2.md` | Brand images, scroll animations, video gen |
| Google Stitch | `tools/google-stitch.md` | UI/UX design, ideation, design systems |
| Open Router | `tools/open-router.md` | Free/cheap model access for Claude Code |

## Repo Structure

```
ai-tool-knowledge-base/
├── README.md                  ← this file
├── decision-matrix.md         ← routing logic (cost, speed, quality, complexity)
└── tools/
    ├── anti-gravity.md
    ├── claude-code.md
    ├── nano-banana-2.md
    ├── google-stitch.md
    └── open-router.md
```

## Source Videos

Tool knowledge was extracted and cleaned from YouTube tutorials by Jack Roberts.
Add new tools by pulling transcripts from new videos and creating a new tool `.md` file.
