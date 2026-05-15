# 🐦‍⬛ Copilot Agent Workshop — Hands-On

You're a RevOps analyst. Your CRO just slid into your DMs: *"Quick pipeline read in 10 min?"*

No pressure. Let's see what agent mode can do.

## The dataset

`sales_pipeline.csv` — ~80 opportunities, with columns:

| Column | What it is |
|---|---|
| `opportunity_id` | Unique opp ID |
| `account_name` | Customer |
| `amount_usd` | Deal size in USD |
| `stage` | Discovery / Qualification / Proposal / Negotiation / Closed Won / Closed Lost |
| `close_date` | Expected or actual close |
| `created_date` | When the opp was opened |
| `owner` | Sales rep |
| `region` | NAMER / EMEA / APAC / LATAM |
| `product` | Enterprise / Team / Pro |
| `industry` | Customer industry |

## How to run this

1. Open Copilot Chat (sidebar icon or `Cmd+Ctrl+I` / `Ctrl+Alt+I`)
2. **Set the mode dropdown to `Agent`** at the top of the chat panel
3. Paste the prompts below — one at a time
4. When the agent proposes file changes or wants to run commands, click **Keep / Continue**

The whole point: **you do not write a single line of Python or HTML.** The agent does. You describe outcomes.

---

## 🟢 Prompt 1 — Get the lay of the land

```
Read sales_pipeline.csv and give me a short briefing: how many rows, total
pipeline value, breakdown by stage, and anything that looks weird or worth
flagging.
```

The agent will read the file and summarize. Notice it didn't need you to write a line of code.

## 🟡 Prompt 2 — Have the agent build the analyzer + dashboard

```
Write a Python script called analyze.py that:

1. Loads sales_pipeline.csv
2. Computes: total pipeline, pipeline by stage, pipeline by region, top 10
   accounts by amount, top 5 reps by Closed Won, and weighted pipeline by
   region (Discovery 10%, Qualification 25%, Proposal 50%, Negotiation 75%,
   Closed Won 100%, Closed Lost 0%)
3. Generates a single self-contained HTML file called dashboard.html with
   interactive charts for each of those — clean, modern styling, all assets
   inline or via CDN.

Then run the script and open dashboard.html.
```

The agent will write `analyze.py`, run it, and produce `dashboard.html`. Open it from the file explorer — in Codespaces, right-click → **Open with Live Preview** (or drag it into a browser if you're local).

## 🟠 Prompt 3 — Iterate

Pick one — whichever you'd actually want:

```
The dashboard looks fine but the stage chart is hard to read. Reorder the
stages logically (Discovery → Closed Won), use a colorblind-friendly palette,
and add the deal count next to each amount.
```

```
Add a new section to the dashboard: a table of any open opportunities (not
Closed Won/Lost) with a close date in the past. Sort by how overdue they
are. Highlight rows over 30 days late in red.
```

```
Add a forecast section to the dashboard: based on the weighted pipeline and
the average sales cycle in the data, what should we expect to close next
quarter?
```

---

## 🚀 Stretch — if you're flying

- *"Add a filter at the top of the dashboard so I can slice by region."*
- *"Theme the whole dashboard in dark mode."*
- *"Export the analysis as a one-page executive summary in markdown."*

---

## 🎉 When you're done

Drop a screenshot of your dashboard (or favorite finding) in **[#rev-strategy-planning](https://github-grid.enterprise.slack.com/archives/C0AK9GN4RNF)**. Bonus points for the weirdest thing the agent did.

---

### Tips while you're prompting

- **Be specific about output.** "Save as `dashboard.html`" beats "show me something nice."
- **One ask per prompt.** Agents handle one clear task better than five tangled ones.
- **If it goes sideways**, just say `undo that and try again with [different approach]`. Iteration is the whole skill.
- **Let it run.** Agent mode will ask permission to run commands — click Continue. It won't break anything in your Codespace.
