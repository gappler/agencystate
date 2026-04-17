---
title: Agency State — Cohort Curriculum
date: 2026-04-16
version: 2.0
status: active
---

# Agency State — Cohort Curriculum

## Format

**Live online cohort.** 8–12 participants. Four 2-hour sessions across two weeks, plus office hours on the Wednesday of each week. Prework required before Session 1.

**Schedule:**
- **Week 1:** Monday (Session 1, 10am ET), Tuesday (Session 2, 10am ET), Wednesday (office hours)
- **Between-session build window:** Tuesday evening through Sunday — five days to build something independently
- **Week 2:** Monday (Session 3, 10am ET), Tuesday (Session 4 — demo day, 10am ET), Wednesday (office hours)

**Price:**
- **Cohort 1 (intro):** $500 per seat
- **Future cohorts:** $899–$1,200 per seat

**Scheduling:** The compressed two-week format is the point — it fits inside a single sprint or planning cycle, and the back-to-back Mon/Tue sessions force the methodology to land before participants drift. Cohorts can run on staggered calendars (e.g., Cohort A starts the first Monday of the month, Cohort B the third Monday). Office hours can be shared across overlapping cohorts on the Wednesday slot if needed.

---

## Prework (completed before Session 1)

Participants complete this independently using **regular Claude chat** (claude.ai) — not Claude Code. The terminal setup is intentionally moved into Session 1 so that prework filters for thinking, not tooling.

**Foundation building (in Claude chat):**
- Choose a fictional or real company to use throughout the intensive (Agency State provides a starter prompt)
- Build a brand/business definition — company overview, product or service definition, audience profiles, brand voice, objectives. The output is a single document the participant will bring to Session 1.
- Generate 6–12 months of synthetic historical data relevant to their business context — performance data, customer records, campaign results, whatever fits. Save as CSV or markdown tables.

**Deliverable at Session 1:** Every participant arrives with (a) a brand/business definition document and (b) a synthetic data set. Both are saved locally and ready to drop into a project folder once Claude Code is installed in Session 1.

**Prework filters intentionally:** If someone can't produce a coherent business definition using Claude chat, they're not ready for the intensive. The bar is conversational fluency with a frontier model — if that bar isn't met, the cohort isn't the right starting point.

---

## The Knowledge Base — A Through-Line

A core thread runs through all four sessions: **the knowledge base.** This is the set of files in the participant's project that describe their business, voice, audience, and rules. Claude Code reads from it on every build.

- **Session 1:** You build the foundation. The prework brand definition becomes the seed of your knowledge base.
- **Session 2:** You see the payoff — the tools you build are customized to your business *because* they read from your knowledge base.
- **Session 3:** You add to it — brand voice rules, content guidelines, deeper audience data, output preferences.
- **Session 4:** You show how your knowledge base shaped what you built independently — the demos surface the principle.

**The principle: context compounds.** The more your knowledge base grows, the better everything Claude Code builds for you — and the less prompting you have to do.

---

## Session 1: Setup, Foundation, and First Build (2 hours)

*Week 1, Monday, 10am ET*

### Objectives
- Get every participant into a working Claude Code environment
- Seed the knowledge base from prework
- Build the first tool and learn the understand → build → reflect cycle

### Flow

**Guided setup (30 min)**
- Install Claude Code, confirm terminal access
- Create the project folder
- Create a CLAUDE.md file with project rules (process logging, commit after each tool, file naming conventions)
- Drop the prework brand definition and synthetic data into the project — this is now the seed of the participant's knowledge base
- Facilitator screen-shares each step; co-facilitator (if available) helps anyone stuck without slowing the group
- **If your install isn't working by the end of setup:** stay on for Wednesday office hours and we'll get you sorted before Session 2. A failed Node version or terminal config shouldn't derail your cohort — we'll fix it 1:1.

**Quick share (5 min)**
- One sentence each: who's the company, what's the data
- Reinforces that the methodology is industry-agnostic — same toolchain, different inputs

**Understand (10 min)**
- What are we about to build and why? What inputs does it read? What should the output look like?
- Framework for writing prompts: what are you building, what data does it read, what should the user see, what format should it take?
- Participants write their own first prompt before seeing the reference

**Build (30 min)**
- Build a performance dashboard from the participant's synthetic data
- Facilitator monitors progress, drops anyone stuck into a breakout

**Reflect (15 min)**
- What did Claude Code produce? Was it right? Did it pull from your knowledge base correctly?
- Cross-compare a few outputs — different data, same methodology, different results
- What would you change about your prompt?

**Second build (20 min)**
- Build a written report generator that reads the same data and produces a narrative interpretation
- Demonstrates sequential building — the report depends on the dashboard's data
- Participants modify the reference prompt to fit their business context

**Wrap and preview (10 min)**
- What we built: two tools, one feeding the other, both reading from your knowledge base
- Tomorrow we go deeper — planning tools and decision tools

---

## Session 2: Planning, Decision Tools, and the Knowledge Base Payoff (2 hours)

*Week 1, Tuesday, 10am ET*

### Objectives
- Build tools that help make decisions, not just display data
- See how the knowledge base customizes outputs without you re-prompting every time
- Set up the between-session build with confidence

### Flow

**Open (10 min)**
- Quick recap of yesterday — what landed, what didn't
- Frame the session: yesterday's tools displayed history. Today's tools model decisions.

**Understand (15 min)**
- What makes a planning tool different from a reporting tool? It takes inputs and models outcomes, not just displays history.
- Framework: what decisions does your team make repeatedly that could be modeled?
- Participants write their own prompt for a planning tool relevant to their business

**Build (35 min)**
- Build a budget allocator, scenario modeler, capacity planner, or roadmap prioritizer — participant chooses based on their business
- Less hand-holding than Session 1 — participants are expected to modify the reference prompt
- Facilitator circulates, helps with specific issues

**Group review (15 min)**
- 2–3 participants share their screen and walk through what they built
- Group feedback: what's working, what's missing, what would you change
- Facilitator points out where the knowledge base is doing the work — "notice your tool used your audience profiles without you re-pasting them"

**Second build (25 min)**
- Build a tool that takes the planning tool's output as input — e.g., the budget allocator's output feeds a campaign plan generator
- Demonstrates the compounding effect: each tool makes the next one smarter
- Reinforces the knowledge base principle — the same brand definition shapes every tool

**Set up the between-session build (15 min)**
- Identify the single most time-consuming recurring task in the participant's actual job — the thing they'd genuinely build a tool for
- Frame it: this is not practice. You're building a portfolio asset for your real work.
- Five-day window: Tuesday evening through Sunday. Office hours Wednesday for stuck-points.
- Bring it to Session 3 ready to discuss what you built and where you got stuck

### Between-session build (Tue evening – Sunday)

**This is your build, not homework.** The work is real: identify a recurring task in your job, build a tool that addresses it, and bring it back. The knowledge base you've seeded with your business definition powers it. The portfolio asset you produce belongs to you.

- **Required, not optional.** Sessions 3 and 4 assume you've done it.
- **Stuck:** Wednesday office hours. Slack channel between then and Sunday.
- **Output:** a working tool plus a few notes on what worked, what broke, and what you'd change. The notes matter as much as the tool.

---

## Session 3: Making Your Tools Smarter (2 hours)

*Week 2, Monday, 10am ET*

### Objectives
- Bring the between-session builds into the room and surface lessons
- Add brand voice rules, content guidelines, and richer audience data to the knowledge base
- See how a deeper knowledge base produces sharper outputs without more prompting

### Flow

**Build review (20 min)**
- Each participant shares in 90 seconds: what they built, what surprised them, where they got stuck
- Facilitator captures common patterns — same kinds of breakage tend to repeat
- Group sees the range — different jobs, same methodology, different outputs

**Understand (15 min)**
- The knowledge base is doing more work than you've used so far. The leap is going from "facts about my business" to "rules my outputs follow."
- What goes in: brand voice rules, terminology dictionaries, audience personas with deeper detail, output format preferences, things to never say
- Framework: what does your team's published work assume that nobody writes down?

**Build the voice and rules layer (30 min)**
- Build out brand voice rules — examples of how to phrase things, examples of how *not* to phrase things, terminology rules
- Add audience persona depth — what each persona cares about, what they ignore, what they'd find condescending
- Add output rules — formats, lengths, banned phrases, required disclaimers if applicable
- These get saved into the knowledge base and committed

**Apply (30 min)**
- Re-run one of the participant's existing tools (the dashboard, the report generator, or their independent build) with the richer knowledge base in place
- Compare before/after — same prompt, same data, sharper output, less manual editing
- Optional: build a content engine, email sequence generator, or brief builder that leans heavily on the new voice rules

**Wrap and prepare for demo day (15 min)**
- Tomorrow is demo day — everyone presents what they built in the between-session window
- Tonight: polish the demo, prepare a short walkthrough (3 min), think about what the knowledge base did for you that you didn't have to ask for
- Facilitator hands out a one-page demo prep sheet

---

## Session 4: Demo Day (2 hours)

*Week 2, Tuesday, 10am ET*

### Objectives
- Every participant presents the tool they built independently
- Surface how the knowledge base shaped the build
- Live teardowns from the facilitator show what to refine next

### Flow

**Open and framing (5 min)**
- The point of demo day: not to perform, but to show the work and learn from each other's choices
- Reminder: this isn't a test. The tool is yours, and the feedback is to make it sharper.

**Demos with feedback (60 min)**
- Each participant gets ~6 minutes: 3 minutes to demo, 3 minutes for group feedback
- Demos cover: the problem they were solving, what they built, what role the knowledge base played, what surprised them
- Group feedback is structured — what's working, what's missing, what would make it sharper

**Live code reviews and strategic teardowns (30 min)**
- Facilitator picks 2–3 builds (selected for teaching value, not quality) and walks through them live
- Code review: what's well-structured, what could be cleaner, what's a future maintenance trap
- Strategic teardown: where this tool fits in the participant's actual workflow, what to add next, what to never bother building
- Group sees the moves an experienced builder would make next

**What's next and close (15 min)**
- What you built across two weeks: a working knowledge base, several tools, and one portfolio asset for your actual job
- How to keep going: the project folder, the process logs, the session recordings, and the Slack channel all stay live
- Community: shared Slack channel persists, monthly check-in for graduates
- Advanced cohort preview: custom skills, agents, MCP server connections, API integrations — for graduates who want to go further
- Celebration: this is graduation. Acknowledge it.

**Optional close (10 min)**
- Open Q&A if time, retro questions on the curriculum itself, photo if the cohort is up for it

---

## Between-Session Builds — The One Window

Unlike a multi-week course, this format has **one independent build window**: Tuesday evening of Week 1 through Sunday. Five days. It's the only stretch where participants build solo, and the deliverable is the centerpiece of demo day.

**The framing matters:** these are not practice exercises. Participants are building portfolio assets for their actual job — tools they'll keep using after the cohort ends. The knowledge base they've seeded in Sessions 1 and 2 powers the build.

**What's expected:**
- A working tool that addresses a real recurring task in the participant's job
- Notes on what worked, what broke, and what they'd change
- Willingness to demo it on Tuesday of Week 2

**Support during the window:**
- Wednesday office hours of Week 1 (the day after Session 2)
- Slack channel for asynchronous questions
- Reference prompts and session recordings available throughout

---

## Between-Session Support

### Office hours
- 30–60 minute optional drop-in on the **Wednesday of each week** (after Session 2 in Week 1, after Session 4 in Week 2)
- Open to anyone stuck, confused, or wanting to go deeper
- Week 1's Wednesday office hours is the most important — it's the launch pad for the between-session build, and the safety net for anyone whose Claude Code install didn't fully work in Session 1
- Week 2's Wednesday office hours is for graduates — wrap-up questions, what to build next, how to bring this back to a team

### Breakout rooms (during sessions)
- If a participant hits a wall during a build phase, drop them into a breakout
- Facilitator or co-facilitator helps them catch up while the main group continues
- Session 1's setup phase is the most likely moment for this — the Claude Code install can hit edge cases on individual machines

### Shared channel (Slack or similar)
- Created at Session 1, persists after the cohort ends
- Most active during the five-day between-session build window
- Participants share wins, ask questions, post screenshots of tools they're building
- Peer support becomes the primary value over time

---

## Materials Provided

### Before prework
- A prework guide that explains the brand definition and synthetic data steps in Claude chat (no terminal, no install)
- Brand/business definition prompt template (used inside Claude chat)
- Synthetic data prompt template (used inside Claude chat)

### At Session 1
- Claude Code installation walkthrough (terminal commands, troubleshooting common issues by OS)
- CLAUDE.md template with project rules
- Reference prompts for the dashboard and report generator builds

### Throughout the cohort
- Reference prompts for each build exercise
- The prompt-writing framework: what are you building, what data does it read, what should the user see, what format
- Session recordings (typically posted same-day for the back-to-back format)

### After the cohort
- All reference prompts and frameworks
- Session recordings
- Process logs and tutorials from the facilitator's builds
- Access to the persistent Slack channel
- Links to the four Agency State demo suites as reference implementations
- A demo-day recap doc with the facilitator's strategic teardown notes

---

## On-Demand Adaptation

The same curriculum works as an on-demand course with modifications to fit the compressed two-week structure:

**Each module mirrors a session and has three parts:**
1. **Watch** — short video showing the build with narration explaining the thinking behind the prompt
2. **Build** — the student gets the prompt and data files, uses as-is or modifies for their own context
3. **Explore** — challenges that push beyond copying: modify the tool, change the inputs, build a variation for their own use case

**The independent build phase is preserved:** between Modules 2 and 3, students take a five-day pause to build something for their actual job. Module 4 in the on-demand version is a recorded demo-day walkthrough plus written teardowns of submitted builds.

**What's lost without live interaction:**
- Peer learning from seeing other participants' builds
- Real-time troubleshooting during the Claude Code setup phase (Module 1's biggest risk)
- Accountability to show up prepared
- The live demo-day energy and facilitator teardowns

**What compensates:**
- Monthly live Q&A session for all on-demand buyers (no additional cost, creates community)
- Discussion forum or Slack channel for peer support
- Built-in pause points: "Before watching the next section, write your own prompt. Then compare it to mine."
- "What went wrong" troubleshooting sections for common Claude Code install issues
- Optional async demo submission with written facilitator feedback

**Price:** $297–$497 for on-demand access
**Upsell:** On-demand buyers can apply their purchase price toward a live cohort seat

---

## Future: Advanced Cohort

Not built yet. Offered when demand from foundational cohort graduates supports it.

**Topics:**
- Custom Claude Code skills — building reusable skill files
- Sub-agents — dispatching parallel work
- MCP server connections — connecting to CRMs, analytics platforms, project management tools
- API integrations — pulling live data from external sources
- Automated workflows — scheduled runs, triggered actions
- Security and governance — what to review before deploying AI-built tools

**Prerequisite:** Completion of the foundational cohort or demonstrated equivalent experience.

**Price:** $2,000–$2,500 per seat.

---

## Facilitator Notes

### What to watch for
- Participants who copy prompts without reading them — pause and ask "what does this prompt tell Claude Code to do?"
- Participants who get a working tool and want to move on without understanding why it works — the reflect phase matters
- One participant dominating the demo or feedback rounds — rotate deliberately
- Technical issues in Session 1 setup consuming group time — move to breakout immediately, don't debug in front of everyone
- Participants who treat the between-session build as practice rather than real work — reframe early: this is a portfolio asset for your actual job, not a homework exercise
- Participants who arrive at Session 3 having not done the between-session build — there's no graceful recovery in a two-week format. Address it directly: they can still get value from Sessions 3 and 4, but they should know the cohort assumes the build was done.

### What makes a great session
- Participants modifying prompts on their own and getting different (sometimes better) results
- Participants helping each other debug
- The "wait, I could build that for my team" moment — usually happens in Session 2 when the knowledge base starts paying off
- Participants asking questions about problems the curriculum doesn't cover — means they're thinking beyond the exercises
- Demo day presentations that solve real recurring tasks the participant actually has — that's the graduation moment
- A demo where a participant says "I didn't have to re-paste my brand voice — it just used it" — the knowledge base concept landed

### What to avoid
- Reading prompts aloud instead of building
- Over-explaining Claude Code internals (skills, agents, sub-agents) — participants learn these organically through use, and the advanced cohort covers them deliberately
- Trying to cover too much in one session — depth beats breadth, especially in the back-to-back Mon/Tue format where participants don't have time to digest between sessions
- Promising that Claude Code will always produce perfect output — it won't, and the ability to evaluate and iterate is the real skill
- Letting demo day turn into a performance — the point is feedback and teardowns, not polish theater
- Skipping the strategic teardown in Session 4 to fit more demos in — the teardowns are where the next-step thinking happens
