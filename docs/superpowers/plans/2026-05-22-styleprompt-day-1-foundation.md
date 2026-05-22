# StylePrompt Day 1 Foundation Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Create the Day 1 product foundation for StylePrompt AI: positioning, homepage messaging, first user flow, Style DNA schema, Character Kit schema, and content template.

**Architecture:** This plan creates a documentation-first product foundation before scaffolding the web app. The outputs live under `docs/product/` and become the source of truth for future UI, data, and prompt template implementation.

**Tech Stack:** Markdown documentation, Git, future Next.js + Tailwind CSS implementation.

---

## File Structure

- Create: `docs/product/positioning.md`
  Product name, audience, pain point, promise, homepage messaging, and launch language.
- Create: `docs/product/first-user-flow.md`
  The first complete user journey from landing page to Style DNA result to Character Kit result.
- Create: `docs/product/style-dna-schema.md`
  Input fields, option sets, output fields, and example result for the Style DNA flow.
- Create: `docs/product/character-kit-schema.md`
  Input fields, option sets, output fields, and example result for the Character Kit flow.
- Create: `docs/product/content-template.md`
  Template for producing inspiration styles and character examples.
- Modify: `README.md`
  Add links to the new product foundation documents.

---

### Task 1: Create Product Positioning Source Of Truth

**Files:**
- Create: `docs/product/positioning.md`

- [ ] **Step 1: Create the product docs directory**

Run:

```powershell
New-Item -ItemType Directory -Force -Path 'D:\01灵感起源\docs\product'
```

Expected:

```text
Directory: D:\01灵感起源\docs
product
```

- [ ] **Step 2: Create `docs/product/positioning.md`**

Write this content:

```markdown
# StylePrompt AI Product Positioning

## Product Name

Working name: StylePrompt AI

## One-Line Positioning

StylePrompt AI helps AI creators build a personal art style and original character system instead of relying on generic prompts.

Chinese:

StylePrompt AI 帮助 AI 创作者建立专属画风和原创角色体系，而不是继续复制通用提示词。

## Core Pain Point

AI creators can generate images, but the results often look generic, inconsistent, and hard to reuse as a recognizable personal identity.

The product solves three connected problems:

- The creator cannot clearly describe their own visual taste.
- The creator's characters lack personality, symbols, story, and repeatable visual rules.
- The creator cannot keep a consistent style across Midjourney, Nano Banana, Imagen, Flux, and other image models.

## First Target User

The first target user is the AI drawing creator or self-media creator who wants a recognizable avatar, mascot, comic lead, recurring personal IP, or visual identity for social publishing.

Primary channels:

- Xiaohongshu
- X
- Pinterest
- Instagram
- TikTok
- YouTube Shorts

## Product Promise

English:

Build your own AI art style and original character.

Chinese:

打造你的专属 AI 画风和原创角色。

## Homepage Headline

English:

Build Your Own AI Art Style and Original Character

Chinese:

打造你的专属 AI 画风和原创角色

## Homepage Subtitle

English:

Generate a reusable personal style system, original character design kit, and multi-model prompts from your mood, visual taste, and creative goal.

Chinese:

通过情绪、视觉偏好和创作目标，生成可复用的个人画风系统、原创角色设定卡和多模型提示词。

## Primary Calls To Action

- Start Style DNA
- Create Character Kit

## Product Principles

- Make personalization the center, not prompt copying.
- Turn taste into reusable visual rules.
- Treat characters as systems, not single images.
- Avoid dependence on artist names, copyrighted IP names, or brand imitation.
- Make every generated output useful across multiple image models.
```

- [ ] **Step 3: Review the file**

Run:

```powershell
Get-Content -LiteralPath 'D:\01灵感起源\docs\product\positioning.md' -Raw -Encoding UTF8
```

Expected:

```text
# StylePrompt AI Product Positioning
```

- [ ] **Step 4: Commit**

Run:

```powershell
git add docs/product/positioning.md
git commit -m "docs: define product positioning"
```

Expected:

```text
[main ...] docs: define product positioning
```

---

### Task 2: Define The First User Flow

**Files:**
- Create: `docs/product/first-user-flow.md`

- [ ] **Step 1: Create `docs/product/first-user-flow.md`**

Write this content:

```markdown
# First User Flow

## Goal

The first user flow must help a creator move from a vague desire for a more personal style to a saved Style DNA and Character Kit.

## Entry Point

The user lands on the home page and sees:

- Headline: Build Your Own AI Art Style and Original Character
- Primary CTA: Start Style DNA
- Secondary CTA: Create Character Kit

## Flow A: Style DNA First

1. User clicks `Start Style DNA`.
2. User selects a creative goal.
3. User selects mood direction.
4. User selects visual preference.
5. User selects color preference.
6. User selects line and texture preference.
7. User selects character proportion.
8. User selects avoid directions.
9. System generates Style DNA.
10. User copies multi-model prompt skeletons.
11. User clicks `Create Character From This Style`.

## Flow B: Character Kit First

1. User clicks `Create Character Kit`.
2. User chooses character role.
3. User chooses personality.
4. User chooses world context.
5. User chooses signature symbol.
6. User chooses output model.
7. System asks whether to use a Style DNA.
8. If no Style DNA exists, system applies a default balanced creator style.
9. System generates Character Kit.
10. User copies model prompts or saves the kit.

## MVP Result Page Actions

Style DNA result page:

- Copy Midjourney skeleton.
- Copy Nano Banana skeleton.
- Copy Imagen skeleton.
- Copy Flux skeleton.
- Create Character From This Style.
- Save Style DNA.

Character Kit result page:

- Copy Midjourney prompt.
- Copy Nano Banana prompt.
- Copy Imagen prompt.
- Copy Flux prompt.
- Save Character Kit.
- Generate another character in this style.

## Success Criteria

The flow succeeds when a first-time user can complete the journey without knowing art terminology before arriving.

The generated result should feel:

- Specific.
- Repeatable.
- Personal.
- Useful across multiple image models.
- Safe from direct IP, brand, or living-artist imitation.
```

- [ ] **Step 2: Review the file**

Run:

```powershell
Get-Content -LiteralPath 'D:\01灵感起源\docs\product\first-user-flow.md' -Raw -Encoding UTF8
```

Expected:

```text
# First User Flow
```

- [ ] **Step 3: Commit**

Run:

```powershell
git add docs/product/first-user-flow.md
git commit -m "docs: define first user flow"
```

Expected:

```text
[main ...] docs: define first user flow
```

---

### Task 3: Define Style DNA Schema

**Files:**
- Create: `docs/product/style-dna-schema.md`

- [ ] **Step 1: Create `docs/product/style-dna-schema.md`**

Write this content:

```markdown
# Style DNA Schema

## Purpose

Style DNA converts a creator's taste into reusable visual rules and multi-model prompt skeletons.

## Input Fields

### Creative Goal

Options:

- Avatar
- IP persona
- Comic lead
- Xiaohongshu visual identity
- Short-video character
- Profile image series

### Mood Direction

Options:

- Warm
- Mysterious
- Cute
- Dark
- Elegant
- Retro
- Dreamy
- Futuristic
- Calm
- Rebellious

### Audience

Options:

- Personal expression
- Fans and community
- Clients
- Niche subculture
- Public creator brand

### Visual Preference

Options:

- Cinematic
- Illustrated
- Anime-inspired
- 3D
- Editorial
- Hand-drawn
- Soft fantasy
- Retro-futurist

### Color Preference

Options:

- Soft pastel
- High contrast
- Muted earth
- Neon night
- Monochrome accent
- Bright candy
- Ink wash
- Luxury dark

### Line And Texture

Options:

- Clean vector
- Painterly brush
- Pencil sketch
- Clay
- Paper cut
- Film grain
- Glossy 3D
- Watercolor

### Character Proportion

Options:

- Realistic
- Semi-realistic
- Chibi
- Tall elegant
- Stylized anime
- Toy-like
- Mascot-like

### Avoid Directions

Options:

- Overly generic
- IP-like
- Artist-name-dependent
- Logo text
- Overcomplicated costume
- Low consistency

## Output Fields

- Style name
- One-sentence style description
- Style personality
- Visual keywords
- Color palette
- Line and texture rules
- Lighting and composition rules
- Character proportion rules
- Good use cases
- Avoided directions
- Midjourney prompt skeleton
- Nano Banana prompt skeleton
- Imagen prompt skeleton
- Flux prompt skeleton
- Negative prompt

## Example Output

### Style Name

Soft Neon Diary Persona

### One-Sentence Style Description

A warm but slightly mysterious creator-avatar style that blends diary-like intimacy, soft neon color accents, gentle facial expressions, and repeatable character proportions.

### Style Personality

Quiet, observant, emotional, lightly futuristic, and friendly enough for social media publishing.

### Visual Keywords

soft neon, diary mood, gentle face, clean silhouette, expressive eyes, cozy urban night, subtle glow, creator avatar

### Color Palette

- Warm ivory
- Mist blue
- Soft violet
- Neon pink accent
- Deep midnight gray

### Line And Texture Rules

Use clean semi-illustrated lines, soft gradients, slight film grain, and minimal clothing detail. Avoid noisy texture and overloaded accessories.

### Lighting And Composition Rules

Use soft front light with a neon rim light. Keep the face readable. Prefer medium close-up, centered composition, and quiet background depth.

### Character Proportion Rules

Use semi-realistic proportions with slightly enlarged eyes and a clear silhouette. Keep the head, hairstyle, and signature accessory consistent.

### Good Use Cases

- Creator avatar
- Xiaohongshu cover character
- Short-video host persona
- Personal IP profile image series

### Avoided Directions

Avoid direct anime IP imitation, overdesigned cyberpunk armor, unreadable dark faces, text in the image, and random symbols.

### Midjourney Prompt Skeleton

personal creator avatar, soft neon diary mood, gentle semi-realistic face, expressive eyes, clean silhouette, cozy urban night background, warm ivory and mist blue palette with soft violet and neon pink accents, subtle film grain, centered medium close-up composition, soft front light, neon rim light, consistent hairstyle and signature accessory --ar 3:4 --stylize 250

### Nano Banana Prompt Skeleton

Create a personal creator avatar in a soft neon diary style. Use a gentle semi-realistic face, expressive eyes, a clean silhouette, and a cozy urban night background. The palette should combine warm ivory, mist blue, soft violet, and small neon pink accents. Keep the hairstyle and one signature accessory consistent for future character variations.

### Imagen Prompt Skeleton

A high-quality semi-realistic creator avatar with a soft neon diary mood, gentle facial expression, expressive eyes, clean silhouette, cozy urban night setting, warm ivory and mist blue colors, soft violet shadows, subtle neon pink accent, soft front lighting, and readable centered composition.

### Flux Prompt Skeleton

semi-realistic creator avatar, soft neon diary mood, gentle face, expressive eyes, clean silhouette, cozy urban night, warm ivory, mist blue, soft violet, neon pink accent, subtle film grain, soft front light, neon rim light, centered medium close-up, consistent hairstyle, signature accessory

### Negative Prompt

low quality, blurry, distorted face, inconsistent hairstyle, extra fingers, text, logo, watermark, direct IP imitation, overcomplicated costume, unreadable dark lighting
```

- [ ] **Step 2: Review the file**

Run:

```powershell
Get-Content -LiteralPath 'D:\01灵感起源\docs\product\style-dna-schema.md' -Raw -Encoding UTF8
```

Expected:

```text
# Style DNA Schema
```

- [ ] **Step 3: Commit**

Run:

```powershell
git add docs/product/style-dna-schema.md
git commit -m "docs: define style dna schema"
```

Expected:

```text
[main ...] docs: define style dna schema
```

---

### Task 4: Define Character Kit Schema

**Files:**
- Create: `docs/product/character-kit-schema.md`

- [ ] **Step 1: Create `docs/product/character-kit-schema.md`**

Write this content:

```markdown
# Character Kit Schema

## Purpose

Character Kit turns a user brief and Style DNA into a reusable original character design package.

## Input Fields

### Character Role

Options:

- Creator avatar
- Mascot
- Comic lead
- Fantasy character
- Daily-life persona
- Short-video host

### Character Personality

Options:

- Gentle
- Sharp
- Chaotic
- Elegant
- Lonely
- Playful
- Brave
- Shy
- Mysterious
- Healing

### World Context

Options:

- Modern city
- Fantasy town
- Cyber street
- Cozy studio
- Campus
- Traveling diary
- Magical realism

### Signature Symbol

Options:

- Accessory
- Color
- Object
- Hairstyle
- Clothing detail
- Small prop
- Pattern
- Visual motif

### Output Model

Options:

- Midjourney
- Nano Banana
- Imagen
- Flux
- All models

### Reference Style DNA

Optional saved Style DNA object.

## Output Fields

- Character name
- Character tagline
- Personality summary
- Backstory
- Visual identity
- Face and hairstyle
- Outfit design
- Color palette
- Signature symbols
- Expressions
- Poses
- Scene ideas
- Character consistency rules
- Midjourney prompt
- Nano Banana prompt
- Imagen prompt
- Flux prompt
- Negative prompt

## Example Output

### Character Name

Mira Lumen

### Character Tagline

A quiet night-diary creator who collects tiny city lights and turns them into visual stories.

### Personality Summary

Mira is calm, observant, and gently mysterious. She feels approachable but has a private inner world, making her suitable for personal essays, visual diaries, and creator-avatar content.

### Backstory

Mira lives in a small rooftop studio above a glowing city street. Every night, she records fragments of light from windows, vending machines, trains, and rainy sidewalks, then turns them into illustrated memories.

### Visual Identity

Semi-realistic creator-avatar character with soft neon diary aesthetics, clean silhouette, expressive eyes, and a recurring small star-shaped hairpin.

### Face And Hairstyle

Oval face, soft expression, slightly enlarged reflective eyes, short layered dark hair with mist-blue highlights, and a small star-shaped hairpin on the left side.

### Outfit Design

Warm ivory oversized jacket, muted midnight inner layer, small violet scarf, simple crossbody notebook pouch, and no complex armor or crowded accessories.

### Color Palette

- Warm ivory
- Midnight gray
- Mist blue
- Soft violet
- Neon pink accent

### Signature Symbols

- Star-shaped hairpin
- Small notebook pouch
- Neon pink thread detail

### Expressions

- Gentle smile
- Quiet focus
- Slight surprise
- Thoughtful side glance

### Poses

- Holding a small notebook
- Looking at city lights
- Standing under soft neon rain
- Turning back with a quiet smile

### Scene Ideas

- Rooftop studio at night
- Rainy street with vending machine glow
- Train window reflection
- Desk covered with small light sketches

### Character Consistency Rules

Keep the star-shaped hairpin, short dark hair with mist-blue highlights, warm ivory jacket, and soft neon diary palette in every generation. Do not change the character into a different age group, species, or costume genre.

### Midjourney Prompt

Mira Lumen, original semi-realistic creator avatar character, quiet night-diary mood, short layered dark hair with mist-blue highlights, small star-shaped hairpin on the left side, warm ivory oversized jacket, muted midnight inner layer, small violet scarf, crossbody notebook pouch, expressive reflective eyes, soft neon diary aesthetic, cozy urban night background, subtle film grain, soft front light, neon rim light, centered character design portrait --ar 3:4 --stylize 250

### Nano Banana Prompt

Create an original semi-realistic creator-avatar character named Mira Lumen. She has short layered dark hair with mist-blue highlights, a small star-shaped hairpin on the left side, expressive reflective eyes, a warm ivory oversized jacket, a muted midnight inner layer, a small violet scarf, and a crossbody notebook pouch. Use a soft neon diary mood with cozy urban night lighting. Keep her design consistent for future variations.

### Imagen Prompt

An original semi-realistic creator-avatar character named Mira Lumen, quiet and mysterious, short dark layered hair with mist-blue highlights, star-shaped hairpin, expressive reflective eyes, warm ivory oversized jacket, violet scarf, small notebook pouch, soft neon diary aesthetic, cozy urban night scene, soft front light, subtle neon rim light, clean centered character design portrait.

### Flux Prompt

Mira Lumen, original creator avatar, semi-realistic, quiet night diary mood, short dark hair, mist-blue highlights, star hairpin, expressive eyes, warm ivory oversized jacket, midnight inner layer, violet scarf, notebook pouch, soft neon diary aesthetic, cozy urban night, subtle film grain, soft front light, neon rim light, clean character portrait

### Negative Prompt

low quality, blurry, distorted face, different hairstyle, missing hairpin, inconsistent outfit, extra fingers, text, logo, watermark, direct IP imitation, overcomplicated armor, unreadable lighting
```

- [ ] **Step 2: Review the file**

Run:

```powershell
Get-Content -LiteralPath 'D:\01灵感起源\docs\product\character-kit-schema.md' -Raw -Encoding UTF8
```

Expected:

```text
# Character Kit Schema
```

- [ ] **Step 3: Commit**

Run:

```powershell
git add docs/product/character-kit-schema.md
git commit -m "docs: define character kit schema"
```

Expected:

```text
[main ...] docs: define character kit schema
```

---

### Task 5: Define Content Production Template

**Files:**
- Create: `docs/product/content-template.md`

- [ ] **Step 1: Create `docs/product/content-template.md`**

Write this content:

```markdown
# Content Production Template

## Purpose

This template keeps StylePrompt AI content focused on personal style and original character design instead of generic prompt collection.

## Inspiration Style Template

### Style Name

Use a name that describes the mood and creator use case.

Example:

Soft Neon Diary Persona

### Style Purpose

Explain who should use this style and why.

Example:

For creators who want a gentle, memorable avatar style suitable for visual diaries, profile images, and short-form personal storytelling.

### Visual DNA Tags

Use 5 to 8 tags.

Example:

- soft neon
- diary mood
- semi-realistic face
- cozy urban night
- expressive eyes
- clean silhouette
- subtle film grain
- personal IP

### Character Use-Case Suggestion

Example:

Best for creator avatars, personal mascots, Xiaohongshu cover characters, and recurring visual diary narrators.

### Prompt Set

Each style must include:

- Midjourney prompt
- Nano Banana prompt
- Imagen prompt
- Flux prompt
- Negative prompt

## Character Example Template

### Character Name

Example:

Mira Lumen

### Character Role

Example:

Creator avatar

### Character Personality

Example:

Quiet, observant, gentle, mysterious, and healing.

### Signature Symbols

Example:

- Star-shaped hairpin
- Notebook pouch
- Neon pink thread detail

### Consistency Rules

Example:

Keep the star-shaped hairpin, short dark hair with mist-blue highlights, warm ivory jacket, and soft neon diary palette in every generation.

### Prompt Set

Each character must include:

- Midjourney prompt
- Nano Banana prompt
- Imagen prompt
- Flux prompt
- Negative prompt

## Quality Checklist

Before publishing a style or character example, confirm:

- It solves personalization, not only decoration.
- It contains repeatable visual rules.
- It avoids direct IP, brand, and living-artist naming.
- It includes clear character symbols.
- It works across at least four model prompt formats.
- It has a negative prompt that protects consistency.
```

- [ ] **Step 2: Review the file**

Run:

```powershell
Get-Content -LiteralPath 'D:\01灵感起源\docs\product\content-template.md' -Raw -Encoding UTF8
```

Expected:

```text
# Content Production Template
```

- [ ] **Step 3: Commit**

Run:

```powershell
git add docs/product/content-template.md
git commit -m "docs: add content production template"
```

Expected:

```text
[main ...] docs: add content production template
```

---

### Task 6: Update README Navigation

**Files:**
- Modify: `README.md`

- [ ] **Step 1: Add product foundation links to `README.md`**

Insert this section after `## Current Documents`:

```markdown
## Product Foundation

- `docs/product/positioning.md`
  Product name, promise, audience, pain point, homepage headline, and launch messaging.
- `docs/product/first-user-flow.md`
  First user journey from landing page to Style DNA and Character Kit.
- `docs/product/style-dna-schema.md`
  Input fields, option sets, output fields, and example Style DNA result.
- `docs/product/character-kit-schema.md`
  Input fields, option sets, output fields, and example Character Kit result.
- `docs/product/content-template.md`
  Production template for inspiration styles and character examples.
```

- [ ] **Step 2: Verify README contains the new section**

Run:

```powershell
Select-String -LiteralPath 'D:\01灵感起源\README.md' -Pattern 'Product Foundation'
```

Expected:

```text
README.md:...:## Product Foundation
```

- [ ] **Step 3: Commit**

Run:

```powershell
git add README.md
git commit -m "docs: link product foundation"
```

Expected:

```text
[main ...] docs: link product foundation
```

---

### Task 7: Final Verification And Push

**Files:**
- Verify: all files under `docs/product/`
- Verify: `README.md`

- [ ] **Step 1: Check repository status**

Run:

```powershell
git status --short --branch
```

Expected:

```text
## main...origin/main [ahead 5]
```

The exact ahead count may be 6 if the plan document itself was committed separately.

- [ ] **Step 2: Inspect final docs tree**

Run:

```powershell
Get-ChildItem -LiteralPath 'D:\01灵感起源\docs\product'
```

Expected files:

```text
positioning.md
first-user-flow.md
style-dna-schema.md
character-kit-schema.md
content-template.md
```

- [ ] **Step 3: Push to GitHub**

Run:

```powershell
git push
```

Expected:

```text
main -> main
```

---

## Self-Review

### Spec Coverage

- Product positioning is covered by Task 1.
- First user flow is covered by Task 2.
- Style DNA input and output structure is covered by Task 3.
- Character Kit input and output structure is covered by Task 4.
- Content production template is covered by Task 5.
- Repository navigation is covered by Task 6.
- GitHub sync is covered by Task 7.

### Placeholder Scan

This plan intentionally avoids vague fill-in language. Every file has concrete content, exact paths, verification commands, and commit commands.

### Type And Naming Consistency

The same names are used across all tasks:

- Style DNA
- Character Kit
- StylePrompt AI
- `docs/product/`
- `positioning.md`
- `first-user-flow.md`
- `style-dna-schema.md`
- `character-kit-schema.md`
- `content-template.md`
