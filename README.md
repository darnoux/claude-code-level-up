# /level-up: The 10 Levels of Claude Code

> **Community project.** This is an unofficial skill built by the [GenAI Circle](https://thegenaicircle.com) community. It is not affiliated with, endorsed by, or sponsored by Anthropic.

Find out where you actually stand with Claude Code, and get a focused roadmap to the next level.

This is a **skill** (custom slash command) for [Claude Code](https://docs.anthropic.com/en/docs/claude-code). It scans your environment, assesses your setup, and gives you a personalized report with concrete next steps.

Not the generic "10 levels of Claude" (browser, desktop, projects). This is specifically about **Claude Code mastery** in the terminal.

## The 10 Levels

| Level | Name | One-liner |
|-------|------|-----------|
| 0 | Terminal Tourist | Just installed it. Typing prompts with no config. |
| 1 | Grounded | CLAUDE.md exists. Claude knows who you are. |
| 2 | Connected | MCP servers pulling real data (Slack, Drive, Notion, Gmail). |
| 3 | Skilled | 3+ custom slash commands you use regularly. |
| 4 | Context Architect | Structured memory system. Knowledge compounds over time. |
| 5 | System Builder | Multi-phase skills, subagents, approval gates, hooks. |
| 6 | Pipeline Engineer | Headless mode. Scripts calling Claude programmatically. |
| 7 | Browser Commander | Playwright/Puppeteer. Screenshots, PDFs, web scraping. |
| 8 | Multi-Agent Operator | Parallel Claude instances. tmux, agent roles, VPS. |
| 9 | Always On | Cron jobs, background agents, Claude as infrastructure. |
| 10 | Swarm Architect | Agents managing agents. Autonomous execution loops. |

Most users land between 1 and 4. Level 5 is strong. Level 7+ is rare.

## Install

**One command.** Run this inside any project where you use Claude Code:

```bash
mkdir -p .claude/commands && curl -sL https://raw.githubusercontent.com/darnoux/claude-code-level-up/main/.claude/commands/level-up.md -o .claude/commands/level-up.md
```

Or clone the whole repo:

```bash
git clone https://github.com/darnoux/claude-code-level-up.git
cd claude-code-level-up
```

## Usage

Open Claude Code in a project where you have the skill installed, then:

```
/level-up            # Full flow: assess + roadmap + optional build
/level-up --assess   # Just show your current level
/level-up --build    # Skip assessment, jump to building the next step
```

## What It Does

### Phase 1: Assessment

Scans your environment automatically (no permissions needed):

- **CLAUDE.md**: exists? how detailed? references memory/patterns?
- **MCP servers**: how many? what categories (data, comms, dev, browser)?
- **Custom skills**: count, complexity, do they chain together?
- **Memory structure**: flat files or deep architecture?
- **Hooks**: quality gates in settings.json?
- **Automation**: headless scripts, JSON piping?
- **Browser tools**: Playwright, Puppeteer, Chrome integration?
- **Multi-agent**: tmux configs, agent roles, VPS deployment?
- **Scheduling**: cron jobs, launchd, pm2, systemd?

Then asks you 3 quick questions to understand your context.

Outputs a clear, honest assessment: here's what you have, here's what's missing, here's where that puts you relative to other users.

### Phase 2: Roadmap

Shows **only the next level**. No information overload. Concrete steps with time estimates and code examples.

Each roadmap includes:
- What the next level unlocks (why it matters)
- Step-by-step instructions (what to do)
- Code snippets you can copy-paste
- Community tips from real users
- Common mistakes to avoid

### Phase 3: Build (Optional)

Asks if you want to build the first step right now. If yes, it does it:

- Level 0: Creates your first CLAUDE.md
- Level 1: Sets up your first MCP connection
- Level 2: Builds your first custom skill
- Level 3-4: Designs your memory architecture
- Level 4-5: Upgrades a skill with phases and subagents
- Level 5-6: Writes your first automation script
- Level 6+: Context audit, pipeline review, optimization

### Dashboard

Every run generates an HTML dashboard at `~/Desktop/level-up-results.html` with your results, progress visualization, and the full roadmap. Dark mode, monospace, clean.

## How Levels Are Determined

The skill checks real signals, not self-reported answers. Your level is the **highest level where you meet ALL criteria**:

- Level 1 requires a CLAUDE.md (any size)
- Level 2 requires 1+ working MCP server
- Level 3 requires 3+ custom skills
- Level 4 requires structured memory directory referenced from CLAUDE.md
- Level 5 requires complex multi-phase skills (80+ lines), subagents or agent definitions, and hook configurations
- Level 6 requires shell scripts calling `claude -p`
- Level 7 requires browser automation (Playwright/Puppeteer)
- Level 8 requires multi-session setups (tmux, agent roles)
- Level 9 requires scheduled automation (cron, launchd, pm2)
- Level 10 requires autonomous agent orchestration

Having 50 simple skills is still Level 3. Complexity and integration matter more than quantity.

## Designed to Be Re-Run

Run `/level-up` after every upgrade to your setup. The assessment updates based on your actual environment. Track your progression over time.

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) (CLI) installed
- Claude Pro, Max, or Team plan
- A project directory (git repo preferred)

## About

Built by the [GenAI Circle](https://thegenaicircle.com) community, a group of professionals learning to work with AI tools daily. The levels, roadmaps, and tips come from real usage patterns across hundreds of members.

Created by [David Arnoux](https://linkedin.com/in/davidarnoux).

## Disclaimer

Claude, Claude Code, and Anthropic are trademarks of Anthropic, PBC. This project is not affiliated with, endorsed by, or sponsored by Anthropic. All trademark references are used solely for identification and description purposes.

## License

MIT. Use it, fork it, share it.
