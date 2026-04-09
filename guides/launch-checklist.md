# Launch Checklist: From Design to Production

## What This Is

A practical checklist for taking a product through the full agent pipeline and shipping it to production. Use this to track what's done, what's in progress, and what's blocking your launch.

---

## Phase 1: Research & Design ✅

- [ ] **User Research** (`ux-research-wireframe`)
  - [ ] Job-to-be-Done statement written
  - [ ] 3 closest alternatives analyzed
  - [ ] User flows mapped (max 7 steps each)
  - [ ] Wireframe specs for all screens

- [ ] **Design System** (`design-system-architect`)
  - [ ] Color tokens defined (neutral, brand, semantic, borders)
  - [ ] Typography scale defined (mobile + desktop)
  - [ ] Spacing scale defined (4px base unit)
  - [ ] Elevation system defined (5 levels, light + dark)
  - [ ] CSS variables + Tailwind config produced

- [ ] **Motion System** (`motion-design`)
  - [ ] Duration scale defined (5 steps)
  - [ ] Easing curves defined (4 curves)
  - [ ] Page transition specified
  - [ ] Component animation catalog complete
  - [ ] `prefers-reduced-motion` strategy defined

- [ ] **Visual Assets** (`visual-asset-generator`)
  - [ ] Icon set generated (stroke-based SVG)
  - [ ] Empty state illustrations created
  - [ ] Avatar placeholder system defined
  - [ ] Loading skeletons with shimmer animation

- [ ] **Component Spec** (`component-style-spec`)
  - [ ] DESIGN.md file created with all 9 sections
  - [ ] Every component has all states defined
  - [ ] Dark AND light mode for every value
  - [ ] File is under 800 lines

- [ ] **Interface Copy** (`ux-microcopy-writer`)
  - [ ] All button labels written
  - [ ] Form labels, helpers, errors written
  - [ ] Empty state copy written
  - [ ] Toast notifications written
  - [ ] No AI-sounding words ("seamless," "delve," "leverage")

- [ ] **Accessibility Audit** (`accessibility-specialist`)
  - [ ] Color contrast audit passed (4.5:1 minimum)
  - [ ] Keyboard navigation verified for all components
  - [ ] ARIA attributes implemented
  - [ ] Focus indicators visible (3:1 contrast)
  - [ ] All violations remediated

- [ ] **Friction Review** (`ux-friction-hunter`)
  - [ ] Friction Score ≤ 6
  - [ ] Zero critical friction items
  - [ ] All moderate friction items fixed or accepted

---

## Phase 2: Build ✅

- [ ] **Database Design** (`database-api-architect`)
  - [ ] Schema defined with proper constraints
  - [ ] Indexes on foreign keys and queried columns
  - [ ] Migration files with up/down scripts
  - [ ] ORM/tool selected and configured

- [ ] **Backend API** (`backend-api-developer`)
  - [ ] REST endpoints defined (RESTful conventions)
  - [ ] Authentication implemented (JWT/session/OAuth)
  - [ ] Input validation on every endpoint
  - [ ] Rate limiting configured
  - [ ] CORS configured (explicit allowlist)
  - [ ] Error response format consistent
  - [ ] Security headers set

- [ ] **Frontend Implementation** (built-in agents)
  - [ ] All components coded per DESIGN.md spec
  - [ ] All states implemented (empty, loading, error, success)
  - [ ] Animations match motion design spec
  - [ ] Copy matches microcopy spec
  - [ ] Responsive breakpoints working

- [ ] **Testing** (`testing-strategy`)
  - [ ] Test model selected (Pyramid/Trophy/Diamond)
  - [ ] Unit tests for complex business logic
  - [ ] Integration tests for API endpoints
  - [ ] E2E tests for critical user journeys
  - [ ] CI pipeline configured (lint → unit → integration → E2E)
  - [ ] Coverage gates set (not 100%, but meaningful targets)

- [ ] **DevOps** (`devops-infrastructure-engineer`)
  - [ ] Dockerfile written (multi-stage build)
  - [ ] CI/CD pipeline configured (GitHub Actions)
  - [ ] Environment variables managed (dev, staging, prod)
  - [ ] Deployment strategy selected (blue-green, canary, or rolling)
  - [ ] Rollback procedure tested

---

## Phase 3: Launch & Grow ✅

- [ ] **Performance** (`performance-optimization-engineer`)
  - [ ] Lighthouse score ≥ 90 on all metrics
  - [ ] Core Web Vitals met (LCP < 2.5s, INP < 200ms, CLS < 0.1)
  - [ ] Bundle size within budget (JS < 200KB gzipped)
  - [ ] Images optimized (WebP/AVIF, responsive sizes)
  - [ ] Caching strategy implemented

- [ ] **Analytics** (`data-analytics`)
  - [ ] 10-15 critical events defined and tracked
  - [ ] Event tracking implemented (PostHog/Amplitude/Segment)
  - [ ] Executive dashboard configured
  - [ ] Funnel analysis set up
  - [ ] Conversion goals defined

- [ ] **Growth Strategy** (`growth-launch-strategist`)
  - [ ] Aha moment identified and optimized
  - [ ] Onboarding flow optimized (time-to-value < 5 min)
  - [ ] Viral loop or referral mechanic designed (if applicable)
  - [ ] Pricing tiers structured (3 tiers, middle highlighted)
  - [ ] Upgrade prompts placed and timed

- [ ] **Documentation** (`technical-documentation-specialist`)
  - [ ] README with quick start (< 5 minutes to running)
  - [ ] API documentation (if applicable)
  - [ ] Architecture decision records (ADRs) for major decisions
  - [ ] Changelog started

---

## Phase 4: Operate ✅

- [ ] **Monitoring** (`monitoring-observability-engineer`)
  - [ ] Error tracking configured (Sentry/Rollbar)
  - [ ] Metrics dashboard live (RED method: Rate, Errors, Duration)
  - [ ] Alert rules defined (actionable, not noisy)
  - [ ] Uptime monitoring from external locations
  - [ ] Log aggregation configured

- [ ] **Incident Response** (`incident-response`)
  - [ ] Severity classification defined (SEV-1 through SEV-4)
  - [ ] Runbooks written for: deploy, rollback, database migration
  - [ ] On-call rotation configured (if team > 3)
  - [ ] Status page set up
  - [ ] Post-mortem template ready

- [ ] **Platform Roadmap** (`platform-migration`)
  - [ ] Platform approach selected (PWA, React Native, Tauri, etc.)
  - [ ] Code sharing strategy defined (monorepo structure)
  - [ ] Offline-first requirements documented
  - [ ] Push notification architecture planned

---

## Launch Day Checklist

- [ ] All Phase 1-4 items complete
- [ ] Final UX friction review (score ≤ 3)
- [ ] Security review (auth, input validation, secrets)
- [ ] Backup verified (test restore from backup)
- [ ] Rollback procedure tested
- [ ] Status page ready (if applicable)
- [ ] Support team briefed on known issues
- [ ] Analytics events firing correctly
- [ ] Monitoring alerts firing (test alert sent)
- [ ] DNS configured (if custom domain)
- [ ] SSL certificate active
- [ ] Email deliverability tested (if sending emails)

---

## Post-Launch (First 2 Weeks)

- [ ] Monitor error rate daily (target: < 1%)
- [ ] Monitor activation rate (target: > 40%)
- [ ] Monitor Day 1 retention (target: > 35%)
- [ ] Review analytics for unexpected usage patterns
- [ ] Collect user feedback (in-app survey, support tickets)
- [ ] Address critical bugs within 24 hours
- [ ] Plan first A/B test (if enough traffic)
- [ ] Write first post-mortem (even if no incidents — document what went well)
