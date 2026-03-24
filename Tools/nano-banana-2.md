# Nano Banana 2

## What It Is
Nano Banana 2 is an AI image (and video) generation tool — the latest and most powerful model in its line. It's used primarily for generating high-quality product/brand visuals, animated scroll-stop images, and reference images for website builds. It integrates directly into the Claude Code + Anti-Gravity workflow.

## Cost Profile
- Separate tool with its own credits/API
- Can be accessed via API key (no need for the UI if you have an API)
- Jack Roberts uses Hailuoai for the video generation step (not affiliated — API key works too)

## Speed
- Image generation: moderate (multiple iterations recommended)
- Video generation: handled by a separate tool (Hailuoai/Kling 3.0)
- Run 4 iterations per image to get best results

## Best For
- Generating brand-specific product images for websites
- Creating "exploded" or deconstructed versions of images for scroll animations
- Generating start/end frames for animated video transitions
- Image-to-image reference workflows (reference a previous image to build the next)
- Redesigning website visuals inside Google Stitch

## Not Ideal For
- Quick throwaway visuals (overkill for simple placeholder images)
- Text-heavy design work (use Stitch for that)

## Key Settings
- **Resolution**: Always use **2K minimum** (1K looks amateur)
- **Aspect ratio**: **16x9** for websites
- **Iterations**: Always run **4 iterations** to have options to choose from
- **Background**: Specify **clean white background** so nothing touches the edges (critical for web use)
- **Reference image**: Use the "reference" feature to chain images — generate image A, then reference it to generate image B (exploded version)

## Step-By-Step: Generate Brand Images for a Website

### Step 1: Extract Brand Identity
1. Go to firecrawl.dev
2. Scrape > Markdown > Branding for the client's website
3. Note: colors, logo, typography, brand assets

### Step 2: Generate Image Prompts (via Claude Code skill)
1. In Claude Code: `/scrollstopbuilder` (or use asset generation skill)
2. Prompt: "Using the skill, build me an HTML view from [company type] which is full of [items], I want the visuals to be [description]"
3. Copy the generated prompt for your assembled/hero image

### Step 3: Generate the Hero Image
1. Open Nano Banana 2
2. Set: 16x9, 2K, 4 iterations, clean white background
3. Upload the brand logo (grab from Google if needed)
4. Upload a reference photo of the product/van/item if available
5. Paste the prompt from Step 2
6. Run — pick the best result

### Step 4: Generate the Exploded/Deconstructed Version
1. Click "Reference" on your chosen hero image
2. Switch to the "exploded load" prompt (from Claude Code skill output)
3. Paste the exploded prompt
4. Run — this creates the animated version of the same image

### Step 5: Generate the Transition Video
1. Download both images (assembled + exploded)
2. Go to Hailuoai (or use API)
3. Upload start frame (assembled image) + end frame (exploded image)
4. Paste the video transition prompt (from Claude Code skill)
5. Settings: Kling 3.0, 7 seconds, no multi-shot, no enhance
6. Generate — download video when complete

### Step 6: Embed in Website
1. Drop the video into Anti-Gravity + Claude Code
2. Use the 3D website builder skill
3. Prompt: "Use the last file I downloaded — integrate the scroll-stopping animation"

## Image Chaining Workflow
```
Brand assets (Firecrawl) 
    → Prompt generation (Claude Code skill)
        → Hero image (Nano Banana 2, 4 iterations, 2K, white bg)
            → Reference hero → Exploded version (Nano Banana 2)
                → Video transition (Hailuoai, start frame + end frame)
                    → Embed in website (Anti-Gravity + Claude Code)
```

## Use Inside Google Stitch
- Stitch has a **Redesign** feature powered by Nano Banana 2
- Drop in a URL screenshot or Dribbble inspiration image
- Stitch generates a full-page redesign as a concept image
- 15 redesign credits per day (new feature limit)
- Works for both mobile (app) and desktop (web) layouts
- Use annotations to guide changes: draw on the canvas, add notes, click Apply

## Tips
- Spar with it — run multiple versions, don't accept the first result
- The scroll animation is only as good as your start and end images — spend time here
- Low quality input images = low quality output — grab the highest res logo/photo you can
- Nano Banana is also available natively inside Gemini 3 Pro High (within Anti-Gravity) for redesign tasks
