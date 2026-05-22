# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Korean-language AFC (Automatic Fare Collection) AI/ML use case documentation repository**. It contains 6 detailed use case documents in both Markdown and HTML formats, plus a PPTX-derived presentation HTML.

No build system, package manager, or test suite — all files are standalone HTML/CSS/JS.

## File Conventions

| Pattern | Purpose |
|---------|---------|
| `{N}.{slug}_usecase.md` | Source content (14-section template) |
| `{N}.{slug}_usecase.html` | Formatted single-page HTML |
| `AFC_AI_ML_*_presentation.html` | Multi-slide presentation HTML |
| `bak/` | Original source files (backups before reformatting) |

Use case numbering maps to presentation slide T-codes: file 1 → T1, file 2 → T2, …, file 6 → T6.

## HTML Design System

All 6 use case HTML files share an identical CSS foundation. **Do not deviate from these variables:**

```css
:root {
  --navy: #1a375e; --blue: #2e6da4; --sky: #e8f2fb; --accent: #f08c00;
  --red: #c0392b; --green: #177b4e; --purple: #6a0d91; --teal: #007a87;
  --white: #ffffff; --gray: #f4f6f9; --border: #ccddeee0;
  --text: #1a1a2e; --muted: #5a6a82;
}
```

**Core layout structure (in order):**
1. `<link>` — Noto Sans KR from Google Fonts
2. Hero section (`.hero`) — gradient unique per file + `.hero-badge` + `.hero-summary`
3. Sticky TOC bar (`.toc-bar`) — horizontal chip navigation
4. `.wrapper` (max-width 1200px) — section cards

**Hero gradient per file:**
- File 1: navy→blue `#1a375e → #2e5090 → #1a5276`
- File 4: navy→teal `#0d1f3c → #1a375e → #0d4f6e`
- File 5: navy→dark orange `#1a1f3c → #1a375e → #5c1f0a`
- File 6: navy→deep red `#0d1f2e → #1a375e → #4a1a1a`

**Shared CSS components** (all files must implement these consistently):
- `.card` / `.card-header` / `.card-body` — section containers
- `.flow` / `.flow-step.{data|process|model|output|action|danger}` / `.flow-arrow` — vertical flow diagrams
- `.hflow` / `.hstep` / `.harrow` — horizontal flow diagrams (file 6)
- `.kpi-grid` / `.kpi-card` — KPI display
- `.card-grid` — 2–3 column card grids
- `.tbl-{blue|teal|accent|green|purple|red}` — colored table header variants
- `.sev.sev-{crit|high|med|low}` — severity badges (red/orange/blue/green)
- `.code-block` — dark monospace detection formula display
- `.privacy-box` — teal gradient privacy notice box

## MD Template Structure (14 sections)

When creating or editing use case `.md` files, follow this section order:

1. 유즈케이스 개요
2. 벤치마크 사례 요약
3. Use Case 정의 (업무 문제 + AI 적용 목표)
4. 데이터 구성
5. AI/ML 모델 구조
6. 시스템 아키텍처
7. 기능 요구사항
8. 기관별 적용 포인트
9. 운영 및 품질 관리
10. 리스크 및 대응방안
11. 구현 로드맵
12. KPI 및 성과 지표
13. 개인정보 보호 및 윤리
14. 요약

Avoid "PoC" and "제안서용" in section titles or headings.

## Presentation HTML (`AFC_AI_ML_*_presentation.html`)

Full-screen slide deck (11 slides). Architecture:
- `<section class="slide">` — one per slide, only `.active` is visible
- Bottom fixed `.controls` bar with prev/next buttons
- `.progress-bar` at top
- `.nav-dots` for slide indicators
- Keyboard: `←/→`, `Space`, `Home`, `End`; touch swipe supported
- Dark theme with `rgba(255,255,255,0.08–0.15)` card backgrounds

Slide 3 links T1–T6 to the corresponding use case HTML files via `<a href="..." target="_blank">`. T7 has no file and is rendered as a disabled (`.uc-no-link`) row.
