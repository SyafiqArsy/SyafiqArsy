# GitHub Profile Portfolio — Implementation Plan

## Goal
Transform the default profile README into a professional, modern dark developer portfolio with automated contribution graph, structured tech stack, featured projects, and subtle animations — all using real GitHub data.

---

## Repository Structure

```
SyafiqArsy/
├── README.md                          # Profile README (main landing page)
├── assets/
│   ├── header.svg                     # Hero banner SVG (dark, branded)
│   ├── typing.svg                     # Typing animation (readme-typing-svg)
│   └── contribution-snake-dark.svg    # Snake contribution graph (auto-generated)
├── .github/
│   └── workflows/
│       └── snake.yml                  # GitHub Actions: generate contribution snake
```

---

## Phase 1: Assets & Workflow Setup

### 1a. Contribution Snake Workflow (`.github/workflows/snake.yml`)
- Use **[Platane/snk](https://github.com/Platane/snk)** — battle-tested, outputs SVG+GIF, supports dark theme
- Runs on schedule (every 6 hours) + on push to main
- Generates both outputs into `assets/`:
  - `contribution-snake-dark.svg` — animated snake through contribution grid
  - `contribution-grid-dark.svg` — static styled contribution calendar
- Auto-commits updated SVGs back to repo
- No tokens needed beyond default `GITHUB_TOKEN`

### 1b. Hero Header SVG (`assets/header.svg`)
- Custom SVG with dark background (`#0d1117` GitHub dark)
- Name "SyafiqArsy" in modern monospace font
- Subtitle line: "Full-Stack Developer | Backend Developer"
- Subtle accent color (cyan/teal `#58a6ff` or `#7ee787`)
- Clean, minimal, no clutter

---

## Phase 2: Profile README.md

### Section Layout (top to bottom):

#### 1. Hero / Header
- `<img>` tag pointing to `assets/header.svg`
- Animated typing text via **[readme-typing-svg](https://github.com/DenverCoder1/readme-typing-svg)** (self-hosted or service):
  - "Building Scalable Web Applications"
  - "Designing RESTful APIs"
  - "Exploring Cloud Computing"
  - "Turning Ideas Into Digital Products"
- Speed: subtle, ~50ms per char, pause between lines

#### 2. About / Terminal Section
- Terminal-style block using code block or SVG:
  - `$ whoami` → Syafiq
  - `$ role` → Full-Stack & Backend Developer
  - `$ currently_building` → Seventh Sky Store, Seventh Sky Style
  - `$ status` → ACTIVE
- Brief paragraph: Informatics Engineering student, full-stack web apps, backend services, RESTful APIs, database systems, deployment

#### 3. Tech Stack (by category)
Using **shields.io** badges or **skill-icons** (GitHub `tandpfun/skill-icons`):
- **Backend**: Laravel, NestJS, FastAPI
- **Frontend**: Next.js, React, Vue.js, Tailwind CSS
- **Database**: PostgreSQL, MySQL, Prisma
- **Cloud & Deployment**: AWS, Vercel
- **Tools**: Git, GitHub, Postman

Only real technologies, no badge spam.

#### 4. Featured Projects
Three cards (using markdown table or HTML `<table>`):

| Project | Description | Tech | Links |
|---------|-------------|------|-------|
| **Seventh Sky Store** | Full-stack fashion e-commerce platform | Laravel, React, MySQL | [Repo](https://github.com/SyafiqArsy/sevenths-sky-store) |
| **Seventh Sky Style** | AI-powered fashion stylist & outfit recommendation | Next.js, FastAPI, PostgreSQL | [Repo](https://github.com/SyafiqArsy/seventh-sky-style) |
| **Portfolio Website** | Personal developer portfolio website | Next.js, Tailwind CSS | [Repo](https://github.com/SyafiqArsy/syafiqarsy-portofolio) |

Each with 1-2 line description, key features, architecture note.

#### 5. GitHub Activity & Contribution Graph
- Contribution snake animation: `<img src="./assets/contribution-snake-dark.svg" />`
- Static contribution grid as fallback: `<img src="./assets/contribution-grid-dark.svg" />`
- Optional: GitHub stats card (using `github-readme-stats` or similar) — only if it adds value
- Language stats — kept minimal, one line

#### 6. Contact / Connect
- Minimal: GitHub profile link, LinkedIn, email (if desired)
- Simple icon links using shields.io

---

## Phase 3: Polish & Validation

- Verify all image paths resolve correctly
- Check SVG renders on GitHub (test by pushing to profile repo)
- Ensure no secrets, tokens, or credentials in any file
- Keep README under ~300 lines for fast scanning
- Test mobile rendering (GitHub mobile app)

---

## Key Design Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| Contribution graph | Platane/snk | Battle-tested, SVG+GIF output, dark theme support, auto-commit |
| Typing animation | readme-typing-svg | Lightweight SVG service, customizable, GitHub-compatible |
| Tech icons | shields.io badges | Consistent, fast-loading, widely recognized |
| Color scheme | GitHub dark (`#0d1117`, `#58a6ff` blue accent, `#7ee787` green) | Matches GitHub native dark mode, blue as primary accent |
| Animation | SVG-based only | No JS in README, all animations baked into SVG assets |
| Stats cards | Minimal or none | Projects > vanity metrics |

---

## Files to Create

1. **`README.md`** — Full profile README (~200-250 lines)
2. **`assets/header.svg`** — Custom hero banner SVG
3. **`.github/workflows/snake.yml`** — Contribution graph automation (generates both snake + grid SVGs)

---

## What We're NOT Doing
- No JavaScript in README
- No external service dependencies for core visuals (snake is self-generated)
- No fake contribution data
- No excessive badges or GIFs
- No secrets in repo
- No overly long README
