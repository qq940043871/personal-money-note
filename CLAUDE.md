# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static HTML prototype for an **投资交易系统** (Investment Trading System) — a Chinese-language financial education and trading management portal. It is a pure frontend prototype with no backend, no build tools, and no package manager.

## Architecture

**Shell model**: `index.html` is the main shell containing:
- Top header bar (`h-16`) with system title and user info
- Left sidebar (`w-64`) with grouped navigation links
- Main content area with `<iframe id="mainFrame">` that loads sub-pages

**Navigation**: Sidebar links call `loadPage('module/page.html')` which sets the iframe `src` and toggles the `.active-nav` class. Sub-pages that need to navigate to other pages call `parent.loadPage('module/page.html')`. All paths are relative to the project root.

**Module structure**: Pages are organized into functional modules:

```
index.html              # Shell with sidebar + iframe
portal/                 # 首页门户 — home, portal
trading/                # 交易系统 — stock_navigation, trading_system, strategies, stock_analysis, etc.
│   retail_mistakes/    # 散户误区子模块
learning/               # 学习系统 — learning_system, learning, biography, etc.
market/                 # 市场信息 — market, read_news, market_essence, etc.
policy/                 # 国家政策 — meetings, fed, policy, government_finance, etc.
industry/               # 行业追踪 — industry_tracking, industrial_software, etc.
system/                 # 系统设置 — settings
```

Each `.html` file has a paired `.md` documentation file with the same name.

## Tech Stack (All CDN, Zero Build Tools)

| Library | CDN | Required |
|---------|-----|----------|
| Tailwind CSS | `https://cdn.tailwindcss.com` | Always |
| Font Awesome 6.4 | `https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css` | Always |
| Chart.js 3.9.1 | `https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.9.1/chart.min.js` | Only for charts |

No `package.json`, no bundler, no npm. Open `index.html` directly in a browser to run.

## Conventions

- **Language**: Always `lang="zh-CN"`, all UI text in Chinese
- **Tailwind config**: Every page includes the same inline config block with `primary: '#3B82F6'`, `secondary: '#64748B'`, `accent: '#10B981'`, `warning: '#F59E0B'`, `danger: '#EF4444'`
- **Static data**: All data is hardcoded in HTML. No API calls, no external data files.
- **Page boilerplate**: Every sub-page starts with the standard HTML head (meta, Tailwind CDN, Font Awesome CDN, Tailwind config) and ends with a `<script>` block. See any existing page for the template.
- **Sub-page navigation**: Use `parent.loadPage('module/page.html')` in onclick handlers to navigate from within the iframe. Paths are relative to project root, not the current file.
- **File naming**: Lowercase with underscores for multi-word names
- **Paired docs**: Every `.html` page has a same-named `.md` file describing requirements and structure

## Page Patterns

Common UI patterns used across pages:

- **Stats cards**: `grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6` with icon circle + label + number
- **Two-column layouts**: `grid grid-cols-1 lg:grid-cols-2 gap-6` for side-by-side content panels
- **Content panels**: `bg-white rounded-lg shadow` with `px-6 py-4 border-b` header and `p-6` body
- **Left-bordered items**: `border-l-4 border-blue-500 pl-4 py-1` for list entries with colored accents
- **Status badges**: `px-2 inline-flex text-xs leading-5 font-semibold rounded-full` with color variants

## Adding a New Page

1. Create the `.html` file in the appropriate module directory using the page boilerplate
2. Create a paired `.md` documentation file with the same base name
3. Add a navigation entry in `index.html` sidebar with `onclick="loadPage('module/new-page.html')"`
4. For inter-page navigation within iframes, use `parent.loadPage('module/page.html')`

## Key Files

- `index.html` — Main shell (sidebar + iframe)
- `portal/home.html` — Default landing page loaded in iframe
- `.claude/skills/html-prototype/SKILL.md` — Claude Code skill with detailed patterns for generating new pages
- `01-init/提示词.md` — Original requirements document
