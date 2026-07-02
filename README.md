# FlowDraft

**Convert any business process description into a complete AI agent workflow spec.**

> 82% of SMBs bought AI tools. 8.8% have them running. FlowDraft closes that gap.

---

## What it does

Paste 3 sentences describing how your team handles something today. FlowDraft calls Gemini 2.5-flash and returns a complete blueprint:

- **Trigger** — what kicks off the workflow
- **Tools needed** — specific apps with their purpose
- **Step-by-step workflow** — each action, which tool, with decision branches where needed
- **Human checkpoints** — where approval or review is genuinely required
- **Cost + time estimate** — realistic for SMB budgets
- **Quick wins** — what to automate this week, no coding required

## Why it exists

The gap between "we use AI tools" and "we have AI running in production" isn't a technology problem. It's a translation problem. SMB owners know their processes but can't translate them into structured agent specs.

FlowDraft does the translation.

## Live demo

→ [flowdraft.github.io/flowdraft](https://rlasaf12.github.io/flowdraft) _(GitHub Pages)_

## Setup

1. Get a [Gemini API key](https://aistudio.google.com/apikey) (free tier works)
2. Open `index.html` in any browser
3. Click **API Key** in the top right and paste your key
4. Describe your process. Hit Convert.

**No backend. No database. Your API key stays in your browser's localStorage — never sent anywhere except directly to Google's API.**

## Tech

- Pure HTML + Tailwind CDN (single file, zero dependencies)
- Gemini 2.5-flash via REST API
- Structured JSON output parsed and rendered as interactive cards

## Example output

Input:
> _"When a customer emails a complaint, we manually check their order in a spreadsheet, sometimes call them, then write a reply. Refunds over $100 need manager approval. 45 min per complaint, 15-20 per week."_

Output:
```json
{
  "workflow_name": "Customer Complaint Resolution",
  "trigger": { "type": "email", "description": "New email arrives in support inbox" },
  "tools_needed": [
    { "name": "Gmail", "purpose": "Receive and send emails", "example": "Gmail" },
    { "name": "Google Sheets", "purpose": "Order history lookup", "example": "Google Sheets" },
    { "name": "Make.com", "purpose": "Workflow orchestration", "example": "Make.com" }
  ],
  "steps": [...],
  "human_checkpoints": [{ "at_step": 4, "reason": "Refund over $100 requires manager approval", "estimated_time": "~2 min" }],
  "estimated_setup": { "tools_cost_monthly": "$30-50/mo", "setup_hours": "4-6 hrs", "automation_savings": "10 hrs/week" },
  "quick_wins": ["Connect Gmail to Make.com and auto-tag complaint emails", "..."]
}
```

## Built by

Ben (nightly prototype builder) — part of RLASAF12's AI agent team.  
2026-07-02 · Nightly loop v4
