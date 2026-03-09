---
description: Assess your Claude Code level (0-10) and get a personalized roadmap to the next one
---

# Level Up

The 10 Levels of Claude Code. Scan your environment, determine where you actually are, get a focused roadmap to the next level, and optionally build the first step right now.

This is NOT the generic "10 Levels of Claude" (browser, desktop, projects). This is specifically about Claude Code mastery. Level 0 is "just installed it." Level 10 is genuinely rare.

**Usage:**
- `/level-up` - Full flow: assess, roadmap, build
- `/level-up --assess` - Just show your current level
- `/level-up --build` - Skip assessment, jump to building

---

## How It Works

```
Scan Environment → Determine Level → Show Roadmap → Build First Step
       ↓                 ↓                ↓               ↓
   Phase 1           Phase 1          Phase 2          Phase 3
   (automatic)       (+ 3 questions)  (next level)     (optional)
```

Designed to be run repeatedly. Every time you level up, the assessment updates.

---

## The 10 Levels of Claude Code

| Level | Name | What It Means (Plain English) |
|-------|------|-------------------------------|
| 0 | Terminal Tourist | You just installed it. You're typing prompts like it's ChatGPT but in a terminal. No setup, no config. That's fine, everyone starts here. |
| 1 | Grounded | You've created a CLAUDE.md file so Claude actually knows who you are and what you want. You know the basic commands. This alone makes a huge difference. |
| 2 | Connected | Claude can read your actual tools: your Slack, your Drive, your Notion, your Gmail. You're not copy-pasting context anymore. It just pulls what it needs. |
| 3 | Skilled | You've built reusable commands (skills) you run regularly. Instead of re-explaining the same task every session, you type `/research` or `/review` and it just works. |
| 4 | Context Architect | You've built a structured knowledge system: memory files, patterns, client profiles, examples. Claude doesn't just follow instructions, it draws from everything you've taught it. Output gets better over time. |
| 5 | System Builder | Your skills chain together. One feeds into the next. You use sub-agents for parallel work. You have approval gates so nothing ships without your sign-off. This is where Claude feels like a team, not a tool. |
| 6 | Pipeline Engineer | You're calling Claude from scripts. Headless mode, JSON output, piping data through it programmatically. Claude is a component in your automation stack, not just a chat window. |
| 7 | Browser Commander | Claude controls a browser. It scrapes websites, takes screenshots, generates PDFs, builds carousels. Research pipelines that crawl the web and turn findings into deliverables. |
| 8 | Multi-Agent Operator | Multiple Claude instances running simultaneously. Each one is a specialist. You coordinate them like a team lead. They share work through files and git. |
| 9 | Always On | Claude runs on a schedule whether you're at your desk or not. Cron jobs, background agents, automated monitoring. It's infrastructure now, not a tool you open. |
| 10 | Swarm Architect | Agents that manage other agents. Autonomous execution loops. Give it a goal and it works toward it, spawning sub-agents as needed. Genuinely rare. Maybe a handful of people on the planet. |

Most users land between Level 1 and 4. Level 5 is strong. Level 7+ is rare.

---

## Phase 1: Assess Your Level

### Step 1.1: Environment Scan

Silently scan the user's environment. Do NOT ask permission for each check. Just read what's available.

**Check all of these:**

```
1. CLAUDE.md (check ALL locations)
   - Check: CLAUDE.md, .claude/CLAUDE.md, CLAUDE.local.md, ~/.claude/CLAUDE.md
   - Does any exist? How many locations are used?
   - How many lines total? (< 10 = minimal, 10-50 = basic, 50-150 = solid, 150+ = advanced)
   - Does it reference memory files, patterns, workflows?
   - Does it have navigation tables, progressive disclosure, workflow instructions?

2. Skills / Commands
   - Check both .claude/commands/ AND .claude/skills/ directories
   - Count total skills
   - Read 2-3 to check complexity:
     * Simple (< 20 lines, single prompt) = Level 3
     * Medium (20-80 lines, multi-step) = Level 3-4
     * Complex (80+ lines, phases, approval gates, tool calls) = Level 5+
     * Skills that call other skills or orchestrate sub-agents = Level 5-6

3. MCP Configuration
   - Check .mcp.json in current directory (project-level)
   - Check ~/.claude.json for mcpServers (user-level)
   - Optionally check managed config if enterprise
   - Count configured MCP servers across all locations
   - Categorize: data (Notion, Drive), comms (Slack, Gmail), dev (GitHub, Supabase), browser (Puppeteer, Chrome), specialty (PostHog, GSC)

4. Memory / Context Structure
   - Is there a memory/ directory?
   - How deep? (flat files = Level 4, nested dirs like memory/patterns/, memory/customers/, memory/examples/ = Level 4-5)
   - Are there templates, workflows, experience directories?
   - Does the CLAUDE.md reference and route to memory files?

5. Quality Gate Signals (Level 5+)
   - Hook configurations in .claude/settings.json? (PreToolUse, PostToolUse, etc.)
   - Agent definitions in .claude/agents/ or ~/.claude/agents/?
   - Hooks are quality gates, not infrastructure. They belong here, not at Level 9.

6. Automation Signals (Level 6+)
   - Any shell scripts that call `claude -p` or `claude --print`?
   - Any package.json with Playwright or Puppeteer?
   - Any screenshot scripts, PDF generators, scraping tools?
   - Evidence of JSON output piping?
   - Chrome browser integration enabled (CLI flags)?

7. Multi-Agent Signals (Level 8+)
   - tmux config files or scripts?
   - Multiple CLAUDE.md files for different agent roles?
   - VPS deployment evidence?

8. Always-On Signals (Level 9-10)
   - Cron jobs, launchd services, or systemd services calling Claude on a schedule?
   - Background agents running 24/7 (pm2, systemd)?
   - Autonomous loop scripts (PRD + test suite patterns)?
   - Agent orchestration configs (Agent Teams, Gastown, OpenClaw)?
   - Evidence of agents managing other agents?
```

### Step 1.2: Context Questions

Ask the user these 3 questions:

1. **What do you mainly use Claude Code for?** (coding / content creation / research / automation / business operations / other)
2. **What's your biggest friction right now?** (output quality / context limits / don't know what's possible / speed / reliability)
3. **If you could automate one thing you do repeatedly, what would it be?**

### Step 1.3: Determine Level

Use this scoring system. The user's level is determined by the HIGHEST level where they meet ALL criteria:

| Level | Required Signals |
|-------|-----------------|
| 0 | No CLAUDE.md, no .claude/ directory |
| 1 | CLAUDE.md exists (any size). Knows basic slash commands. |
| 2 | .mcp.json with 1+ working MCP servers. Pulling real data into sessions. |
| 3 | 3+ custom skills in .claude/commands/ or .claude/skills/. Uses them regularly. |
| 4 | Structured memory/ directory with patterns, examples, or knowledge files. CLAUDE.md references them. Context architecture, not just a config file. |
| 5 | Complex multi-phase skills (80+ lines). Skills chain together (output of one feeds another). Evidence of subagent usage or agent definitions in .claude/agents/. Hook configurations for quality gates. Consistent production-quality output. |
| 6 | Shell scripts or automation calling `claude -p`. JSON output piping. Programmatic integration beyond interactive use. |
| 7 | Browser automation in project (Playwright, Puppeteer, or Chrome integration). Screenshot automation, PDF generation, web scraping workflows. Browser-powered pipelines. |
| 8 | tmux multi-session setups. Multiple parallel CC instances. Different agent roles. VPS or remote deployment. |
| 9 | Cron jobs or scheduled tasks running CC. Background agents running 24/7. CC as persistent infrastructure, not a tool you open. |
| 10 | Autonomous execution loops. Multi-agent orchestration frameworks. Agents spawning and managing other agents. Safety boundaries and rollback systems. |

**Important:** Having lots of files doesn't automatically mean advanced. 50 simple skills is still Level 3. The complexity and integration between components matters more than quantity.

### Step 1.4: Present the Assessment

Show the user their level with clear reasoning. The goal is to make them feel understood, not judged. Explain WHY each thing matters, not just that you found it.

```
## Your Claude Code Level: [X] / 10

**[Level Name]**

### Here's why you're at Level [X]:

Walk through the levels one by one, bottom to top, showing what you found for each:

**Level 0 (Terminal Tourist): ✓ You're past this.**
You have [specific thing], so you're clearly not just typing into a terminal with no setup.

**Level 1 (Grounded): ✓ Covered.**
Your CLAUDE.md [describe what it looks like: how long, what's in it, how detailed].
This means Claude actually knows [what it knows about them]. That's the foundation.

**Level 2 (Connected): ✓ Covered.**
You have [X] MCP servers: [list them]. That means Claude can directly [what those MCPs enable: read your Slack, check your email, pull from Notion, etc.]. You're not copy-pasting context anymore.

[Continue for each level they've achieved...]

**Level [X+1] ([Name]): ✗ This is where it stops.**
[Explain plainly what's missing and WHY it matters. Don't just say "no headless scripts found." Say something like: "Right now you're doing everything interactively. You open Claude, type a command, wait for output. Level 6 is about making Claude work without you sitting there. You'd write a script that calls Claude, processes the output, and saves it somewhere. Like a morning briefing that generates itself before you wake up. I didn't find any scripts like that in your setup."]

### The short version:
[One paragraph summary. Example: "You've got a solid foundation: Claude knows who you are, it can pull from your real tools, and you've built workflows that run on command. That's strong. What you're missing is the jump from interactive to programmatic. Everything still requires you to be in the chair typing commands."]

### Where that puts you:
Most Claude Code users land between Level 1 and 4. At Level [X], you're [ahead of most / in the middle / at the frontier / etc.].
```

**Tone rules:**
- Talk to them like a knowledgeable friend, not a grading rubric
- Explain things like you're talking to someone smart who just hasn't seen this particular thing before
- If something is impressive, say so genuinely
- If something is messy or could be better, say that too, but constructively
- Use "you" and "your", not "the user"
- Avoid jargon without explanation. If you mention "headless mode" also say "that means running Claude from a script instead of typing into the terminal"
- The goal is: after reading this, they understand exactly what they have, what they're missing, and why the next level matters

If `--assess` flag was used, stop here. Otherwise continue to Phase 2.

---

## Phase 2: Your Roadmap

Show ONLY the next level transition. Do not dump all 10 levels. Focus is everything.

**Pick the matching section below based on assessed level.**

---

### Level 0 → Level 1: Get Grounded

**What this unlocks:** Claude remembers your preferences, follows your rules, produces consistent output instead of generic responses every session.

**Your roadmap:**

1. **Create your CLAUDE.md** (10 minutes)
   - This is the single most important file. Claude reads it at the start of every session.
   - Include: who you are, what you do, your communication preferences, your project context, rules for output quality.
   - Think of it as onboarding a new team member. What would they need to know on day one?

2. **Set up your project folder** (2 minutes)
   - Create a dedicated folder for your main work.
   - Initialize git: `git init` (Claude Code works best in git repos, it tracks changes).
   - Put your CLAUDE.md at the root.

3. **Learn the essential commands** (5 minutes)
   - `/compact` compresses your conversation to save context space
   - `/model` switches between Opus (deep reasoning), Sonnet (daily work), Haiku (quick tasks)
   - `/cost` shows how much you've spent this session
   - `/help` shows everything available

4. **Run a real task** (10 minutes)
   - Don't start with toy problems. Give it something you actually need done.
   - Notice how it follows your CLAUDE.md rules.

**Community tip:** "The quality of your repository dictates the quality of your output." Members who invested 30 minutes in their CLAUDE.md before doing anything else got dramatically better results from day one.

**Common mistake:** Writing a CLAUDE.md that's too vague. "Be helpful" means nothing. "Always write in short paragraphs, use data to support claims, never use jargon" means everything.

---

### Level 1 → Level 2: Connect Your Data

**What this unlocks:** Claude reads your actual Slack messages, Notion pages, Google Docs, Gmail. No more copy-pasting context. It just knows.

**Your roadmap:**

1. **Pick your first MCP** (5 minutes)
   - If you use Google Drive: start there (docs, sheets, slides)
   - If you use Notion: start there (databases, pages)
   - If you communicate via Slack: start there
   - If email is your life: Gmail MCP

2. **Add it to your config** (5 minutes)
   - Create `.mcp.json` in your project root (or add to `~/.claude.json` for global access).
   - Example structure:
   ```json
   {
     "mcpServers": {
       "google-drive": {
         "command": "npx",
         "args": ["-y", "@anthropic-ai/google-drive-mcp"]
       }
     }
   }
   ```
   - Restart Claude Code after adding.

3. **Test it with a real task** (5 minutes)
   - "Summarize the last 5 messages in #general on Slack"
   - "What are the action items from my last meeting notes in Notion?"
   - "Draft a reply to the last email from [name]"

4. **Add a second MCP** (5 minutes)
   - Two connected data sources is where the magic starts.
   - Claude can cross-reference: "Based on the Slack discussion AND the Notion brief, draft the proposal."

**Community tip:** Don't install 15 MCPs on day one. Tijmen discovered that too many MCPs bloat your starting context. Claude Code's tool search feature helps (dropped context from 51% to 13%), but fewer is still better. Start with 1-2 that match your daily work.

**Best first combos:**
- Content creators: Google Drive + Notion
- Marketers: Slack + Google Drive
- Developers: GitHub + Supabase
- Consultants: Notion + Gmail + Slack

---

### Level 2 → Level 3: Build Your Skills

**What this unlocks:** Repeatable workflows you trigger with a single command. Instead of re-explaining tasks every session, you type `/review` or `/research` and it runs the whole thing.

**Your roadmap:**

1. **Identify your most repeated task** (5 minutes)
   - What do you explain to Claude Code at least once a week?
   - What has a consistent structure every time?
   - That answer from question 3 in the assessment? That's your first skill.

2. **Create the skill file** (10 minutes)
   - Create `.claude/commands/` directory if it doesn't exist.
   - Create a markdown file: `.claude/commands/[name].md`
   - Structure:
   ```markdown
   ---
   description: What this skill does in one line
   ---

   # [Skill Name]

   [2-3 sentences: what this does and when to use it]

   ## Steps

   1. [First thing Claude should do]
   2. [Second thing]
   3. [Third thing]

   ## Output Format

   [Describe what the final output should look like]

   ## Rules

   - [Important constraint 1]
   - [Important constraint 2]
   ```

3. **Test and iterate** (5 minutes)
   - Type `/[name]` to run it.
   - First version won't be perfect. Run it, see what's off, edit the .md file.
   - Good skills get specific over time. Add examples, add rules, add edge cases.

4. **Build 2-3 more skills** (ongoing)
   - Research, review, create. That's the core three most people start with.
   - Skills compound. Your `/research` feeds into `/create` which feeds into `/review`.

**Community tip:** Skills turn Claude into a team member who never forgets the process. After building 5+ skills, output consistency goes from "hit or miss" to "reliable every time."

**Note on terminology:** "Custom commands" and "skills" are the same thing. Files in `.claude/commands/` and `.claude/skills/` both create slash commands. The skills format (`.claude/skills/[name]/SKILL.md`) supports additional features like frontmatter config and supporting files.

---

### Level 3 → Level 4: Become a Context Architect

**What this unlocks:** A persistent knowledge system. Claude doesn't just follow instructions. It draws from your accumulated knowledge, patterns, client history and examples to produce work that improves over time.

**Your roadmap:**

1. **Design your memory architecture** (20 minutes)
   - Create a structured knowledge base Claude can reference:
   ```
   memory/
   ├── company/        # Your business context
   ├── customers/      # Client profiles and history
   ├── patterns/       # Reusable approaches and frameworks
   └── examples/       # Reference outputs and templates
   ```
   - Each file is markdown. Keep them focused. One topic per file.

2. **Connect it through CLAUDE.md** (10 minutes)
   - Your CLAUDE.md becomes the index. It tells Claude where to find what.
   - Add a "Repository Navigation" section mapping needs to file paths.
   - Add a "Before Starting Work" section: "Load memory/customers/[client] before any client work."

3. **Seed it with knowledge** (30 minutes)
   - Write down your top 5 patterns, frameworks, or approaches you use repeatedly.
   - Save 3-5 examples of your best output as reference files.
   - Create a client/project profile for your main work.

4. **Build the feedback loop** (ongoing)
   - After every project, extract what worked into memory/patterns/.
   - Your system gets smarter with every project. This is where compounding starts.

**Community tip:** "I moved my entire business into GitHub. Everything is a repo." The members running structured knowledge systems report 3-5x productivity gains after the first month of accumulation.

**The formula:** Context quality = output quality. This is not prompt engineering. This is context engineering.

---

### Level 4 → Level 5: Build Systems, Not Skills

**What this unlocks:** Multi-phase workflows that produce consistently excellent output. Skills that call other skills. Sub-agents that handle specialized tasks. You become the architect, not the operator.

**Your roadmap:**

1. **Write multi-phase skills** (15 minutes)
   - Upgrade your simple skills to have phases with approval gates:
   ```markdown
   ## Phase 1: Research
   [Steps...]
   **Approval gate:** Wait for confirmation before proceeding.

   ## Phase 2: Create
   [Steps...]
   **Approval gate:** Review draft before finalizing.

   ## Phase 3: Review
   [Steps...]
   ```

2. **Chain skills together** (10 minutes)
   - Design skills that feed into each other.
   - `/research [company]` outputs a brief → `/create [deliverable]` uses it → `/review` quality checks it.
   - Reference each other in the skill files.

3. **Use subagents** (10 minutes)
   - In your skills, use the Agent tool to spin up specialized subagents:
     * Explore agents for codebase search
     * Plan agents for architecture design
     * General-purpose agents for multi-step research
   - Define agent roles in `.claude/agents/` (project) or `~/.claude/agents/` (global)
   - Subagents run in parallel. One researches while another writes while another reviews.

4. **Set up hooks as quality gates** (10 minutes)
   - Configure pre/post hooks in `.claude/settings.json` that fire before or after Claude acts.
   - PreToolUse hooks: block writes to sensitive files (.env, credentials), enforce formatting.
   - PostToolUse hooks: auto-lint, run checks after edits.
   - Hooks are quality guardrails, not infrastructure. They belong at this level.

5. **Quality systems** (ongoing)
   - Build review checklists into your skills.
   - Reference your memory/patterns/ and memory/examples/ files for consistency.
   - Output should be production-ready, not "good enough."

**Community tip:** The jump from Level 4 to 5 is where Claude Code stops feeling like a tool and starts feeling like a team. The key is building the orchestration layer, not just having more skills.

---

### Level 5 → Level 6: Programmatic Pipelines

**What this unlocks:** Claude Code as a programmable component. Scripts call it, data pipes through it, outputs feed into other systems. No human in the loop for routine tasks.

**Your roadmap:**

1. **Headless mode** (5 minutes)
   - Run Claude without the interactive terminal:
   ```bash
   claude -p "Analyze all files in /src and write a security audit to audit.md"
   ```
   - Pipe data in: `cat data.csv | claude -p "Summarize trends"`
   - JSON output for chaining: `claude -p "List issues" --output-format json`
   - **Important:** Slash commands (like `/lookout`) are interactive-only. In headless mode, describe the task in plain text or pipe the skill's prompt file: `claude -p "$(cat .claude/commands/lookout.md)" --allowedTools "Read,Write,Glob,Grep"`

2. **Build your first automation script** (15 minutes)
   - A shell script that calls Claude Code as part of a pipeline:
   ```bash
   #!/bin/bash
   # Daily briefing generator
   # Note: use -p with a prompt string, NOT with /slash-commands
   claude -p "Read my latest emails and Slack messages, write a morning briefing to briefing.md" \
     --allowedTools "Read,Write,Glob,Grep,mcp__google__gmail_search_messages"
   ```

3. **Chain outputs programmatically** (10 minutes)
   - Use JSON output mode to pipe Claude's output into other tools.
   - Example: Claude analyzes data → outputs JSON → script processes it → sends to API.

4. **Integrate with existing tools** (ongoing)
   - CI/CD pipelines (code review on every PR)
   - Build scripts (generate documentation from code)
   - Data pipelines (transform, analyze, report)

**Community tip:** Level 6 is where most people who do real automation work land. It's the practical ceiling for most use cases. Beyond here, you're building infrastructure.

---

### Level 6 → Level 7: Browser Power

**What this unlocks:** Claude controls a browser. It scrapes websites, takes screenshots, generates PDFs, fills forms, and runs research pipelines that crawl the web and synthesize findings.

**Your roadmap:**

1. **Install browser tools** (5 minutes)
   - Option A: `npm install playwright` in your project + `npx playwright install chromium`
   - Option B: Enable Chrome integration via Claude Code CLI flags (`--browser`)
   - Either path unlocks browser-powered workflows.

2. **Screenshot and PDF generation** (10 minutes)
   - Build skills that create HTML → screenshot to PNG → compile to PDF.
   - Use case: branded decks, carousels, reports, one-pagers.

3. **Web scraping workflows** (15 minutes)
   - Build a `/research [company]` skill that scrapes their website, LinkedIn, news.
   - Claude synthesizes everything into a structured brief.

4. **Research pipelines** (ongoing)
   - Combine browser automation + MCPs: scrape web data, store in Notion, alert via Slack.
   - Build competitive intelligence systems that run on demand.

**Community tip:** This is the level where Claude Code starts replacing paid SaaS tools. Members have canceled Gamma (decks), Canva Pro (design), Superhuman (email) after building equivalent browser-powered workflows.

---

### Level 7 → Level 8: Multi-Agent Operations

**What this unlocks:** Multiple Claude Code instances working in parallel. Each one is a specialist. You're the tech lead coordinating a team of AI agents.

**Your roadmap:**

1. **tmux multi-session setup** (10 minutes)
   ```bash
   tmux new-session -s orchestrator
   # Split panes: Ctrl+B then %
   # Each pane runs: cd /project && claude
   ```
   - One instance researches, another writes, another reviews. Simultaneously.

2. **Define agent roles** (15 minutes)
   - Each agent gets its own context and instructions.
   - Orchestrator: breaks work into tasks, coordinates.
   - Specialists: frontend, backend, research, review, testing.
   - Pass work between agents via shared files in the repo.

3. **VPS deployment** (30 minutes)
   - Move your setup to a cloud server for persistent, always-available agents.
   - SSH + Termius from your phone = Claude Code anywhere.

4. **Coordination patterns** (ongoing)
   - Shared task files that agents read and update.
   - Git branches per agent to avoid conflicts.
   - Orchestrator reviews and merges.

**Community tip:** R moved his entire business to this model. "We've all become endpoint facilitators for our agents. We're context generators, for now." This level requires discipline. Multiple agents without coordination create chaos, not productivity.

---

### Level 8 → Level 9: Always On

**What this unlocks:** Claude Code runs whether you're at your desk or not. Scheduled tasks, automated monitoring, event-driven triggers. It's infrastructure now.

**Your roadmap:**

1. **Scheduled automation** (15 minutes)
   - Cron jobs or launchd services that run Claude on a schedule:
   ```bash
   # Daily morning briefing at 7am (cron)
   0 7 * * * cd /project && claude -p "Generate morning briefing" >> /logs/briefing.log
   ```
   - On macOS, use launchd plist files for more reliable scheduling.
   - Weekly reports, daily digests, periodic audits.
   - **Remember:** headless mode uses `-p` with plain text prompts, not slash commands.

2. **Persistent background agents** (15 minutes)
   - Use pm2 or systemd to keep agents running continuously.
   - Pattern: agent watches a file/queue, processes items as they appear.
   - Log rotation, error handling, restart policies.

3. **Monitoring and alerting** (15 minutes)
   - Claude monitors data sources and alerts you when something needs attention.
   - Example: check competitor pricing daily, alert on changes.

**Community tip:** Level 9 is where the line between "using a tool" and "running an AI system" disappears. Most people don't need this. If your work is project-based, Level 5-7 is the sweet spot. Level 9 is for people running continuous operations.

---

### Level 9 → Level 10: Swarm Architecture

**What this unlocks:** Autonomous execution. Agents that manage other agents. Systems that take a goal and work toward it without human intervention. The edge of what's possible.

**Your roadmap:**

1. **The Ralph Wiggum Loop** (advanced)
   - Give Claude a PRD (product requirements document) and a test suite.
   - It picks a task, implements, runs tests, commits if passing, picks next. Repeat.
   - Safety checklist:
     - Always run in a sandboxed environment
     - Set clear boundaries on what it can modify
     - Review commits before pushing to main
     - Set maximum iteration count
     - Kill switch always accessible

2. **Multi-agent orchestration frameworks**
   - Agent Teams, Gastown, OpenClaw being tested by the community.
   - Pattern: orchestrator agent breaks work into tasks, specialist agents execute, review agent validates.
   - Each agent has its own CLAUDE.md, its own memory, its own skills.

3. **Agent-to-agent communication**
   - Shared file system for task queues and results.
   - Git-based coordination (branches, PRs, merges).
   - Status files that agents read and update.

4. **Always-on assistants**
   - OpenClaw: open source framework running Claude as a persistent assistant via WhatsApp/Telegram.
   - Message it like a colleague. Always available.

**Community tip:** Level 10 is experimental. The community is actively building and testing these patterns. Things break. The value is in the learning. Very few people are here, and those who are spend significant time managing the systems. This is not "set and forget." This is "build, monitor, iterate."

---

## Generate Dashboard

After completing Phase 1 (assessment) and Phase 2 (roadmap), ALWAYS generate an HTML dashboard and open it in the browser. This is not optional. Every `/level-up` run ends with a visual dashboard.

### Instructions

1. Build a single self-contained HTML file using the template below
2. Replace ALL placeholder tokens with actual assessment data
3. Write it to `~/Desktop/level-up-results.html`
4. Open it in the browser (platform-aware: `open` on macOS, `xdg-open` on Linux, `start` on Windows/WSL)
5. Tell the user it's open and print the file path

### Placeholder Tokens

Replace these in the HTML template with real values from your assessment:

- `{{LEVEL_NUMBER}}` — The assessed level (0-10)
- `{{LEVEL_NAME}}` — The level name (e.g. "Browser Commander")
- `{{SUMMARY_TEXT}}` — The "short version" paragraph from Step 1.4
- `{{CAPABILITY_CARDS}}` — HTML for each detected capability (see card format below)
- `{{NEXT_LEVEL_NUMBER}}` — Current level + 1
- `{{NEXT_LEVEL_NAME}}` — Name of the next level
- `{{GAP_EXPLANATION}}` — Plain English explanation of what's missing (from Step 1.4)
- `{{ROADMAP_STEPS}}` — HTML for each roadmap step (see step format below)
- `{{PROGRESS_DOTS}}` — HTML for the 0-10 progress dots (see dot format below)
- `{{LEVELS_TABLE_ROWS}}` — HTML rows for the reference table

### Card Format (for {{CAPABILITY_CARDS}})

Generate one card per detected capability. Categories: CLAUDE.md, MCPs, Skills, Memory, Automation, Browser, Workflows, Templates.

```html
<div class="cap-card">
  <div class="cap-icon">✓</div>
  <div class="cap-title">CLAUDE.MD</div>
  <div class="cap-detail">181 lines, advanced<br>References memory, patterns, workflows</div>
</div>
```

For missing capabilities (levels above the user), use this variant:

```html
<div class="cap-card missing">
  <div class="cap-icon">✗</div>
  <div class="cap-title">HOOKS</div>
  <div class="cap-detail">No hook configurations found<br>settings.json is empty</div>
</div>
```

### Step Format (for {{ROADMAP_STEPS}})

Generate one step per roadmap item from Phase 2:

```html
<div class="step">
  <div class="step-num">1</div>
  <div class="step-body">
    <div class="step-title">Configure hooks</div>
    <div class="step-desc">Your .claude/settings.json is empty. Hooks let you auto-run things before or after Claude acts. Start with a post-edit hook that auto-formats files.</div>
    <div class="step-time">~10 minutes</div>
  </div>
</div>
```

If the roadmap step includes a code example, add it inside step-body:

```html
<pre class="step-code">claude -p "/lookout" --output-format json > ~/briefing.md</pre>
```

### Dot Format (for {{PROGRESS_DOTS}})

Generate 11 dots (0-10). Completed levels get class "done", current level gets "current", future levels get no extra class:

```html
<div class="dot done"><span>0</span></div>
<div class="dot done"><span>1</span></div>
<!-- ... -->
<div class="dot current"><span>7</span></div>
<div class="dot"><span>8</span></div>
<!-- ... -->
<div class="dot"><span>10</span></div>
```

### Levels Table Rows (for {{LEVELS_TABLE_ROWS}})

One row per level. Current level gets class "current-row":

```html
<tr>
  <td class="lvl-num">0</td>
  <td class="lvl-name">Terminal Tourist</td>
  <td class="lvl-desc">Just installed it. Typing prompts like ChatGPT in a terminal.</td>
</tr>
<tr class="current-row">
  <td class="lvl-num">7</td>
  <td class="lvl-name">Browser Commander</td>
  <td class="lvl-desc">Browser control, screenshots, PDF generation, scraping workflows.</td>
</tr>
```

### HTML Template

Write this exact template, replacing all `{{TOKENS}}` with generated content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Level {{LEVEL_NUMBER}} | The 10 Levels of Claude Code</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: #0a0a0a;
    color: #fff;
    font-family: Consolas, 'Courier New', monospace;
    padding: 0;
    min-height: 100vh;
  }

  .container {
    max-width: 960px;
    margin: 0 auto;
    padding: 48px 40px 64px;
  }

  /* Header */
  .top-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 56px;
  }

  .top-bar h1 {
    font-size: 13px;
    font-weight: 400;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: #666;
  }

  .top-bar .brand {
    font-size: 12px;
    color: #555;
    letter-spacing: 1px;
  }

  /* Hero Section */
  .hero {
    display: flex;
    gap: 48px;
    align-items: flex-start;
    margin-bottom: 48px;
  }

  .level-display {
    flex-shrink: 0;
    text-align: center;
    min-width: 160px;
  }

  .level-number {
    font-size: 96px;
    font-weight: 400;
    color: #f59e0b;
    line-height: 1;
    margin-bottom: 8px;
  }

  .level-label {
    font-size: 11px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: #666;
    margin-bottom: 4px;
  }

  .level-name {
    font-size: 16px;
    color: #f59e0b;
    letter-spacing: 1px;
  }

  .summary-box {
    flex: 1;
    border: 1px solid #222;
    padding: 24px;
    color: #ccc;
    font-size: 14px;
    line-height: 1.7;
  }

  /* Progress Dots */
  .progress {
    display: flex;
    justify-content: center;
    gap: 4px;
    margin-bottom: 56px;
    padding: 20px 0;
    border-top: 1px solid #1a1a1a;
    border-bottom: 1px solid #1a1a1a;
  }

  .dot {
    width: 64px;
    text-align: center;
    padding: 10px 0;
    font-size: 12px;
    color: #333;
    position: relative;
  }

  .dot::before {
    content: '';
    display: block;
    width: 10px;
    height: 10px;
    border: 1px solid #333;
    margin: 0 auto 6px;
  }

  .dot.done::before {
    background: #4ade80;
    border-color: #4ade80;
  }

  .dot.done { color: #4ade80; }

  .dot.current::before {
    background: #f59e0b;
    border-color: #f59e0b;
    width: 14px;
    height: 14px;
  }

  .dot.current {
    color: #f59e0b;
    font-weight: 700;
  }

  /* Section Headers */
  .section-label {
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: #555;
    margin-bottom: 20px;
    padding-bottom: 8px;
    border-bottom: 1px solid #1a1a1a;
  }

  /* Capability Cards */
  .capabilities {
    margin-bottom: 56px;
  }

  .cap-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 12px;
  }

  .cap-card {
    border: 1px solid #222;
    padding: 16px;
    background: #111;
  }

  .cap-card.missing {
    border-color: #1a1a1a;
    background: transparent;
    opacity: 0.5;
  }

  .cap-icon {
    font-size: 16px;
    margin-bottom: 8px;
    color: #4ade80;
  }

  .cap-card.missing .cap-icon { color: #555; }

  .cap-title {
    font-size: 12px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: #fff;
    margin-bottom: 6px;
  }

  .cap-card.missing .cap-title { color: #555; }

  .cap-detail {
    font-size: 12px;
    color: #666;
    line-height: 1.5;
  }

  /* Next Level Section */
  .next-level {
    margin-bottom: 56px;
  }

  .next-header {
    font-size: 18px;
    color: #fff;
    margin-bottom: 8px;
  }

  .next-header span { color: #f59e0b; }

  .gap-text {
    color: #999;
    font-size: 14px;
    line-height: 1.7;
    margin-bottom: 24px;
    max-width: 720px;
  }

  /* Roadmap Steps */
  .steps {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .step {
    display: flex;
    gap: 16px;
    border: 1px solid #222;
    padding: 20px;
    background: #111;
  }

  .step-num {
    font-size: 24px;
    color: #f59e0b;
    flex-shrink: 0;
    width: 32px;
  }

  .step-body { flex: 1; }

  .step-title {
    font-size: 14px;
    color: #fff;
    margin-bottom: 6px;
  }

  .step-desc {
    font-size: 13px;
    color: #888;
    line-height: 1.6;
    margin-bottom: 8px;
  }

  .step-time {
    font-size: 11px;
    color: #555;
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  .step-code {
    background: #0a0a0a;
    border: 1px solid #222;
    padding: 12px 16px;
    font-size: 12px;
    color: #f59e0b;
    margin: 8px 0;
    overflow-x: auto;
    white-space: pre;
    font-family: Consolas, 'Courier New', monospace;
  }

  /* Reference Table */
  .reference {
    margin-bottom: 48px;
  }

  .ref-table {
    width: 100%;
    border-collapse: collapse;
  }

  .ref-table th {
    text-align: left;
    color: #555;
    font-size: 11px;
    font-weight: 400;
    text-transform: uppercase;
    letter-spacing: 1px;
    padding: 10px 16px;
    border-bottom: 1px solid #222;
  }

  .ref-table td {
    padding: 10px 16px;
    border-bottom: 1px solid #111;
    font-size: 13px;
  }

  .lvl-num { color: #555; width: 40px; }
  .lvl-name { color: #ccc; width: 180px; }
  .lvl-desc { color: #666; }

  .ref-table .current-row td { color: #f59e0b; }
  .ref-table .current-row .lvl-num { color: #f59e0b; }
  .ref-table .current-row .lvl-name { color: #f59e0b; }
  .ref-table .current-row .lvl-desc { color: #f59e0b; }

  .ref-table .done-row td { color: #4ade80; opacity: 0.5; }
  .ref-table .done-row .lvl-num { color: #4ade80; }

  /* Footer */
  .footer {
    text-align: center;
    padding-top: 32px;
    border-top: 1px solid #1a1a1a;
    color: #333;
    font-size: 12px;
    letter-spacing: 1px;
  }

  .footer a {
    color: #555;
    text-decoration: none;
  }

  .footer a:hover { color: #f59e0b; }

  .footer .cta {
    color: #666;
    margin-top: 8px;
    font-size: 12px;
  }
</style>
</head>
<body>
<div class="container">

  <div class="top-bar">
    <h1>The 10 Levels of Claude Code</h1>
    <div class="brand">thegenaicircle.com</div>
  </div>

  <div class="hero">
    <div class="level-display">
      <div class="level-label">Your Level</div>
      <div class="level-number">{{LEVEL_NUMBER}}</div>
      <div class="level-name">{{LEVEL_NAME}}</div>
    </div>
    <div class="summary-box">{{SUMMARY_TEXT}}</div>
  </div>

  <div class="progress">
    {{PROGRESS_DOTS}}
  </div>

  <div class="capabilities">
    <div class="section-label">What You Have</div>
    <div class="cap-grid">
      {{CAPABILITY_CARDS}}
    </div>
  </div>

  <div class="next-level">
    <div class="section-label">Your Roadmap</div>
    <div class="next-header">Level <span>{{NEXT_LEVEL_NUMBER}}</span>: {{NEXT_LEVEL_NAME}}</div>
    <div class="gap-text">{{GAP_EXPLANATION}}</div>
    <div class="steps">
      {{ROADMAP_STEPS}}
    </div>
  </div>

  <div class="reference">
    <div class="section-label">All 10 Levels</div>
    <table class="ref-table">
      <thead>
        <tr>
          <th>Level</th>
          <th>Name</th>
          <th>What It Means</th>
        </tr>
      </thead>
      <tbody>
        {{LEVELS_TABLE_ROWS}}
      </tbody>
    </table>
  </div>

  <div class="footer">
    <a href="https://thegenaicircle.com">thegenaicircle.com</a> / <a href="https://thegenaicircle.com">/level-up</a>
    <div class="cta">Run /level-up again when you're ready for the next step.</div>
  </div>

</div>
</body>
</html>
```

### After Writing the HTML

1. Write the completed HTML (with all tokens replaced) to `~/Desktop/level-up-results.html`
2. Open it: run `open ~/Desktop/level-up-results.html` via Bash
3. Tell the user: "Your level-up dashboard is open in the browser."

---

## Phase 3: Build It Now

**Ask the user:** "Want me to build the first step of your roadmap right now?"

If yes, execute the matching build step below. If no, end with the roadmap summary.

---

### Build: CLAUDE.md Starter (for Level 0)

Create a CLAUDE.md in the current project root using the context questions:

```markdown
# [Project/Business Name]

## About
- **Role:** [from Q1 answer]
- **Main work:** [from Q1 answer]
- **Key tools:** [detected from environment]

## Communication Style
- [Infer from conversation]
- Be direct and actionable
- Use plain language

## Project Context
[Based on files and structure detected]

## Output Rules
- [Address their biggest friction from Q2]
- Always be specific, not vague
- Include examples when explaining concepts

## What I Want to Automate
- [ ] [From Q3 answer]
```

Adapt this template. Make it specific to the user. Don't use it verbatim.

---

### Build: First MCP Setup (for Level 1)

Based on Q1, recommend and configure their first MCP:

1. Determine the best MCP for their use case
2. Create or update `.mcp.json`
3. Walk through authentication
4. Test with a real query

---

### Build: First Skill (for Level 2)

Based on Q3 (what they'd automate):

1. Create `.claude/commands/` directory
2. Write a skill .md file for their specific use case
3. Test it by running the command
4. Suggest 2-3 more skills they should build next

---

### Build: Memory Architecture (for Level 3-4)

1. Create the `memory/` directory structure
2. Seed with initial files based on their work
3. Update CLAUDE.md to reference the memory structure
4. Show how the feedback loop works

---

### Build: Multi-Phase Skill Upgrade (for Level 4-5)

1. Take their most-used existing skill
2. Rewrite it with phases, approval gates, and sub-agent calls
3. Add references to memory/patterns/ for consistency
4. Test the upgraded version

---

### Build: First Automation Script (for Level 5-6)

1. Create a shell script that calls `claude -p` for a routine task
2. Test it end-to-end
3. Show how to schedule with cron or run on demand

---

### Build: Advanced Optimization (for Level 6+)

For power users:
1. **Context budget audit:** How much context consumed on startup? Optimize.
2. **Skill architecture review:** Which skills could chain? Build connections.
3. **Memory file health check:** Stale files? Outdated patterns? Clean up.
4. **MCP health check:** All configured MCPs actually working? Test each one.
5. **Pipeline review:** Where could headless mode replace interactive sessions?

---

## Community Wisdom (from GenAI Circle)

**On context windows:**
Break tasks into smaller chunks. The "auto-compact" (the community calls it "the lobotomy") loses important context. Better to do 5 focused sessions than 1 marathon.

**On getting started:**
Your CLAUDE.md is 80% of the early value. Spend 30 minutes on it before anything else. Claude can only be as good as the context you give it.

**On MCP management:**
Fewer is better. Tool search helps manage context (dropped startup from 51% to 13%), but don't load MCPs you don't use daily.

**On replacing SaaS:**
Track what you're paying for monthly. Try replacing one tool per week. Members have canceled Gamma, Canva Pro, Superhuman, Clay after building equivalent workflows.

**On building your knowledge system:**
The pattern is Claude Code + MCP + markdown memory files + git. Your system gets smarter with every project. The first month feels slow. By month two, the compounding kicks in.

**On autonomous work:**
Start supervised. Remove guardrails gradually. The members who trust too fast burn tokens on bad output. The members who never trust miss the productivity multiplier.

**On the levels:**
There's no shame in being at Level 1. The jump from 1 to 3 takes a weekend. The jump from 3 to 5 takes a few weeks of daily use. Most people find their sweet spot between 4 and 6. Going higher means running infrastructure, and that's only worth it if your work demands it.

---

## After Running This

Come back and run `/level-up` again whenever you're ready for the next step. The assessment updates based on your actual environment.

---

**Version:** 3.0.0
**Created by the GenAI Circle community** (thegenaicircle.com)
