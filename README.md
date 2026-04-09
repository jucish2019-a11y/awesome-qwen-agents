# Awesome Qwen Agents

> A curated collection of **20 production-grade AI agents** for building software products end-to-end — from research and design to engineering, launch, growth, and operations.

Built for [Qwen Code](https://qwen.ai), but the specifications are universal and can be adapted to any AI coding assistant (Claude Code, Cursor, GitHub Copilot, etc.).

---

## Why This Exists

Most AI coding agents are great at writing code but terrible at **deciding what to build, how it should look, whether it's testable, or what happens when it breaks in production**.

These 20 agents fill those gaps. Each one is a detailed specification that turns an AI assistant into a specialized expert — a senior designer who studies Linear and Vercel, a test engineer who knows the modern test pyramid, an SRE who writes runbooks that work at 3am.

Every agent is built on **2025/2026 best practices** from companies known for doing this well: Linear, Vercel, Stripe, Google SRE, PagerDuty, Amplitude, and the open-source design/testing/motion communities.

---

## Quick Start

### Prerequisites
- [Qwen Code](https://qwen.ai) (or any AI coding assistant that supports custom agent specifications)
- A project you want to build

### Installation

#### Option 1: Use with Qwen Code (Recommended)

1. Clone this repository:
```bash
git clone https://github.com/YOUR_USERNAME/awesome-qwen-agents.git
```

2. Copy the `agents/` folder into your Qwen Code configuration directory:
```bash
# Windows
xcopy /E /I awesome-qwen-agents\agents %USERPROFILE%\.qwen\agents\

# macOS / Linux
cp -r awesome-qwen-agents/agents ~/.qwen/agents/
```

3. The agents are now available for Qwen Code to use automatically. When your task matches an agent's capabilities, Qwen Code will invoke it.

#### Option 2: Use as Reference Documents

Each agent in the `agents/` folder is a self-contained markdown file. You can:
- Read them as design/engineering best practice guides
- Use them as prompts for any LLM (paste the content + your task)
- Adapt them for your team's internal AI assistant
- Reference them during code reviews

#### Option 3: Use with Other AI Tools

For Cursor, Claude Code, or GitHub Copilot:
1. Open the agent file you need
2. Paste its content at the start of your conversation as a system prompt
3. Add your specific task after it

---

## Agent Fleet

### 🎨 Design & UX (8 agents)

| Agent | What It Does | When to Use |
|-------|-------------|-------------|
| [**Design System Architect**](agents/design-system-architect.md) | Creates color palettes, typography scales, spacing grids, and tokens using Linear/Vercel/Stripe techniques | Defining a design system for a new app or redesign |
| [**Component Style Spec**](agents/component-style-spec.md) | Produces a single DESIGN.md file defining every component's look, states, and behavior | Before coding components, or when design drift happens |
| [**Motion Design**](agents/motion-design.md) | Animation system with exact timings, easing curves, GPU-accelerated CSS patterns | Defining page transitions, micro-interactions, loading states |
| [**Visual Asset Generator**](agents/visual-asset-generator.md) | Stroke-based SVG icons, empty-state illustrations, avatars, loading skeletons | Generating icon sets, empty states, placeholder images |
| [**UX Research & Wireframe**](agents/ux-research-wireframe.md) | User flows, information architecture, wireframe specs, lightweight usability testing | Before any design — figuring out WHAT to build |
| [**UX Friction Hunter**](agents/ux-friction-hunter.md) | Reviews UI across 7 friction layers, audits state coverage, scores friction | Before shipping any feature |
| [**UX Microcopy Writer**](agents/ux-microcopy-writer.md) | Human-sounding interface copy with component-by-component writing guidelines | Writing button text, error messages, form labels, empty states |
| [**Accessibility Specialist**](agents/accessibility-specialist.md) | WCAG 2.2 compliance, screen reader support, keyboard navigation, ARIA patterns | Building components, auditing UI, legal compliance |

### ⚙️ Engineering & Infrastructure (5 agents)

| Agent | What It Does | When to Use |
|-------|-------------|-------------|
| [**Backend/API Developer**](agents/backend-api-developer.md) | REST/GraphQL APIs, auth, rate limiting, background jobs, file uploads, real-time | Building API endpoints, authentication, middleware |
| [**DevOps/Infrastructure Engineer**](agents/devops-infrastructure-engineer.md) | CI/CD pipelines, Docker, Infrastructure as Code, deployment strategies | Setting up automated deployments |
| [**Database/API Architect**](agents/database-api-architect.md) | Database schema design, API architecture, query optimization, data modeling | Designing data layer before building |
| [**Performance Optimization Engineer**](agents/performance-optimization-engineer.md) | Load testing, bundle size optimization, caching, Core Web Vitals | Before launch, or when app feels slow |
| [**Platform Migration Specialist**](agents/platform-migration.md) | Mobile (React Native/PWA), Desktop (Tauri/Electron), offline-first, app stores | Going mobile or desktop from a web app |

### 🧪 Quality & Operations (4 agents)

| Agent | What It Does | When to Use |
|-------|-------------|-------------|
| [**Pre-Push Commit Auditor**](agents/pre-push-auditor.md) | Conventional commits, secret scanning, security, branch hygiene before push | Before every `git push`, before opening a PR |
| [**Testing Strategy**](agents/testing-strategy.md) | Test pyramid selection, unit/integration/E2E strategy, flaky test prevention, CI gates | Setting up testing for the first time |
| [**Monitoring/Observability Engineer**](agents/monitoring-observability-engineer.md) | Logging infrastructure, alerting, APM, error tracking, SLOs, incident detection | Before launching to production |
| [**Incident Response & Runbook**](agents/incident-response.md) | Severity classification, escalation procedures, runbooks, post-mortems, disaster recovery | After first production incident (or before) |

### 📈 Growth & Data (3 agents)

| Agent | What It Does | When to Use |
|-------|-------------|-------------|
| [**Growth & Launch Strategist**](agents/growth-launch-strategist.md) | Activation optimization, viral loops, freemium conversion, pricing psychology, PLG | Planning launch, optimizing conversion |
| [**Data Analytics & Insights**](agents/data-analytics.md) | Event tracking schema, funnel analysis, cohort analysis, A/B testing, dashboards | Understanding what users actually do |
| [**Technical Documentation Specialist**](agents/technical-documentation-specialist.md) | README files, API docs, ADRs, runbooks, changelogs, onboarding guides | After building core features |

---

## Recommended Workflow

### Building a Product End-to-End

```
PHASE 1: RESEARCH & DESIGN
  1. ux-research-wireframe        → What to build, user flows, wireframe specs
  2. design-system-architect      → Color, type, spacing, elevation tokens
  3. motion-design                → Animation durations, easing curves, patterns
  4. visual-asset-generator       → Icons, illustrations, avatars, skeletons
  5. component-style-spec         → Single DESIGN.md with every component defined
  6. ux-microcopy-writer          → All interface copy for defined components
  7. accessibility-specialist     → Audit components for WCAG compliance
  8. ux-friction-hunter           → Final review of assembled UI for friction

PHASE 2: BUILD
  9. database-api-architect       → Schema design, API contracts
 10. backend-api-developer        → API implementation, auth, middleware
 11. frontend-specialist          → Frontend implementation (built-in Qwen agent)
 12. zero-defect-engineer         → Production-hardened business logic (built-in Qwen agent)
 13. pre-push-auditor             → Audit commits, scan for secrets, verify conventions
 14. testing-strategy             → Test suite for all layers
 15. devops-infrastructure        → CI/CD, Docker, deployment pipeline

PHASE 3: LAUNCH & GROW
 16. performance-optimization     → Load testing, bundle optimization, Core Web Vitals
 17. data-analytics               → Event tracking, dashboards, funnels
 18. growth-launch-strategist     → Activation, viral loops, pricing, launch plan
 19. technical-documentation      → README, API docs, deployment guides

PHASE 4: OPERATE
 20. monitoring-observability     → Logging, alerting, error tracking, SLOs
 21. incident-response            → Runbooks, severity matrix, post-mortems
 22. platform-migration           → Mobile (PWA/RN), Desktop (Tauri/Electron)
```

---

## Design Philosophy

### Why These Agents?

Most AI-assisted development follows this pattern:

```
User: "Build me a task management app"
AI: *generates generic CRUD app with default styling*
Result: Looks like every other AI-generated app
```

These agents break that pattern by enforcing **specialized expertise at each step**:

1. **Research first** — The `ux-research-wireframe` agent figures out what users actually need before any code is written
2. **Design like pros** — The `design-system-architect` uses specific techniques from Linear, Vercel, and Stripe (mathematical type ratios, alpha transparency borders, warm gray palettes) — not generic "use a nice blue"
3. **Build with quality** — The `testing-strategy` agent picks the right test model and writes tests that catch real bugs, not vanity coverage
4. **Launch with data** — The `data-analytics` agent designs event tracking so you know what's actually working
5. **Operate calmly** — The `incident-response` agent has runbooks ready so the first outage is a procedure, not a panic

### What Makes These Different from Generic Prompts

Each agent specification contains:
- **Specific numbers, not vibes**: Type scale ratios (1.200, 1.250, 1.333), border alpha values (`rgba(255,255,255,0.06)`), exact animation durations (150ms ease-out)
- **Real-world references**: Linear's "invisible UI" philosophy, Vercel's Geist font approach, Stripe's layered shadows
- **"What to NEVER do" lists**: Explicit bans on AI design tells (pure black backgrounds, full-opacity borders, "seamless" in copy)
- **Copy-paste-ready code**: Actual CSS keyframes, React component patterns, SQL queries, CI pipeline configs
- **Output standards**: Every agent produces structured, agent-readable deliverables — not essays

---

## Agent Deep Dive

### Design Agents

The 8 design agents work together as a pipeline:

```
ux-research-wireframe     → Defines WHAT to build (flows, IA, wireframes)
design-system-architect   → Defines HOW it looks (tokens, colors, type)
motion-design             → Defines HOW it moves (animations, transitions)
visual-asset-generator    → Creates WHAT's inside (icons, illustrations)
component-style-spec      → Documents EVERYTHING in one DESIGN.md file
ux-microcopy-writer       → Writes what it SAYS (copy for every element)
accessibility-specialist  → Ensures EVERYONE can use it (WCAG compliance)
ux-friction-hunter        → Reviews the ASSEMBLED result for friction
```

**Key differentiator**: These agents study and emulate real premium products. The `design-system-architect` doesn't say "pick a nice color" — it specifies a 10-step neutral scale using OKLCH, a 3-tier border alpha system (0.06/0.1/0.2), and warm grays inspired by Linear's 2026 redesign.

### Engineering Agents

The engineering agents follow 2025/2026 best practices:

- **`backend-api-developer`**: Layered architecture (never expose DB models), cursor-based pagination, JWT with refresh token rotation, "extend don't mutate" API stability
- **`database-api-architect`**: Schema-first design, proper indexing strategy, ORM selection guidance, migration safety
- **`testing-strategy`**: Modern test trophy (integration-first), Playwright E2E with `data-testid`, MSW for mocking, mutation testing validation
- **`devops-infrastructure-engineer`**: Multi-stage Docker builds, GitHub Actions with proper gating, blue-green deployments, secret management
- **`pre-push-auditor`**: Conventional commits enforcement, secret/credential scanning, sensitive file detection, code quality checks, commit atomicity, branch compliance, dependency security, .gitignore completeness, license/legal checks, documentation sync

### Operations Agents

These agents handle what happens AFTER launch:

- **`monitoring-observability-engineer`**: Three pillars (metrics, logs, traces), RED method monitoring, error budget tracking
- **`incident-response`**: SEV-1 through SEV-4 classification, 5-minute acknowledgment, blameless post-mortem templates, quarterly disaster recovery drills
- **`platform-migration`**: Monorepo code sharing strategy, PWA service workers, React Native component mapping, app store requirements

### Growth Agents

These agents ensure the product actually reaches and retains users:

- **`growth-launch-strategist`**: Aha moment identification, viral loop embedding (Calendly/Figma patterns), PQL scoring models, behavioral economics pricing
- **`data-analytics`**: 10-15 critical events (not hundreds), funnel drop-off analysis, cohort retention curves, A/B test statistical rigor
- **`technical-documentation-specialist`**: README that gets developers running in 5 minutes, API docs with request/response examples, ADRs for decisions

---

## Guides

### Getting Started Guides

- [**How to Use These Agents with Qwen Code**](guides/using-with-qwen.md)
- [**How to Adapt These Agents for Claude Code**](guides/using-with-claude.md)
- [**How to Use These as Standalone Prompts**](guides/using-as-prompts.md)

### Best Practice Guides

- [**The Design Pipeline: How the 8 Design Agents Work Together**](guides/design-pipeline.md)
- [**Testing Strategy: From Zero to CI**](guides/testing-from-zero.md)
- [**Launch Checklist: From Design to Production**](guides/launch-checklist.md)

---

## Project Structure

```
awesome-qwen-agents/
├── README.md                          # This file
├── LICENSE                            # MIT License
├── agents/                            # All 20 agent specifications
│   ├── design-system-architect.md
│   ├── component-style-spec.md
│   ├── motion-design.md
│   ├── visual-asset-generator.md
│   ├── ux-research-wireframe.md
│   ├── ux-friction-hunter.md
│   ├── ux-microcopy-writer.md
│   ├── accessibility-specialist.md
│   ├── backend-api-developer.md
│   ├── database-api-architect.md
│   ├── devops-infrastructure-engineer.md
│   ├── performance-optimization-engineer.md
│   ├── platform-migration.md
│   ├── pre-push-auditor.md
│   ├── testing-strategy.md
│   ├── monitoring-observability-engineer.md
│   ├── incident-response.md
│   ├── growth-launch-strategist.md
│   ├── data-analytics.md
│   └── technical-documentation-specialist.md
└── guides/                            # How-to guides
    ├── using-with-qwen.md
    ├── using-with-claude.md
    ├── using-as-prompts.md
    ├── design-pipeline.md
    ├── testing-from-zero.md
    └── launch-checklist.md
```

---

## Inspiration & References

These agents are informed by the design and engineering practices of:

- **Design**: Linear (invisible UI, warm grays), Vercel (Geist, minimalism), Stripe (layered depth, generous type), Raycast (keyboard-first, dense but scannable)
- **Animation**: Framer Motion (spring physics, ease-out defaults), Apple HIG (purposeful motion, reduced motion)
- **Testing**: Spotify's test diamond, Kent C. Dodds' testing trophy, Playwright best practices
- **Operations**: Google SRE (error budgets, SLOs), PagerDuty (incident management), Stripe (runbook quality)
- **Growth**: Amplitude (product analytics), Reforge (growth models), OpenView (PLG benchmarks)

---

## Contributing

Contributions are welcome! If you have an agent specification that fills a gap not covered here, or improves an existing one:

1. Fork the repository
2. Add your agent to `agents/` or improve an existing one
3. Open a pull request with a description of what it adds/fixes

### What Makes a Good Agent Specification?

- **Specific, not generic**: Concrete numbers, named techniques, real references
- **Actionable output**: Clear deliverables the agent must produce
- **"Never do" list**: Explicit anti-patterns to avoid
- **Real-world patterns**: Copy-paste code, tables, and templates
- **Technology coverage**: Modern tool choices with reasoning

---

## License

[MIT License](LICENSE) — Use these agents in personal projects, commercial products, or your team's internal tooling. Attribution appreciated but not required.

---

## Changelog

### v1.1.0 — April 2026
- Added `pre-push-auditor` agent for commit quality and security auditing (20 agents total)
- 4 Quality & Operations agents (was 3)

### v1.0.0 — April 2026
- Initial release with 19 agents
- 8 Design & UX agents
- 5 Engineering & Infrastructure agents
- 3 Quality & Operations agents
- 3 Growth & Data agents

---

<div align="center">

**Built with the belief that AI-assisted development should produce products that look designed, not generated.**

[⭐ Star this repo](../../stargazers) · [🐛 Report a bug](../../issues/new) · [💡 Request an agent](../../issues/new)

</div>
