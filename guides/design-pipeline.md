# The Design Pipeline: How the 8 Design Agents Work Together

## Overview

The 8 design agents in this repository form a **complete design pipeline** that takes you from "I have an idea" to "I have a polished, accessible, production-ready design system."

This guide explains how they work together, in what order, and what you get at each step.

---

## The Pipeline

```
┌─────────────────────────────────────────────────────────────────┐
│                     THE DESIGN PIPELINE                         │
│                                                                 │
│  1. ux-research-wireframe                                       │
│     ↓ What to build, for whom, in what flow                     │
│                                                                 │
│  2. design-system-architect                                     │
│     ↓ Colors, typography, spacing, elevation tokens             │
│                                                                 │
│  3. motion-design                                               │
│     ↓ Animation durations, easing curves, transition patterns   │
│                                                                 │
│  4. visual-asset-generator                                      │
│     ↓ Icons, illustrations, avatars, loading skeletons          │
│                                                                 │
│  5. component-style-spec                                        │
│     ↓ Single DESIGN.md file documenting every component         │
│                                                                 │
│  6. ux-microcopy-writer                                         │
│     ↓ Button text, error messages, form labels, empty states    │
│                                                                 │
│  7. accessibility-specialist                                    │
│     ↓ WCAG audit, keyboard nav, screen reader support, ARIA    │
│                                                                 │
│  8. ux-friction-hunter                                          │
│     ↓ Final review across 7 friction layers, friction score     │
│                                                                 │
│     ↓↓↓ OUTPUT: Complete, documented, audited design system     │
└─────────────────────────────────────────────────────────────────┘
```

---

## Step-by-Step Breakdown

### Step 1: UX Research & Wireframe
**Agent**: `ux-research-wireframe`

**What happens**: This agent figures out WHAT to build before anyone touches pixels. It defines the user's job-to-be-done, maps user flows, creates information architecture, and produces wireframe specifications.

**What you provide**: A product idea and target user description

**What you get**:
- Jobs-to-be-Done statement
- User flow diagrams (max 7 steps per flow)
- Information architecture with navigation structure
- Wireframe specs with component tables for every screen
- Empty, loading, and error state definitions

**Time**: 1-2 hours of AI interaction

**Why first**: Designing without knowing what you're building is guessing. This agent eliminates the guesswork.

---

### Step 2: Design System Architect
**Agent**: `design-system-architect`

**What happens**: Creates the foundational design tokens — colors, typography, spacing, elevation, border radius, and motion principles — using techniques from Linear, Vercel, Stripe, and Raycast.

**What you provide**: Product type, aesthetic preference (e.g., "dark, dense, like Linear" or "clean, minimal, like Vercel")

**What you get**:
- 10-step neutral color scale (OKLCH or HSL)
- 5-7 step brand/primary palette
- Semantic colors (success, warning, error, info)
- Border color system (3-tier alpha transparency)
- Proportional type scale (1.200, 1.250, or 1.333 ratio)
- Spacing scale (4px base unit: 0, 2, 4, 8, 12, 16, 24, 32...)
- 5-level elevation system with dark/light mode variants
- CSS custom properties + Tailwind configuration

**Time**: 30-60 minutes

**Why second**: Tokens are the foundation everything else is built on. Get these right first.

---

### Step 3: Motion Design
**Agent**: `motion-design`

**What happens**: Defines the complete animation system — duration scales, easing curves, and 10+ production-ready animation patterns for pages, modals, dropdowns, toasts, drag-and-drop, and more.

**What you provide**: The design system from Step 2

**What you get**:
- 5-step duration scale (50ms, 100ms, 150ms, 250ms, 400ms)
- 4 easing curves with cubic-bezier values
- Copy-paste CSS for: page transitions, modal open/close, dropdowns, toasts, stagger lists, drag-and-drop, hover/active states, loading spinners, success checkmarks
- `prefers-reduced-motion` strategy
- Performance budget (< 16ms per frame, max 20 concurrent animations)

**Time**: 20-30 minutes

**Why third**: Motion is part of the design language. Define it before components are coded so every component uses consistent animations.

---

### Step 4: Visual Asset Generator
**Agent**: `visual-asset-generator`

**What happens**: Creates all the visual assets your app needs — icons, empty-state illustrations, avatar placeholders, loading skeletons, and SVG decoration patterns.

**What you provide**: List of icons needed, empty state scenarios, app context

**What you get**:
- Stroke-based SVG icons (Lucide/Linear style: 1.5px stroke, round caps)
- Empty state illustrations (geometric abstraction, 300×200px)
- Avatar placeholder system (deterministic color from name hash)
- Loading skeletons with shimmer animation
- Status indicators (online, away, offline, busy)
- Background decoration patterns

**Time**: 30-60 minutes (depending on number of assets)

**Why fourth**: Assets are applied to the design system. They need the tokens from Step 2 to use the right colors.

---

### Step 5: Component Style Spec
**Agent**: `component-style-spec`

**What happens**: Produces a single `DESIGN.md` file that documents exactly how every component should look in every state. This is the single source of truth for developers and AI agents.

**What you provide**: List of components used in the app

**What you get**: A 300-800 line DESIGN.md file with 9 sections:
1. Visual theme & atmosphere
2. Color palette & roles
3. Typography rules
4. Component stylings (button, input, card, modal, table, badge — with all states)
5. Layout principles
6. Depth & elevation
7. Motion & animation
8. Do's and don'ts
9. Responsive behavior

**Time**: 30-45 minutes

**Why fifth**: This consolidates everything from Steps 2-4 into one reference document. It's what developers actually read when building components.

---

### Step 6: UX Microcopy Writer
**Agent**: `ux-microcopy-writer`

**What happens**: Writes all the interface copy — button labels, error messages, form helper text, empty state messages, toast notifications, confirmation dialogs — in a human, specific, non-AI-sounding voice.

**What you provide**: Component list from Step 5, product voice preference

**What you get**:
- Button copy for every component (max 3 words, verb-first)
- Form labels, placeholders, helper text, error messages
- Empty state headlines and body text
- Toast notification messages
- Confirmation dialog titles, body text, and button labels
- Onboarding flow copy

**Time**: 20-30 minutes

**Why sixth**: Copy needs the component context from Step 5. "Create task" on a button has different constraints than "Task created" in a toast.

---

### Step 7: Accessibility Specialist
**Agent**: `accessibility-specialist`

**What happens**: Audits the entire design system for WCAG 2.2 AA compliance — color contrast, keyboard navigation, screen reader support, ARIA implementation, focus management.

**What you provide**: The complete design system (Steps 2-6)

**What you get**:
- Color contrast audit with pass/fail for every text/background combination
- Keyboard navigation map for every component
- ARIA attribute specifications for custom components
- Focus indicator designs (2px outline, 3:1 contrast)
- Remediation steps for every violation found
- Screen reader testing checklist

**Time**: 30-45 minutes

**Why seventh**: Accessibility needs the complete design to audit. Fixing contrast is easier before components are coded.

---

### Step 8: UX Friction Hunter
**Agent**: `ux-friction-hunter`

**What happens**: Reviews the complete assembled design system from a power user perspective, identifying friction across 7 layers: cognitive, visual, interaction, state, feedback, onboarding, and performance.

**What you provide**: Complete design system with all components, states, and copy

**What you get**:
- Critical friction list (must fix before shipping)
- Moderate friction list (should fix soon)
- Minor friction list (nice to have)
- Friction Score: X/10 with ship/fix/don't-ship recommendation
- Specific fixes for every issue found

**Time**: 20-30 minutes

**Why last**: This is the final quality gate. It reviews everything assembled and catches what the individual specialists missed.

---

## Output Summary

After completing all 8 steps, you have:

| Artifact | Produced By | Used By |
|----------|------------|---------|
| User flows & wireframes | Step 1 | Designers, frontend developers |
| Design tokens (CSS/Tailwind) | Step 2 | All developers |
| Animation system (CSS) | Step 3 | Frontend developers |
| SVG icons & illustrations | Step 4 | Frontend developers |
| DESIGN.md (component spec) | Step 5 | All developers, AI coding agents |
| Interface copy | Step 6 | Frontend developers, UX writers |
| Accessibility audit | Step 7 | Frontend developers, QA team |
| Friction audit with score | Step 8 | Product managers, designers |

---

## Skipping Steps

You don't always need all 8 steps. Here's when to skip:

| Scenario | Skip | Use |
|----------|------|-----|
| Redesigning colors only | 1, 3, 4, 6, 7, 8 | 2, 5 |
| Adding one new feature | 2, 3, 4 | 1, 5, 6, 7 |
| Polishing an existing app | 1, 2, 4 | 3, 5, 6, 7, 8 |
| Quick audit before launch | 1, 2, 3, 4 | 5, 7, 8 |
| Writing copy for built components | 1, 2, 3, 4, 5 | 6 |

---

## Real-World Example

**Product**: Task management SaaS for small teams
**Aesthetic**: "Dark, dense, calm — like Linear"

```
Step 1: ux-research-wireframe
→ Job-to-be-done: "When I have multiple tasks across team members,
   I want to see who's doing what at a glance,
   so nothing falls through the cracks."
→ 3 user flows: create task, assign task, complete task
→ Navigation: Hub-and-spoke (Board, List, Calendar, Team, Settings)

Step 2: design-system-architect
→ Neutral scale: 10-step zinc-based dark mode
→ Primary: Violet (#8B5CF6) with 500/400/600 hierarchy
→ Type scale: 1.200 (minor third) for dense app UI
→ Spacing: 4px base, 16px standard gap
→ Borders: rgba(255,255,255,0.06) subtle, 0.1 medium, 0.2 strong

Step 3: motion-design
→ 150ms ease-out default transitions
→ Page entrance: fade + 8px slide up in 250ms
→ Modal open: backdrop fade + dialog scale 0.95→1

Step 4: visual-asset-generator
→ 24 stroke-based icons (home, board, list, calendar, team, settings)
→ Empty state: geometric clipboard + checkmark for "No tasks yet"
→ Avatar initials badge with deterministic violet/blue/green colors

Step 5: component-style-spec
→ 387-line DESIGN.md documenting: button (3 sizes, 4 variants),
  input, card, modal, table, badge, dropdown, tooltip, tab
  — every component with all states in both light and dark mode

Step 6: ux-microcopy-writer
→ Button: "Create task" (not "Submit")
→ Empty state: "No tasks yet. Create your first one to get started."
→ Error: "Couldn't save task. Check your connection and try again."
→ Toast: "Task moved to Done" (not "Action completed successfully")

Step 7: accessibility-specialist
→ Found 3 contrast failures (fixed gray text on dark background)
→ Keyboard navigation: Tab order verified for all components
→ ARIA: role="dialog" + aria-modal for modals, aria-live for toasts

Step 8: ux-friction-hunter
→ Friction Score: 3/10 — Ship it
→ Critical: 0 issues
→ Moderate: Missing skeleton screen for board load (fix before ship)
→ Minor: No keyboard shortcut for "complete task" (add later)
```

**Result**: A complete, documented, audited design system that looks like it was crafted by a dedicated design team — produced in ~4 hours of AI interaction time.
