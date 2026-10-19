<div align="center">

# Landing Pages with Skills

*Same brief, same prompt, two builds: what a single Claude Code skill changes about design quality.*

[![HTML5](https://img.shields.io/badge/HTML5-single_file-e34f26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-custom_properties-1572b6?style=flat-square&logo=css3&logoColor=white)](https://developer.mozilla.org/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-vanilla-f7df1e?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/docs/Web/JavaScript)
[![Built with Claude Code](https://img.shields.io/badge/Built_with-Claude_Code-d97757?style=flat-square&logo=anthropic&logoColor=white)](https://claude.com/claude-code)
[![Skill: frontend-design](https://img.shields.io/badge/Skill-frontend--design-6b4f3f?style=flat-square)](https://github.com/anthropics/claude-code/tree/main/plugins/frontend-design)

[Overview](#overview) • [Before and after](#before-and-after) • [What the skill changed](#what-the-skill-changed) • [Projects](#projects) • [Run it](#run-it) • [How I built this](#how-i-built-this)

</div>

## Overview

This repo is an experiment in **Claude Code skills**. I gave Claude Code the same brief twice:
a landing page for *Sugar & Bloom*, a boutique bakery. The first build ran with no skill. The
second ran with Anthropic's [`frontend-design`](https://github.com/anthropics/claude-code/tree/main/plugins/frontend-design)
skill installed.

The prompt didn't change between builds. Both pages share the same section structure:

- a hero with the bakery name and tagline
- a one-question-at-a-time quiz (occasion → flavor → budget) that recommends a cake
- a six-cake menu
- three testimonials
- an order form

Each page is a single self-contained `.html` file, written in HTML, CSS and vanilla JavaScript
with no frameworks or build step.

## Before and after

| Without the skill | With `frontend-design` |
| --- | --- |
| ![Sugar & Bloom without the skill: pastel pink-and-cream gradient hero with Playfair Display heading, tracked-out all-caps pill label and two rounded pill buttons](docs/screenshots/bakery-no-skill-hero.png) | ![Sugar & Bloom with the skill: full-bleed photo of a layered sprinkle cake on a dark plum overlay, Fraunces serif heading and a berry call-to-action](docs/screenshots/bakery-with-skill-hero.png) |
| ![Quiz result without the skill: centered white card with a chocolate emoji, "YOUR MATCH" label and pill buttons](docs/screenshots/bakery-no-skill-quiz.png) | ![Quiz result with the skill: cake photo beside an occasion-specific line, cake name, starting price with serving size, and an "Add to my order" button](docs/screenshots/bakery-with-skill-quiz.png) |
| Pleasant, but recognisably the default: soft gradient, emoji, centered everything, uppercase eyebrow labels. | Real photography, a specific palette, asymmetric shapes, and copy that sounds like a bakery wrote it. |

<details>
<summary><strong>Full-page comparison</strong></summary>

| Without the skill | With `frontend-design` |
| --- | --- |
| ![Full page of the no-skill build](docs/screenshots/bakery-no-skill-full.png) | ![Full page of the with-skill build](docs/screenshots/bakery-with-skill-full.png) |

</details>

### Mobile (with skill)

<img src="docs/screenshots/bakery-with-skill-mobile.png" width="300" alt="Sugar & Bloom with-skill build on a 390px phone screen with a hamburger menu and stacked buttons">

The with-skill build at phone width, with no horizontal scroll.

## What the skill changed

| | Without the skill | With `frontend-design` |
| --- | --- | --- |
| **Type** | Playfair Display + Poppins | Fraunces (variable optical size, italics for accents) + Work Sans |
| **Palette** | Blush, rose, cream, gold | Ivory, espresso, berry, sage, butter, held as named CSS tokens |
| **Hero** | Gradient with decorative flower shapes | Full-bleed cake photograph with a tinted overlay |
| **Quiz result** | Emoji, generic "Your match" | Cake photo, occasion-specific line, price with size and servings |
| **Labels and CTAs** | Tracked-out all-caps eyebrows, pill buttons | Italic serif kickers, one distinctive asymmetric button shape |
| **Copy** | "Find Your Perfect Cake", "What Our Customers Say" | "Not sure what to order?", "Six cakes, always made to order" |
| **Sections** | Uniform rounded cards throughout | Each section has its own background tint; the order form sits on espresso |

The skill doesn't add features. Both pages do the same things. What it changes is the design
decisions. It pushes for a direction specific to the brief and calls out common "AI-looking"
defaults to avoid.

## Projects

| Page | Folder | Built with |
| --- | --- | --- |
| Sugar & Bloom (no skill) | [`Build a business frontpage - no skills/`](Build%20a%20business%20frontpage%20-%20no%20skills/sugar_and_bloom.html) | Claude Code, no skills |
| Sugar & Bloom v2 | [`Build a business frontpage -with skills/`](Build%20a%20business%20frontpage%20-with%20skills/sugar_and_bloom_v2.html) | Claude Code + `frontend-design` |

## Run it

No install or build step is needed. Clone the repo and open any `.html` file in a browser.

```bash
git clone https://github.com/safia-raja/landing-pages-with-skills.git
```

> [!NOTE]
> Fonts load from Google Fonts and the v2 photos from Unsplash, so you need an internet
> connection for the pages to look as shown.

### Reproduce the experiment

1. Ask Claude Code for the bakery page with a structured prompt (see below).
2. Install the skill into the project:

   ```bash
   npx skills add anthropics/claude-code --skill frontend-design
   ```

   This puts the skill in `.claude/skills/` (for Claude Code) and `.agents/skills/` (for other
   agent runtimes). I left those folders out of the repo, so reinstall the skill with this
   command.
3. Run the same prompt again with the skill active and compare the two files side by side.

## How I built this

I didn't write the code by hand. Both pages were generated by
**[Claude Code](https://claude.com/claude-code)**. My role was the experiment itself:

- **Prompt design**: I wrote each brief in a Context / Instruction / Input / Output format so
  that the only variable between the two bakery builds was the skill
- **Controlled comparison**: I kept the business, tagline, quiz questions, menu size and form
  fields identical across both builds
- **Skill setup**: I installed `frontend-design` from Anthropic's repo before the second build
- **Review**: I opened the builds side by side and compared typography, color, layout and copy

## Credits

- Cake photography in v2 via [Unsplash](https://unsplash.com)
- [`frontend-design`](https://github.com/anthropics/claude-code/tree/main/plugins/frontend-design)
  skill by Anthropic
- Built as part of a Claude Code course project
