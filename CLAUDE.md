# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static HTML prototype for an **投资交易系统 / 投资交易工作站** (Investment Trading System) — a Chinese-language financial education and trading management portal. Pure frontend: no backend, no build tools, no package manager.

Open `index.html` in a browser, or run `start.bat` (`npx http-server -p 3004`).

## Architecture

**Shell model**: `index.html` is the main shell:
- Top bar (48px): page title, static market ticker, clock, user chip
- Left sidebar (`w-52`, dark gradient): 6 collapsible nav groups — 工作台 / 行情市场 / 交易体系 / 宏观政策 / 学习成长 / 系统
- Main area: `<iframe id="mainFrame">` loads sub-pages (default `portal/home.html`)
- Bottom status bar (28px)

**Navigation**:
- Shell: `loadPage(page, title, evt)` sets iframe `src`, updates `#pageTitle`, toggles `.active-nav`. With `evt` it highlights the clicked item; otherwise it matches the path string inside each `.nav-item`'s `onclick`. Collapsed groups auto-expand when their item becomes active.
- Sub-pages call `parent.loadPage('module/page.html')`. Paths are relative to the project root.

**Tab container pages**: Many module entries are thin containers (not content pages): a top tab bar + inner `<iframe id="tabFrame">`. Examples: `trading/system.html`, `trading/methods.html`, `market/cognition.html`, `policy/macro.html`, `learning/notes.html`, `industry/overview.html`. Tabs call `switchTab(btn, page)` with paths **relative to the container's directory**. Content lives in the child `.html` files those tabs load.

**Module structure**:

```
index.html                 # Shell + index.md
portal/                    # 首页门户 — home, portal
trading/                   # 交易体系
│  system.html             # Tab: trading_system, stock_navigation, investment_plan
│  methods.html            # Tab: strategies, volume_price, stock_cycle, market_resonance
│  manipulation.html       # Tab: mainipulation_process + ../learning/心理页
│  stock_analysis.html     # Standalone
│  retail_mistakes/        # 散户误区子模块 (index, overtrading)
learning/                  # 学习成长
│  notes.html              # Tab: learning_system, learning, scoring_system, learning_news, biography
market/                    # 行情市场
│  cognition.html          # Tab: market_essence, fundamental_logic, technology_imagination, china_future, first_mover_advantage
policy/                    # 宏观政策
│  meetings_policy.html    # Tab: meetings, policy
│  macro.html              # Tab: fed, government_finance, economic_development, global_economic_development, economic_conditions
│  rules.html              # Tab: financial_disclosure_rules, delisting_rules
industry/                  # 行业追踪
│  overview.html           # Tab: industry_tracking, industrial_software, industrial_software_chain
system/                    # 设置 — settings
```

**Paired docs**: Every `.html` (shell, tab container, and content page) has a same-named `.md` with: 页面概述 / 功能需求 / 页面结构 / 技术实现.

## Tech Stack (All CDN, Zero Build Tools)

| Library | CDN | Required |
|---------|-----|----------|
| Tailwind CSS | `https://cdn.tailwindcss.com` | Always |
| Font Awesome 6.4 | `https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css` | Always |
| Chart.js 3.9.1 | `https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.9.1/chart.min.js` | Only for charts |

No `package.json`, no bundler, no npm install step.

## Conventions

- **Language**: Always `lang="zh-CN"`, all UI text in Chinese
- **Shell palette**: `brand` indigo scale (`#6366F1` / `#4F46E5`), dark sidebar (`#0F172A`), surface `#F8FAFC`
- **Up/down (A-share)**: red up `#DC2626`, green down `#10B981` — opposite of US convention
- **Legacy content-page Tailwind config**: some older pages still use `primary: '#3B82F6'`, `secondary: '#64748B'`, `accent: '#10B981'`, `warning: '#F59E0B'`, `danger: '#EF4444'` — keep consistent within the page you edit
- **Static data**: All data hardcoded in HTML. No APIs, no external data files
- **Page boilerplate**: Standard head (meta, Tailwind CDN, Font Awesome CDN) + optional inline `tailwind.config` + `<script>` at end. Copy an existing page of the same kind (shell / tab container / content)
- **Sub-page navigation**: `parent.loadPage('module/page.html')` — project-root relative
- **Tab container navigation**: `switchTab` uses directory-relative paths; cross-module tabs may use `../learning/...`
- **File naming**: lowercase with underscores
- **Known filename quirks** (do not “fix” without updating all refs): `mainipulation_process.html` (庄家过程), `tongce_medical.html`
- **Paired docs**: Every `.html` has a same-named `.md`

## Page Patterns

- **Tab container**: `.tab-bar` + `.tab-btn` + `#tabFrame`; height `calc(100vh - 42px)`; active underline `#6366F1`
- **Stats cards**: `grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6`
- **Two-column layouts**: `grid grid-cols-1 lg:grid-cols-2 gap-6`
- **Content panels**: card with header bar + body (see content pages)
- **Left-bordered items**: `border-l-4 border-blue-500 pl-4 py-1`
- **Status badges**: `px-2 inline-flex text-xs leading-5 font-semibold rounded-full`
- **Sidebar badges**: sub-page count on multi-tab entries (e.g. 股市认知 → 5)

## Adding a New Page

1. Create the `.html` in the appropriate module directory (boilerplate from a similar page)
2. Create the paired `.md` (概述 / 功能需求 / 页面结构 / 技术实现)
3. Wire navigation:
   - Top-level: add sidebar entry in `index.html` with `onclick="loadPage('module/x.html','标题',event)"`
   - Under an existing module: add a tab in the module’s container page and bump the sidebar badge
4. Sub-pages navigate with `parent.loadPage('module/page.html')`

## Key Files

- `index.html` / `index.md` — Shell
- `README.md` — Project overview, module table, doc index
- `portal/home.html` — Default landing page
- `.claude/skills/html-prototype/SKILL.md` — Detailed templates for generating new pages
- `start.bat` — Optional local static server (port 3004)
