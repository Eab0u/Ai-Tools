# Open Router

## What It Is
Open Router is a unified API gateway that gives you access to hundreds of AI models — including free ones — through a single API key. When used with Claude Code, it lets you swap out Claude's engine for cheaper or free alternatives while keeping all of Claude Code's framework features (skills, agentic loop, sub-agents, etc.).

## Cost Profile
- **Free models available**: DeepSeek V3, Qwen, Open Router Free (cycles through free models)
- **Cheap models**: Gemini Flash (~$1.50/1M tokens = ~10% of Claude cost)
- **Deposit recommendation**: Put in $10 even if using free models — prevents rate limiting
- **Credit limit setting**: Set to $15/month with monthly reset

## Speed
- Gemini Flash: Very fast
- DeepSeek V3 (free): Can be slow, rate limited
- Qwen (free): Sometimes rate limited / wait times
- Open Router Free tier: Cycles through models automatically, reduces wait times vs. picking one free model

## Best For
- Running Claude Code framework for free or near-free
- Extending your coding sessions when Claude tokens run out
- Testing and prototyping where top-tier model quality isn't critical
- Long burns of code generation where cost-per-token matters

## Not Ideal For
- Client projects with sensitive data (stick to Claude Opus/Sonnet)
- Tasks requiring peak reasoning quality (use Claude Opus)
- When reliability is critical (free models can be rate limited)

## Model Comparison (for Claude Code use)
| Model | Cost/1M tokens | Performance | Speed | Use Case |
|---|---|---|---|---|
| Claude Opus 4.6 | $15 | 10/10 | Good | Client work, complex projects |
| Claude Sonnet 4.6 | $9 | 9/10 | Fast | Everyday coding |
| Gemini Flash | $1.50 | 8.5/10 | Very fast | Long coding sessions, cost-sensitive |
| DeepSeek V3 | Free | 7/10 | Slow (rate limited) | Prototyping, low-stakes work |
| Qwen | Free | 6.5/10 | Variable | Same as DeepSeek |
| Open Router Free | Free | Varies | Variable | Best free option (auto-cycles models) |

## How To Set Up Open Router with Claude Code

### Step 1: Create Account + API Key
1. Go to openrouter.ai
2. Click API Keys in sidebar
3. Click "Create new API key"
4. Name it (e.g. "claude-code-free")
5. Set credit limit: $15
6. Set reset: Monthly
7. Click Create
8. **Copy the API key immediately** (won't show again)

### Step 2: Deposit $10
- Even on free models, having $10 in your account prevents rate limiting
- Go to openrouter.ai > Credits > Add Credits

### Step 3: Configure Claude Code to Use Open Router
```
1. Go to the resource website (Jack Roberts' community link)
2. Select your desired model from the dropdown
3. Click "Copy" — this copies the config prompt
4. Open Anti-Gravity
5. Create a new folder/project
6. Open Claude agent window
7. Paste the copied config prompt + your Open Router API key
8. Claude updates settings.json automatically
9. Shut down terminal → reopen terminal
10. Type `claude` → verify model shows (e.g. "Gemini 2.5 Pro Preview")
```

### Step 4: Verify the Model
```
In Claude terminal:
"Hey there, what model is this?"
→ Should return something like "Google Gemini 7.5 Preview" or the model you selected
```

### Step 5: Switch Between Models
```
# To switch to a different model:
1. Go back to resource website
2. Select new model → Copy
3. Paste into Anti-Gravity agent window
4. Claude switches the config
5. Restart terminal

# To revert to Claude:
1. Go to resource website
2. Click "Revert to Claude" / copy reset prompt
3. Paste into Anti-Gravity
4. Restart terminal
5. Verify: should show "Opus 4.6" or "Sonnet 4.6"
```

## Settings.json Details
- **Project level**: create settings.json in your project folder → affects only that project
- **Global level**: edit the global settings.json → affects all terminals
- Anti-Gravity handles this automatically when you use the config prompts
- You can also edit it manually if you know the file location

## Open Router Free Tier (Best Free Option)
The "Open Router Free" plan automatically cycles through whichever free models are available:
- Better than picking a single free model (avoids being stuck waiting on one rate-limited model)
- Trades off: you don't know exactly which model is running at any given time
- Good for: bulk code generation, non-critical tasks

## Open Code (Alternative)
Open Code is a separate tool that also gives access to 100+ frontier models:
```bash
# Install in Anti-Gravity terminal:
"install open code"
# OR paste the Open Code install command from their site

# Run:
open code
# → shows model list, make selections, proceed
```
- Lets you use ChatGPT Plus subscription as well if you have one
- Link a full video for more details (Jack Roberts mentions this in his content)

## Tips
- **Don't use a single free model** (DeepSeek, Qwen) for heavy work — rate limiting kills momentum. Use the Open Router Free cycling plan instead.
- **False economy warning**: Free isn't always cheaper. You pay with your time correcting mistakes and waiting on rate limits. For client work, always use Claude.
- **Multi-panel strategy**: Have one Anti-Gravity panel just for model control (checking which model is active) and separate panels for actual coding work.
- **Skills are portable**: Even if you switch to a free model, all your installed Claude skills still work — the skills travel with the framework, not the model.
