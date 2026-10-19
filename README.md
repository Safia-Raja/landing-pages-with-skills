<div align="center">

# Landing Pages with Skills

*Same bakery brief, two builds: what a single Claude Code skill changes about design quality.*

[![HTML5](https://img.shields.io/badge/HTML5-single_file-e34f26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-custom_properties-1572b6?style=flat-square&logo=css3&logoColor=white)](https://developer.mozilla.org/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-vanilla-f7df1e?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/docs/Web/JavaScript)
[![Built with Claude Code](https://img.shields.io/badge/Built_with-Claude_Code-d97757?style=flat-square&logo=anthropic&logoColor=white)](https://claude.com/claude-code)
[![Skill: frontend-design](https://img.shields.io/badge/Skill-frontend--design-6b4f3f?style=flat-square)](https://github.com/anthropics/claude-code/tree/main/plugins/frontend-design)

[Overview](#overview) • [Before and after](#before-and-after) • [What the skill changed](#what-the-skill-changed) • [The prompts](#the-prompts) • [Projects](#projects) • [Run it](#run-it) • [How I built this](#how-i-built-this)

</div>

## Overview

This repo is an experiment in **Claude Code skills**. I gave Claude Code the same brief twice:
a landing page for *Sugar & Bloom*, a boutique bakery. The first build ran with no skill. The
second ran with Anthropic's [`frontend-design`](https://github.com/anthropics/claude-code/tree/main/plugins/frontend-design)
skill installed.

Both prompts ask for the same page with the same sections:

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

> [!NOTE]
> The skill wasn't the only thing that changed. The second prompt is also more detailed: it asks
> for a "premium and distinctive" design, Unsplash photos and a Typeform-style quiz. Some of the
> difference comes from that, so read this as "skill plus a sharper brief" rather than a strict
> one-variable test.

## The prompts

Both prompts come from Prof. Ryan Ahmed's Claude masterclass on Udemy (Module 6, Claude Code
Foundations). Each follows a Context / Instruction / Input / Output structure.

<details>
<summary><strong>Prompt 1: build without the skill</strong></summary>

```text
Context: I run a boutique bakery called "Sugar & Bloom." I need a website page I can open in my browser to show customers what we offer and help them pick the right cake.
 
Instruction: Create a single file called "sugar_and_bloom.html" with everything a customer would need — a big beautiful intro with our name and tagline, a short interactive quiz that helps them find the right cake, our menu, some customer reviews, and a way to contact us and place an order. The quiz should feel smooth — one question at a time, not a long form.
 
Implement it without using any skills.
 
Input:
- Business name: Sugar & Bloom
- Tagline: "Handcrafted cakes for life's sweetest moments"
- Quiz questions: What's the occasion? (Birthday, Wedding, Anniversary, Just Because) → What flavor? (Chocolate, Vanilla, Red Velvet, Lemon, Surprise Me) → Budget? (Under $50, $50–$100, $100–$200, $200+) → then recommend a cake
- Menu: 6 cakes with names, descriptions, and prices
- Reviews: 3 happy customer quotes
- Contact form: name, email, phone, date needed, message
 
Output: A single file I can open in any browser — everything should work, the quiz should flow nicely, and it should look good enough to show a customer.
```

</details>

<details>
<summary><strong>Prompt 2: rebuild with the skill</strong></summary>

```text
Context: I have the frontend-design skill installed. I want to rebuild my bakery landing page from scratch with a professional, distinctive design — not generic AI-looking output.

Instruction: Create a single HTML file called "sugar_and_bloom_v2.html" for a boutique bakery called "Sugar & Bloom". The page should include:
1. A beautiful hero section with the bakery name, tagline ("Handcrafted cakes for life's sweetest moments"), and a background image placeholder
2. A Typeform-style interactive quiz that asks customers 3 questions one at a time with smooth transitions:
   - "What's the occasion?" (Birthday, Wedding, Anniversary, Just Because)
   - "What's your flavor preference?" (Chocolate, Vanilla, Red Velvet, Lemon, Surprise Me)
   - "What's your budget?" (Under $50, $50–$100, $100–$200, $200+)
   Then shows a personalized cake recommendation based on their answers
3. A menu section with 6 cakes, each with a name, description, price, and image placeholder
4. A testimonials section with 3 customer reviews
5. A contact/order form with name, email, phone, date needed, and a message field

Make it fully functional — the quiz should actually work, transitions should be smooth, and the design should feel premium and distinctive. Use only HTML, CSS, and vanilla JavaScript in one file.

Input:
- File name: sugar_and_bloom_v2.html
- Business: Sugar & Bloom Bakery
- Tagline: "Handcrafted cakes for life's sweetest moments"
- For images use placeholder images from unsplash

Output: A single self-contained HTML file with a polished, professional design that looks like it was built by a designer — not generated by AI.
```

</details>

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

1. Run [Prompt 1](#the-prompts) in Claude Code.
2. Install the skill into the project:

   ```bash
   npx skills add anthropics/claude-code --skill frontend-design
   ```

   This puts the skill in `.claude/skills/` (for Claude Code) and `.agents/skills/` (for other
   agent runtimes). I left those folders out of the repo, so reinstall the skill with this
   command.
3. Run [Prompt 2](#the-prompts) with the skill active and compare the two files side by side.

## How I built this

I didn't write the code by hand. Both pages were generated by
**[Claude Code](https://claude.com/claude-code)**. My role was the experiment itself:

- **Prompts**: I ran the two course prompts above, which use a Context / Instruction / Input /
  Output format
- **Controlled comparison**: I kept the business, tagline, quiz questions, menu size and form
  fields identical across both builds
- **Skill setup**: I installed `frontend-design` from Anthropic's repo before the second build
- **Review**: I opened the builds side by side and compared typography, color, layout and copy
- **Design direction on v2**: I tested the quiz end to end, checked that every photo matched
  the cake it sits next to, and came up with the hero idea: a full-bleed cake photo under a
  gradient overlay

## Credits

- Cake photography in v2 via [Unsplash](https://unsplash.com)
- [`frontend-design`](https://github.com/anthropics/claude-code/tree/main/plugins/frontend-design)
  skill by Anthropic
- Prompts and project idea from Prof. Ryan Ahmed, PhD, MBA, in his Claude masterclass on Udemy
