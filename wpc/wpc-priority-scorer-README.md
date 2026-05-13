# WPC Priority Scorer — Skill for Claude Cowork

Score and prioritize every project in your portfolio using the **Weighted Priority Calculator (WPC)**. Upload a project CSV from any tool — Kantata, Asana, Monday.com, Teamwork, Harvest, or a custom spreadsheet — and Claude scores each project across six factors and delivers a color-coded Excel priority matrix.

---

## What It Does

For every project in your CSV, Claude scores six factors on a 1–5 scale:

| Factor | What it measures | How it's scored |
|---|---|---|
| **Industry** | Prestige and strategic value of the client's sector | Claude infers from client name/type |
| **Relationship** | Depth and tenure of the client relationship | Derived from project count + total budget in your data |
| **Stakeholder Complexity** | Number of approvers and political layers | Inferred from client type (universities = high, solo businesses = low) |
| **Budget Score** | Contracted project fee | Directly from your data |
| **Timeline** | Urgency based on status and due date | Directly from your data |
| **Creative Impact** | Strategic significance of the project type | Derived from project type/tags |

**WPC Formula:** `WPC = Σ(factor × weight) / Σ(weights)` — defaults to ÷6, range 1–5.

The output Excel file has three tabs:
- **WPC Priority Scores** — all projects sorted high → low, color-coded, with Eisenhower quadrant labels
- **Legend & Scoring Guide** — formula reference and all scoring criteria
- **Summary** — count and % by priority tier

---

## Priority Bands

| Color | Score | What it means |
|---|---|---|
| 🔴 Red | 4.0 – 5.0 | **High** — act now |
| 🟡 Yellow | 3.0 – 3.99 | **Moderate** — schedule it |
| 🟢 Green | 1.0 – 2.99 | **Low** — monitor |

---

## Eisenhower Quadrants

Each project gets one of four quadrant labels based on urgency and importance:

- **DO FIRST** — urgent and important
- **SCHEDULE** — important, not urgent
- **DELEGATE** — urgent, not important
- **DEPRIORITIZE** — neither

---

## How to Use It

1. Export your project list as a CSV from your PM tool (Kantata, Asana, Monday.com, etc.)
2. Upload the CSV to Claude with a message like:
   - *"Score my projects"*
   - *"Build me a priority matrix from this CSV"*
   - *"Which of these projects should I focus on?"*
3. Claude maps your columns, analyzes the portfolio, asks if you want to adjust any factor weights, then runs the scorer
4. Download your color-coded Excel file

---

## Adjusting Weights

By default all six factors count equally. Before scoring, Claude will ask if you want to adjust. You can say things like:

- *"Weight Budget 2x"*
- *"Timeline is most important"*
- *"Double the Budget and Timeline weights"*

The formula normalizes automatically, so the 1–5 scale stays intact no matter what weights you choose.

---

## CSV Requirements

The skill works with any CSV that has columns for project name, status, budget, and due date. Common exports that work out of the box:

- **Kantata / Mavenlink** — standard project export
- **Asana** — task or project export
- **Monday.com** — board export
- **Teamwork** — project list export
- **Harvest** — projects export
- **Custom spreadsheets** — any CSV with recognizable column names

If a client column doesn't exist, Claude extracts the client code from the project name prefix (e.g., `26-KSU Brand Campaign` → `KSU`).

---

## Installation

1. Download `wpc-priority-scorer.skill`
2. Open Claude Cowork
3. Go to **Settings → Skills → Install from file**
4. Select the `.skill` file

The skill is now available in any Cowork session.

---

## Files Included

```
wpc-priority-scorer/
├── SKILL.md                        # Skill instructions Claude follows
├── scripts/
│   └── generate_wpc_excel.py       # Excel generator script
└── references/
    └── scoring_guide.md            # Full scoring criteria for all 6 factors
```

---

*Built for agencies and project-based teams who want a fast, repeatable way to decide where to focus.*
