# How the AI Design Team Works

## The Setup

I have 10 AI agents, each named after a legendary designer. Each one specializes in a different area:

- **Don Norman** — Usability and user psychology
- **Jony Ive** — Mobile and responsive design
- **Dieter Rams** — Trust and honest design
- **Massimo Vignelli** — Visual hierarchy and search
- **Charles Eames** — Design systems and components
- **Milton Glaser** — Copy and brand voice
- **Paula Scher** — Host acquisition and marketing
- **Josef Müller-Brockmann** — Design consistency
- **Luke Wroblewski** — Conversion and forms
- **Saul Bass** — Hero sections and first impressions

Each agent has 3 files:
- `agent.md` — Their personality and expertise
- `memory.md` — What they've learned from past sessions
- `prompt.md` — Their current task

## How I Run It

### Step 1: The Orchestrator Creates Prompts

I start by telling the orchestrator what I want. For example:

> "Create Comet testing prompts for the whole team. Each agent should analyze Split Lease from their perspective and suggest 6 automated tests."

The orchestrator then writes a `prompt.md` file for each agent with specific instructions.

### Step 2: Trigger Each Agent

I go to each agent folder and say:

> "read your prompt.md"

The agent reads its personality file, checks its memory, then executes the task. It saves results to a `runs/` folder organized by date.

### Step 3: Collect Results

Each agent produces:
- **Reports** (markdown) — Analysis, findings, recommendations
- **Mockups** (HTML) — Visual prototypes, component demos
- **Prompts** (for Comet) — Automated testing instructions

### Step 4: Generate the Summary Report

Once all agents finish, I compile the results into an HTML report that showcases what each agent produced.

## Example: Run 003 (Comet Integration)

Here's what actually happened:

1. **I asked the orchestrator** to have each agent create Comet prompts (Comet is an AI browser that can test websites automatically)

2. **The orchestrator wrote 10 prompt.md files**, one per agent:
   - Don Norman got: "Create 6 prompts to test the proposal flow"
   - Jony Ive got: "Create 6 prompts to test mobile viewports"
   - Dieter Rams got: "Create 6 prompts to verify trust claims"
   - etc.

3. **Each agent executed their task** and saved results to `runs/run-003--2026-01-31/[agent-name]/reports/`

4. **Cross-agent collaboration**: Massimo created a graphics strategy (34 specs), then Charles produced all 34 graphics using his Empty State approach

5. **Final output**: 54 Comet prompts + collaboration examples + HTML report

## The Comet Part

Comet is Perplexity's AI browser. It can:
- Navigate to URLs
- Click buttons
- Fill forms
- Take screenshots
- Verify things loaded correctly

So instead of manually testing "does the proposal flow work?", I can give Comet a prompt like:

```
TASK: Test proposal submission
URL: splitlease.com/listing/test-123
STEPS:
1. Click "Request to Book"
2. Select Monday and Wednesday
3. Fill form with test data
4. Submit
VERIFY: Confirmation modal appears
```

Each agent creates prompts for their domain. Don Norman tests usability flows. Jony Ive tests at different screen sizes. Dieter Rams checks if trust badges actually load.

## Tools

- **Claude Code** (Opus 4.5) — Runs the agents
- **Markdown files** — Agent definitions, prompts, memory
- **HTML/CSS** — Mockup output
- **Perplexity Comet** — Automated browser testing
- **GitHub** — Version control for reports

## Folder Structure

```
AI Team/
├── agents/
│   ├── don-norman/
│   │   ├── agent.md      ← personality
│   │   ├── memory.md     ← session logs
│   │   └── prompt.md     ← current task
│   ├── jony-ive/
│   └── ... (10 agents)
│
├── runs/
│   ├── run-001--2026-01-29/
│   ├── run-002--2026-01-30/
│   └── run-003--2026-01-31/
│       ├── _manifest.md  ← what each agent was assigned
│       └── don-norman/
│           └── reports/
│               └── comet-prompts.md
│
└── orchestrator/
    └── agent.md          ← coordinates everything
```

## That's It

1. Tell orchestrator what you want
2. Orchestrator writes prompts for each agent
3. Trigger agents one by one
4. Collect results into a report

The agents remember what they learned, build on each other's work, and produce consistent output because they each have a defined personality and expertise area.
