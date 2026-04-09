# Using These Agents as Standalone Prompts

## You Don't Need Qwen Code

Every agent in this repository is a self-contained markdown file. You can use it with **any** LLM — ChatGPT, Claude, Gemini, Llama, or any AI coding tool that accepts text input.

## How to Use

### Method 1: Paste as System Prompt

1. Open the agent file you need
2. Copy its entire contents
3. Paste it as the first message in your conversation
4. Add your specific task after it

**Example:**
```
[Paste entire content of design-system-architect.md]

---

My task: Create a design system for a project management app that targets small creative teams. I want a light-mode-first aesthetic inspired by Vercel's clean minimal style, with teal accents.
```

### Method 2: Use as a Reference Document

1. Keep the agent file open in a tab
2. Work through it section by section with your LLM
3. Reference specific sections: "Follow the Output Standards from section 4"

### Method 3: Break Into Smaller Tasks

Large agent files can overwhelm some LLMs. Break them into specific requests:

Instead of: *"Run the full testing-strategy agent"*

Do:
1. *"Using the testing-strategy agent, select the right test model for my Next.js app with a REST API and PostgreSQL database"*
2. *"Now write the integration test specs for my /api/tasks endpoints"*
3. *"Now set up the E2E test for the critical user journey: signup → create task → complete task"*

## Which Agent to Use When

| Your Task | Agent to Use |
|-----------|-------------|
| "I need a color system" | `design-system-architect.md` |
| "I need to document how every component looks" | `component-style-spec.md` |
| "I need animations for my app" | `motion-design.md` |
| "I need icons and illustrations" | `visual-asset-generator.md` |
| "I need to figure out what to build" | `ux-research-wireframe.md` |
| "Review my UI for problems" | `ux-friction-hunter.md` |
| "Write my button text and error messages" | `ux-microcopy-writer.md` |
| "Make my app accessible" | `accessibility-specialist.md` |
| "Build my API endpoints" | `backend-api-developer.md` |
| "Design my database schema" | `database-api-architect.md` |
| "Set up my CI/CD pipeline" | `devops-infrastructure-engineer.md` |
| "Make my app faster" | `performance-optimization-engineer.md` |
| "Go mobile from my web app" | `platform-migration.md` |
| "Write tests for my app" | `testing-strategy.md` |
| "Set up monitoring" | `monitoring-observability-engineer.md` |
| "Handle production incidents" | `incident-response.md` |
| "Grow my user base" | `growth-launch-strategist.md` |
| "Track what users actually do" | `data-analytics.md` |
| "Write my README and docs" | `technical-documentation-specialist.md` |

## Tips for Best Results

1. **Provide context**: The more you tell the agent about your product, the better its output
2. **Be specific about constraints**: "I'm a solo developer" changes the recommendations vs. "I have a team of 5"
3. **Ask for deliverables**: Each agent has defined output standards — reference them explicitly
4. **Iterate**: If the output isn't quite right, refine your prompt with more specifics
5. **Combine agents**: Use multiple agents in sequence for complex projects (see [Design Pipeline guide](design-pipeline.md))
