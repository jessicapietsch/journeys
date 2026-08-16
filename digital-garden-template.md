# Digital Garden Template (Modern Botanical Theme)

This is a complete, ready-to-use template set to build your plain-text, non-linear **Digital Garden** on GitHub Pages using native Jekyll parsing. It features the **Modern Botanical** style, featuring high readability, soft paper-like tones, and lush green accents [57, 63].

To launch your garden, simply upload these files to your GitHub repository maintaining the exact folder structure described below [57, 66].

---

## Folder Structure Overview

Your GitHub repository should look like this [62, 65]:

```text
├── _config.yml               <-- Repository configuration
├── _layouts/
│   └── default.html          <-- Page layout wrapper
├── assets/
│   └── css/
│       └── style.css         <-- Modern Botanical styling
├── index.md                  <-- Your garden's homepage/README
└── templates/
    └── note-template.md      <-- Front matter and tags for new entries
```

---

## 1. The Configuration File (`_config.yml`)
Place this at the root of your repository. This file configures your site and automatically applies the default botanical layout wrapper to every Markdown note you create, eliminating the need to write the layout metadata manually [59, 66].

```yaml
# _config.yml
title: "My Digital Garden"
description: "A non-linear, personal space to grow thoughts, notes, and milestones."
url: "" # Leave blank for GitHub Pages to auto-fill

# Automatically apply the custom default layout to all Markdown files
defaults:
  - scope:
      path: "" # Applies to all files in the repository
    values:
      layout: "default"

# Exclude system and draft files from rendering
exclude:
  - Gemfile
  - Gemfile.lock
  - node_modules/
  - vendor/
```

---

## 2. The Layout Wrapper (`_layouts/default.html`)
Create a folder named `_layouts` in your repository root, and place this file inside it as `default.html`. It serves as the shell that wraps all your markdown entries, pulling in the Botanical CSS automatically [64, 67].

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ page.title | default: site.title }}</title>
    <!-- Relative URL filter ensures links work on both root domains and sub-folders -->
    <link rel="stylesheet" href="{{ '/assets/css/style.css' | relative_url }}">
</head>
<body>
    <header class="garden-header">
        <div class="header-container">
            <a href="{{ '/' | relative_url }}" class="garden-brand">{{ site.title }}</a>
            <nav class="garden-navigation">
                <a href="{{ '/' | relative_url }}">Garden Gate (Home)</a>
                <a href="{{ '/about' | relative_url }}">About</a>
            </nav>
        </div>
    </header>

    <main class="garden-main">
        <article class="garden-note">
            {% if page.title %}
            <h1 class="note-heading">{{ page.title }}</h1>
            {% endif %}
            
            {{ content }}
        </article>
    </main>

    <footer class="garden-footer">
        <p>© {{ site.time | date: "%Y" }} — Grown with care. Grounded in Life Events.</p>
    </footer>
</body>
</html>
```

---

## 3. The Botanical Stylesheet (`assets/css/style.css`)
Create a folder named `assets`, inside it a folder named `css`, and save this stylesheet as `style.css`. It implements the "Modern Botanical" aesthetic, focusing on readable typography, a soft "paper-like" background, and forest green accents [63, 64].

```css
/* Modern Botanical Theme - style.css */
:root {
    --bg-color: #fcfbf9;         /* Soft paper-like background */
    --text-color: #2b2e2a;       /* Off-black for reduced eye strain */
    --accent-color: #1e3f20;     /* Lush forest green for major titles */
    --accent-mid: #355e3b;       /* Mid-tone green for sub-headers and borders */
    --accent-light: #eff4ef;     /* Soft green background for highlights */
    --link-color: #3b6e41;       /* Sage green for links */
    --link-hover: #1b381e;       /* Deep pine green for hovered links */
    --border-color: #e3e8e1;     /* Delicate border tone */
    --code-bg: #f4f6f3;          /* Soft background for checkboxes and tags */
}

body {
    background-color: var(--bg-color);
    color: var(--text-color);
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji";
    line-height: 1.6;
    margin: 0;
    padding: 0;
}

.garden-header {
    border-bottom: 1px solid var(--border-color);
    padding: 1.5rem 0;
}

.header-container {
    max-width: 800px;
    margin: 0 auto;
    padding: 0 1.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.garden-brand {
    font-size: 1.5rem;
    font-weight: 700;
    color: var(--accent-color);
    text-decoration: none;
    letter-spacing: -0.025em;
}

.garden-navigation a {
    margin-left: 1.5rem;
    color: var(--text-color);
    text-decoration: none;
    font-weight: 500;
    transition: color 0.2s ease;
}

.garden-navigation a:hover {
    color: var(--link-color);
}

.garden-main {
    max-width: 800px;
    margin: 3.5rem auto;
    padding: 0 1.5rem;
}

.note-heading {
    font-size: 2.25rem;
    color: var(--accent-color);
    margin-bottom: 2rem;
    line-height: 1.25;
    letter-spacing: -0.02em;
}

h2, h3, h4 {
    color: var(--accent-color);
    margin-top: 2rem;
}

h2 {
    font-size: 1.6rem;
    border-bottom: 1px solid var(--border-color);
    padding-bottom: 0.5rem;
}

a {
    color: var(--link-color);
    text-decoration: none;
    border-bottom: 1px dashed var(--link-color);
    transition: all 0.2s ease;
}

a:hover {
    color: var(--link-hover);
    border-bottom-style: solid;
}

p {
    margin-bottom: 1.5rem;
}

ul, ol {
    padding-left: 1.5rem;
    margin-bottom: 1.5rem;
}

li {
    margin-bottom: 0.5rem;
}

/* Bullet list optimization */
ul li::marker {
    color: var(--link-color);
}

/* Checkbox alignment for task lists */
input[type="checkbox"] {
    accent-color: var(--accent-mid);
    margin-right: 0.5rem;
    cursor: pointer;
}

pre, code {
    background-color: var(--code-bg);
    border-radius: 6px;
    font-family: ui-monospace, SFMono-Regular, SF Pro Icons, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;
    font-size: 0.9rem;
}

pre {
    padding: 1.25rem;
    overflow-x: auto;
    border: 1px solid var(--border-color);
}

code {
    padding: 0.2rem 0.4rem;
}

/* Tag Container Styling */
.tag-dictionary {
    background-color: var(--accent-light);
    border-left: 4px solid var(--accent-mid);
    padding: 1rem 1.25rem;
    border-radius: 0 8px 8px 0;
    margin-top: 3rem;
}

.tag-dictionary p {
    margin: 0;
    font-size: 0.95rem;
    color: var(--accent-color);
}

.garden-footer {
    max-width: 800px;
    margin: 6rem auto 3rem;
    padding: 1.5rem 1.5rem 0;
    border-top: 1px solid var(--border-color);
    text-align: center;
    font-size: 0.85rem;
    color: #7b8079;
}
```

---

## 4. Your Homepage (`index.md`)
Save this as `index.md` (or rename your `README.md` to `index.md`) in the root of your repository. This serves as your homepage and provides standard internal wiki links to other pages, such as an "About" page or specific notes [59, 60, 61].

```markdown
---
title: "The Garden Gate"
---

Welcome to my **Digital Garden**, a non-linear personal space designed to grow, evolve, and interlink thoughts, personal milestones, and life transitions over time [57]. Unlike a blog, this garden is a living web of interconnected notes [57].

## Active Pathways

*   **[Managing a New Medication](notes/medication-routine)** — Transitioning a new medical script into a seamless background habit using plain text checklists.
*   **[Identity & Unmasking](notes/unmasking-journey)** — Documenting sensory-friendly environmental setups and navigating burnout recovery.
*   **[About This Garden](about)** — My methodology behind using open-source, plain-text plain language structures.

## Planting Status

*   **Current Focus:** Building a carbon-conscious living planner [168].
*   **Last Pruned:** August 2026.

<div class="tag-dictionary">
    <p>💡 <strong>Note:</strong> To link pages together, use simple relative links: <code>[Link Text](path-to-file)</code> without the <code>.html</code> or <code>.md</code> extension [61].</p>
</div>
```

---

## 5. Reusable Note Template (`templates/note-template.md`)
Create a folder named `templates`, and save this note format as `note-template.md`. This is a blank, plain-text structure optimized for both human reading and machine-readability (by an LLM), featuring the correct accessible tagging rules at the base [61, 148].

```markdown
---
title: "Insert Specific Milestone Name"
---

# Insert Milestone / Event Name
*   **Date of Event:** YYYY-MM-DD
*   **Location:** [Specific venue or home]
*   **Life Event Journey:** [e.g., Managing a New Medication, Relocating]

## 1. Lead-Up (Context & Triggers)
*   *What occurred before this event? (e.g., burnout warning signs, doctor's script)*

## 2. Main Experience (Stages & Cycles)
*   `- [ ]` Daily Task (written in plain language beginning with an action verb)
*   `- [ ]` Completed Task (check when finished to help an LLM parse status)

## 3. How I Felt (Interoceptive & Bodily Cues)
*   *What sensory, physical, or emotional responses did I observe?*

## 4. What Helped or Hurt (Pain Points & Support)
*   **Hurt (Pain Point):** *e.g., Executive function exhaustion, unexpected fees at counter*
*   **Helped (Workaround):** *e.g., Setting automated daily routines, utilizing parallel play*

## 5. Reflections or Meaning
*   *What did I understand or realize during this event?*

---
`#LifeEventsFramework` `#Stage-Action` `#Task-BuildRoutines` `#ExecutiveSupport`
```
