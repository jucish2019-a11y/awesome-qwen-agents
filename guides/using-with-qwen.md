# Using These Agents with Qwen Code

## What is Qwen Code?

Qwen Code is an AI coding assistant (similar to Claude Code, Cursor, or GitHub Copilot) that can launch specialized "agents" — subprocesses with deep expertise in specific domains like design, testing, infrastructure, or growth.

## How Agents Work

When you describe a task that matches an agent's capabilities, Qwen Code automatically routes your request to the right specialist. For example:

- You say: *"Design a color system for my SaaS app"*
- Qwen Code routes to: `design-system-architect`
- You get: A complete 10-step neutral scale, brand palette, semantic colors, border colors, and Tailwind config

## Setup

### Step 1: Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/awesome-qwen-agents.git
```

### Step 2: Install Agents

Copy the agent files to your Qwen Code agents directory:

**Windows:**
```cmd
xcopy /E /I awesome-qwen-agents\agents %USERPROFILE%\.qwen\agents\
```

**macOS / Linux:**
```bash
cp -r awesome-qwen-agents/agents ~/.qwen/agents/
```

### Step 3: Verify Installation

Your `.qwen/agents/` directory should now contain 19 `.md` files:

```
~/.qwen/agents/
├── design-system-architect.md
├── component-style-spec.md
├── motion-design.md
├── ... (16 more)
```

## Using Agents

### Automatic Invocation

Once installed, agents are invoked automatically when your task matches their description. You don't need to call them explicitly — just describe what you need:

```
You: "Create a dark mode color system for my project management app"
→ design-system-architect agent activates automatically

You: "Review my login page for usability issues"
→ ux-friction-hunter agent activates automatically

You: "Set up tests for my API endpoints"
→ testing-strategy agent activates automatically
```

### Explicit Invocation

You can also explicitly request an agent:

```
You: "Use the design-system-architect to create my typography scale"
→ Qwen Code launches the specific agent
```

## Tips for Best Results

1. **Be specific about your product**: Mention your app type, target users, and aesthetic preferences (e.g., "dark SaaS app like Linear")
2. **Reference real products**: Agents know the design patterns of Linear, Vercel, Stripe, etc. Use them as references
3. **Follow the pipeline**: For design-heavy projects, use agents in order: research → design → motion → assets → component spec → copy → accessibility → friction review
4. **Ask for deliverables**: Each agent has defined output standards. Ask for them explicitly: "Produce the full DESIGN.md file"

## Troubleshooting

### Agent Not Triggering

If an agent doesn't activate:
1. Check that the `.md` file exists in `~/.qwen/agents/`
2. Try explicitly naming the agent: "Use the [agent-name] to..."
3. Make your task more specific to the agent's domain

### Agent Output Seems Generic

The agents are only as good as the context you provide. Add specifics:
- Bad: "Design my app"
- Good: "Design a dark-mode-first design system for a task management SaaS, inspired by Linear's calm, dense aesthetic, with violet accents"

## Updating Agents

To get the latest versions:

```bash
cd awesome-qwen-agents
git pull
cp agents/*.md ~/.qwen/agents/
```
