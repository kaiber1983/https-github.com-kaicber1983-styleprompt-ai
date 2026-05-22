# StylePrompt AI v0.1 Product Design

## 1. Product Positioning

StylePrompt AI is a lightweight AI visual design workspace for creators who want a more personal art style and more distinctive original characters.

The first version should not be a broad AI style gallery. Its core job is to help an AI creator define a reusable personal style system, then use that system to generate original character design kits and multi-model prompts.

Core promise:

> Build your own AI art style and original character.

Chinese promise:

> 打造你的专属 AI 画风和原创角色。

## 2. Target User

The first target segment is AI drawing creators and self-media creators.

Typical users:

- AI art creators who publish on Xiaohongshu, X, Pinterest, Instagram, TikTok, or YouTube Shorts.
- Creators who want a recognizable avatar, IP persona, mascot, comic lead, or recurring visual character.
- Beginners who can use AI image tools but cannot describe a personal style in professional visual language.
- Creators who feel their outputs look generic, inconsistent, or too similar to common prompt examples.

The first version should not prioritize ecommerce teams, game studios, enterprise brand systems, team workflows, or image-to-3D.

## 3. Pain Point

The main problem is not lack of prompts. The main problem is lack of personalization.

Users struggle with:

- Their AI images look generic and interchangeable.
- Their characters lack clear personality, story, visual symbols, and repeatable design rules.
- They do not know how to translate taste into concrete visual language such as color, silhouette, line quality, material, lighting, composition, or character proportion.
- They cannot keep a consistent style across Midjourney, Nano Banana, Imagen, Flux, and other tools.
- They save scattered images and prompts, but cannot turn them into a reusable personal visual system.

## 4. MVP Product Shape

The MVP should be a tool-first website with two core flows:

1. Style DNA
   A guided diagnostic flow that turns user preferences into a personal AI art style system.

2. Character Kit
   A character design generator that uses the Style DNA to output a distinctive original character package.

The style library is still useful, but only as an inspiration and calibration layer. It should support the two flows instead of becoming the product center.

## 5. Core Pages

### Home

Purpose:
Explain the product in five seconds and push users into Style DNA or Character Kit.

Primary headline:

> Build Your Own AI Art Style and Original Character

Chinese headline:

> 打造你的专属 AI 画风和原创角色

Subtitle:

> Generate a reusable personal style system, original character design kit, and multi-model prompts from your mood, visual taste, and creative goal.

Chinese subtitle:

> 通过情绪、视觉偏好和创作目标，生成可复用的个人画风系统、原创角色设定卡和多模型提示词。

Primary CTA:

- Start Style DNA
- Create Character Kit

Homepage sections:

- Hero with direct visual examples.
- Three-step workflow: choose goal, define style, generate character kit.
- Example Style DNA cards.
- Example Character Kit cards.
- Prompt support for Midjourney, Nano Banana, Imagen, and Flux.
- Lightweight pricing or email waitlist CTA.

### Style DNA Page

Route:

`/style-dna`

Purpose:
Help users convert their taste into a reusable visual system.

Input steps:

- Creative goal: avatar, IP persona, comic lead, Xiaohongshu visual identity, short-video character, profile image series.
- Mood direction: warm, mysterious, cute, dark, elegant, retro, dreamy, futuristic, calm, rebellious.
- Audience: personal expression, fans/community, clients, niche subculture, public-facing creator brand.
- Visual preference: cinematic, illustrated, anime-inspired, 3D, editorial, hand-drawn, soft fantasy, retro-futurist.
- Color preference: soft pastel, high contrast, muted earth, neon night, monochrome accent, bright candy, ink wash, luxury dark.
- Line and texture: clean vector, painterly brush, pencil sketch, clay, paper cut, film grain, glossy 3D, watercolor.
- Character proportion: realistic, semi-realistic, chibi, tall elegant, stylized anime, toy-like, mascot-like.
- Avoid list: overly generic, IP-like, artist-name-dependent, logo text, overcomplicated costume, low consistency.

Output fields:

- Style name.
- One-sentence style description.
- Style personality.
- Visual keywords.
- Color palette.
- Line and texture rules.
- Lighting and composition rules.
- Character proportion rules.
- Good use cases.
- Avoided directions.
- Midjourney prompt skeleton.
- Nano Banana prompt skeleton.
- Imagen prompt skeleton.
- Flux prompt skeleton.
- Negative prompt.

### Character Kit Page

Route:

`/character-kit`

Purpose:
Generate an original character design package from a user brief and selected Style DNA.

Input fields:

- Character role: creator avatar, mascot, comic lead, fantasy character, daily-life persona, short-video host.
- Character personality: gentle, sharp, chaotic, elegant, lonely, playful, brave, shy, mysterious, healing.
- World context: modern city, fantasy town, cyber street, cozy studio, campus, traveling diary, magical realism.
- Signature symbol: accessory, color, object, hairstyle, clothing detail, small prop, pattern, visual motif.
- Output model: Midjourney, Nano Banana, Imagen, Flux, all models.
- Optional reference Style DNA.

Output fields:

- Character name.
- Character tagline.
- Personality summary.
- Backstory.
- Visual identity.
- Face and hairstyle.
- Outfit design.
- Color palette.
- Signature symbols.
- Expressions.
- Poses.
- Scene ideas.
- Character consistency rules.
- Midjourney prompt.
- Nano Banana prompt.
- Imagen prompt.
- Flux prompt.
- Negative prompt.

### Style Library

Route:

`/styles`

Purpose:
Inspiration only. The page helps users choose directions for Style DNA, not merely copy prompts.

Card fields:

- Preview image.
- Style name.
- Mood tags.
- Use case tags.
- Visual DNA tags.
- "Use in Style DNA" action.
- "Create Character from this style" action.

### Moodboard

Route:

`/moodboard`

Purpose:
Save user-created style systems, character kits, prompt history, and inspiration styles.

MVP scope:

- Saved Style DNA.
- Saved Character Kits.
- Saved inspiration styles.
- Copied prompt history.

Do not build complex team asset management in v0.1.

## 6. First Content Set

The first public content batch should support creator identity and original character use cases.

Recommended first 30 inspiration directions:

- Cozy diary avatar.
- Neon lonely creator.
- Soft fantasy self-portrait.
- Retro comic host.
- Cute mascot creator.
- Dark elegant storyteller.
- Dreamy watercolor persona.
- Urban film portrait.
- Pastel toy-like character.
- Ink-wash fantasy avatar.
- Futuristic personal brand.
- Hand-drawn notebook character.
- Magical girl creator persona.
- Minimal editorial avatar.
- Clay-like social mascot.
- Y2K pop character.
- Gentle healing illustrator.
- Cyber street narrator.
- Vintage film blogger.
- Tiny explorer mascot.
- Elegant black-and-white persona.
- Warm cafe creator.
- Starry night fantasy lead.
- Soft Japanese fantasy-inspired character.
- Retro-futurist host.
- Paper-cut story character.
- Bright candy mascot.
- Quiet scholar avatar.
- Music cover persona.
- Daily comic self-insert.

Each inspiration direction should include:

- Style name.
- Style purpose.
- 4 visual examples.
- Style DNA tags.
- Character use-case suggestion.
- Midjourney prompt.
- Nano Banana prompt.
- Imagen prompt.
- Flux prompt.
- Negative prompt.

## 7. MVP Feature Priority

P0:

- Home page.
- Style DNA diagnostic flow.
- Character Kit generator flow.
- Result page for Style DNA.
- Result page for Character Kit.
- Copy prompt.
- Save result locally or to account.
- Basic style inspiration library.
- Admin-friendly content format.

P1:

- Login.
- Cloud moodboard.
- Prompt history.
- Export prompt pack.
- Free usage limits.
- Paid tier.

P2:

- Image generation.
- Character consistency image workflow.
- Batch character variations.
- Team spaces.
- 3D asset reference workflow.

## 8. Lightweight Technical Direction

For the first implementation, keep the architecture simple:

- Frontend: Next.js + Tailwind CSS.
- Auth and database: Supabase.
- Payments later: Stripe.
- Content storage: Supabase Storage or Cloudflare R2.
- AI prompt generation: start with deterministic templates, then add LLM rewriting.
- Deployment: Vercel.

The first usable version can work without live image generation. The main product value is structured personalization and multi-model prompt generation.

## 9. Seven-Day Execution Plan

Day 1:
Finalize product name, positioning, homepage headline, and the exact first user flow.

Day 2:
Define Style DNA input fields, output fields, and scoring/mapping rules.

Day 3:
Define Character Kit input fields, output fields, and prompt templates.

Day 4:
Create 10 complete Style DNA examples and 10 Character Kit examples.

Day 5:
Create homepage wireframe, Style DNA wireframe, and Character Kit wireframe.

Day 6:
Prepare the first 30 inspiration directions and their content template.

Day 7:
Review all sample outputs, remove generic wording, and prepare development backlog.

## 10. Success Criteria

The first version is successful if users can:

- Understand the product within five seconds.
- Generate a Style DNA that feels more personal than generic prompt lists.
- Generate a Character Kit with enough specificity to guide repeated image creation.
- Copy prompts for at least four models.
- Save or reuse their style and character direction.

Early metrics:

- Style DNA completion rate.
- Character Kit completion rate.
- Prompt copy rate.
- Result save rate.
- Share rate of generated Style DNA or Character Kit.

## 11. Open Decisions

These decisions can wait until after the first design review:

- Whether the first public site uses English first, Chinese first, or bilingual UI.
- Whether account login is required for saving in the MVP.
- Whether AI text generation is included in v0.1 or prompt templates are used first.
- Whether the first launch is a free tool, waitlist, or paid beta.
