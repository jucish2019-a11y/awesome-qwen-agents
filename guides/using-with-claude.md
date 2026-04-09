# Using These Agents with Claude Code

## What is Claude Code?

Claude Code is Anthropic's AI coding assistant, similar to Qwen Code. It operates as a CLI-based agent that can read, write, and edit code in your project. While it doesn't have a native "agent" system like Qwen Code, you can still leverage these specifications effectively.

## How to Use

### Method 1: Project Context File

1. Copy the agent files into your project's root:
```bash
mkdir -p .claude/agents
cp awesome-qwen-agents/agents/*.md .claude/agents/
```

2. Reference them in your `.claude/settings.json` or project context:
```json
{
  "context_files": [".claude/agents/*.md"]
}
```

3. When you need an agent, reference it in your prompt:
```
Read .claude/agents/design-system-architect.md and follow its instructions to create a design system for my app.
```

### Method 2: Inline Reference

Simply paste the relevant sections of an agent file into your conversation:

```
I'm following the design-system-architect specification. Here are the key rules:
[Paste the "Output Standards" and "What to NEVER Do" sections]

Now create a design system for my fitness tracking app.
```

### Method 3: Custom Instructions

Add your preferred agent specifications to Claude's custom instructions:

1. Go to Claude settings → Custom Instructions
2. Add: "When asked about design, follow the principles in [your agent file]. When asked about testing, follow the testing-strategy specification..."

## Key Differences from Qwen Code

| Feature | Qwen Code | Claude Code |
|---------|-----------|-------------|
| Agent auto-invocation | ✅ Automatic | ❌ Manual reference |
| Context file support | ✅ `.qwen/agents/` | ✅ `.claude/agents/` |
| File editing | ✅ | ✅ |
| Shell commands | ✅ | ✅ |

## Recommended Workflow for Claude Code Users

Since Claude Code doesn't auto-invoke agents:

1. **Keep a cheat sheet**: Bookmark the [README](../README.md) agent table
2. **Use a task → agent mapping**: When you have a task, check which agent covers it
3. **Reference the file**: Always tell Claude Code which agent file to follow
4. **Be explicit**: "Follow the output standards from the testing-strategy agent"
