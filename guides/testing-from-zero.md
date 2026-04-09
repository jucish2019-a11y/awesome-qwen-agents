# Testing Strategy: From Zero to CI

## Who This Guide Is For

Developers who have **no tests** or **a few brittle tests** and want to build a testing strategy that actually catches real bugs without becoming a maintenance nightmare.

---

## The Problem with Most Testing

Most teams either:
1. **Have no tests** because "setting up testing is hard"
2. **Have lots of tests** that break on every refactor and nobody trusts them

Both are equally bad. The agents in this repository take a third path: **test behavior, not implementation**, with a focus on the tests that catch real regressions.

---

## Step 1: Pick Your Test Model

The `testing-strategy` agent selects the right model for your architecture:

| Your Architecture | Model | Why |
|------------------|-------|-----|
| Next.js / React SPA | **Test Trophy** | Integration tests catch the most bugs in SPAs |
| Backend API + Database | **Test Diamond** | Integration with real DB is most important |
| Microservices | **Test Pyramid** | Heavy unit tests, contract tests between services |
| Full-stack monolith | **Hybrid** | Integration-heavy with solid unit coverage for business logic |

**If you're not sure**: Go with the Test Trophy. It works for 80% of modern web apps.

---

## Step 2: Set Up Infrastructure First

Before writing a single test, get the infrastructure running:

### Install Dependencies (Next.js + TypeScript example)
```bash
# Unit/Integration testing
npm install -D vitest @testing-library/react @testing-library/jest-dom jsdom

# E2E testing
npm install -D @playwright/test

# Mocking
npm install -D msw

# Coverage
npm install -D @vitest/coverage-v8
```

### Configure Vitest
```typescript
// vitest.config.ts
import { defineConfig } from 'vitest/config';

export default defineConfig({
  test: {
    environment: 'jsdom',
    setupFiles: './src/test/setup.ts',
    coverage: {
      provider: 'v8',
      reporter: ['text', 'json', 'html'],
      thresholds: {
        lines: 70,
        branches: 65,
      },
    },
  },
});
```

### Configure Playwright
```bash
npx playwright install
```

---

## Step 3: Write Your First Tests

### Start with Integration Tests (Most Important Layer)

**API endpoint test:**
```typescript
describe('POST /api/tasks', () => {
  it('creates a task and returns 201', async () => {
    const response = await request(app)
      .post('/api/tasks')
      .send({ title: 'New task' });

    expect(response.status).toBe(201);
    expect(response.body).toHaveProperty('id');
    expect(response.body.title).toBe('New task');
  });
});
```

**Component integration test:**
```typescript
it('submits the form and shows success', async () => {
  render(<TaskForm onSubmit={mockSubmit} />);

  await userEvent.type(screen.getByLabelText('Title'), 'New task');
  await userEvent.click(screen.getByRole('button', { name: /create/i }));

  expect(mockSubmit).toHaveBeenCalled();
});
```

### Add E2E Tests for Critical Journeys Only

```typescript
test('user can sign up and create first task', async ({ page }) => {
  await page.goto('/signup');
  await page.getByLabel('Email').fill('test@example.com');
  await page.getByLabel('Password').fill('password123');
  await page.getByRole('button', { name: 'Sign up' }).click();

  await page.waitForURL('/dashboard');
  await page.getByRole('button', { name: 'Add task' }).click();
  await page.getByLabel('Title').fill('My first task');
  await page.getByRole('button', { name: 'Create' }).click();

  await expect(page.getByText('My first task')).toBeVisible();
});
```

### Add Unit Tests Only for Complex Logic

```typescript
it.each([
  [0, 0],     // on time, no fine
  [1, 1.00],  // 1 day late
  [10, 10.00], // 10 days late
  [30, 25.00], // caps at maximum
])('%d days late = $%d fine', (days, expected) => {
  expect(calculateFine(days)).toBe(expected);
});
```

---

## Step 4: Set Up CI Pipeline

```yaml
# .github/workflows/test.yml
name: Tests

on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm ci
      - run: npm run lint

  unit-integration:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm ci
      - run: npm run test:unit -- --coverage

  e2e:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm ci
      - run: npx playwright install --with-deps
      - run: npm run build
      - run: npm run test:e2e
```

---

## Step 5: Prevent Flaky Tests

The #1 reason teams abandon testing is flaky tests. Follow these rules:

1. **Never use `sleep()` or `setTimeout`** — use explicit waits: `await expect(element).toBeVisible()`
2. **Every test cleans up** — `beforeEach` resets state
3. **Use `data-testid` for E2E** — not CSS classes that change
4. **Mock external services with MSW** — real APIs make tests nondeterministic
5. **Use fixed dates and IDs** — `vi.useFakeTimers()` for determinism
6. **One concept per test** — not 15 assertions in one giant test

---

## Step 6: Set Reasonable Coverage Targets

| Code Type | Line Coverage | Branch Coverage |
|-----------|--------------|-----------------|
| Core business logic | ≥ 90% | ≥ 85% |
| Backend API handlers | ≥ 80% | ≥ 75% |
| Frontend UI components | ≥ 70% | ≥ 65% |
| Utility/library code | ≥ 95% | ≥ 90% |

**Don't chase 100%.** It's a vanity metric that rewards testing trivialities.

---

## What the `testing-strategy` Agent Adds

This guide is the TL;DR. The full `testing-strategy.md` agent specification provides:

- Complete test model selection framework with decision trees
- Layer-by-layer testing strategies with code examples
- Flaky test prevention rules with specific debugging techniques
- CI pipeline configuration with parallelization
- Test data management patterns (factories, fixtures, containers)
- Mutation testing setup to validate test quality
- Explicit "what NOT to test" lists
- Contract testing between frontend and backend
