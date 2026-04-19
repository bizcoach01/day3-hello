# Personal Portfolio Static Website — Design Spec

## Overview

A single-page scrolling personal portfolio website with a warm, friendly design. Built with plain HTML and Tailwind CSS (CDN), no build tools required.

## Architecture

- **Single file**: `index.html` with all content
- **Styling**: Tailwind CSS via CDN (`<script src="https://cdn.tailwindcss.com">`)
- **No build step**: Open directly in browser or deploy to any static host
- **Language**: Korean (all text content)

## Color Palette

| Role        | Color     | Usage                         |
|-------------|-----------|-------------------------------|
| Page bg     | `#FFF8F0` | Default section background    |
| Alt bg      | `#FFFAF5` | Career section background     |
| Accent      | `#D4845A` | Buttons, highlights, nav name |
| Title text  | `#6B4226` | Headings                      |
| Body text   | `#8B7355` | Paragraphs, labels            |
| Border      | `#F5E6D3` | Dividers, input borders       |
| Tag bg      | `#FDEBD0` | Skill tags                    |
| Tag border  | `#F5CBA7` | Timeline line, tag accent     |

## Sections (top to bottom)

### 1. Fixed Navigation Bar
- Left: Name (bold, accent color)
- Right: Section links (소개 / 경력 / 연락처)
- Click scrolls to corresponding section (smooth scroll)
- Warm beige background with bottom border
- Responsive: hamburger menu on mobile

### 2. Hero / Intro
- Centered layout, gradient background (`#FFF8F0` → `#FDEBD0`)
- Circular profile image placeholder (80px, warm orange)
- Name heading (h2, title color, 28px)
- One-line introduction (body color, 16px)
- Padding: generous vertical spacing (60px top, 40px bottom)

### 3. Career / Experience
- Section heading centered
- Timeline layout: left border line with career entries
- Each entry: date range (accent, small), title (bold, title color), description (body color)
- Background slightly different from hero (`#FFFAF5`)
- Skill tags: pill-shaped badges in warm tones below timeline

### 4. Contact
- Section heading centered
- Form with three fields: name, email, message
- Submit button (accent bg, white text, rounded)
- Form action: Formspree endpoint (`https://formspree.io/f/<id>`)
- Placeholder: `YOUR_FORMSPREE_ID` in action URL for user to replace

### 5. Footer
- Centered copyright text
- Warm beige background (`#F5E6D3`)

## Responsive Behavior

- Desktop: full layout as described
- Mobile (Tailwind `md` breakpoint):
  - Navigation collapses to hamburger menu
  - Content padding reduces
  - Font sizes scale down appropriately

## Interactions

- Smooth scrolling via CSS `scroll-behavior: smooth` and Tailwind config
- Navigation highlights active section (optional enhancement)
- Form validation: HTML5 built-in (`required` attributes)

## File Structure

```
index.html          — Complete single-page site
```

## Deployment

- Any static host: GitHub Pages, Netlify, Vercel, or direct file serving
- No build or compilation step needed
