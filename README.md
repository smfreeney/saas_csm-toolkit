MIT License

Copyright (c) 2026

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
# 🚀 SaaS CSM Toolkit

**The all-in-one Customer Success Manager operating system — built for Notion.**

Task tracker. Documentation hub. Brag book. Project planner. Performance review ammo.

---

## What This Is

If you're a CSM at a SaaS company, you already know the drill — you're juggling 30+ accounts, hopping between Zoom calls, chasing down action items in Slack threads, and somehow expected to remember that thing you did six months ago when review season hits.

This toolkit fixes that. It's a complete Notion workspace designed specifically for Customer Success Managers who work in SaaS. Not generic project management. Not repurposed sales templates. Built from the ground up for how CSMs actually work.

## What's Inside

### 📋 Task & Action Item Tracker
- Track action items by account, priority, and due date
- Automatic rollover for overdue items
- Meeting-linked tasks (every action item ties back to a call)
- Weekly review dashboard

### 📞 Call & Meeting Log
- Pre-call prep templates with account context
- Live note-taking structure (agenda → discussion → action items → follow-up)
- Searchable call history by account, date, or topic
- QBR and EBR planning templates

### 📊 Account Health Dashboard
- Health score tracking (usage, engagement, sentiment, support tickets)
- Risk and expansion signal flags
- Renewal timeline with countdown
- Stakeholder mapping per account

### 🏆 Brag Book / Win Tracker
- Log wins as they happen (don't wait for review season)
- Categorize by type: retention, expansion, advocacy, process improvement
- Quantify impact with revenue numbers, NPS changes, churn prevention
- Auto-generate review talking points from your wins

### 📈 Project Planner
- Onboarding project templates (30/60/90 day)
- Implementation tracking with milestones
- Cross-functional collaboration tracker (who owes what from Product, Support, Engineering)
- Customer journey stage tracking

### 📖 CSM Best Practices Playbook
- Discovery call frameworks
- QBR structure and cadence guide
- Escalation handling playbook
- Churn risk mitigation strategies
- Expansion/upsell conversation guides
- Stakeholder management tactics
- Internal advocacy techniques

### 🔄 Performance & Growth
- Weekly self-assessment prompts
- Goal tracking (OKRs / KPIs)
- Skills development tracker
- Feedback log (from managers, peers, customers)
- Quarterly review prep worksheet

---

## Quick Start

### Option 1: Excel Workbook (Fastest)
1. Download `CSM-Operating-System.xlsx` from this repo
2. Open it in Excel or Google Sheets
3. Replace the sample data with your own accounts
4. See [EXCEL-README.md](EXCEL-README.md) for the full guide

### Option 2: Notion Template
1. Follow the Setup Guide in `/docs/setup-guide.md`
2. Build databases using the schemas in `/docs/database-schemas.md`
3. Import CSV sample data from `/notion-import/`
4. Copy template content from `/templates/` into Notion pages

### Option 3: Build From Scratch
1. Clone this repo
2. Follow the detailed database schemas in `/docs/database-schemas.md`
3. Create each database manually in Notion using the field definitions
4. Import the markdown content from `/docs/` for reference pages

---

## File Structure

```
csm-toolkit/
├── README.md                          # You are here
├── EXCEL-README.md                    # Guide for the Excel workbook
├── CSM-Operating-System.xlsx          # Ready-to-use Excel workbook
├── docs/
│   ├── setup-guide.md                 # Step-by-step Notion workspace setup
│   ├── database-schemas.md            # Every database field defined
│   ├── best-practices-playbook.md     # CSM playbook content
│   ├── performance-review-guide.md    # How to use this for reviews
│   └── customization-guide.md         # Adapting to your org
├── templates/
│   ├── weekly-review-template.md      # Weekly check-in structure
│   ├── qbr-template.md               # Quarterly Business Review template
│   ├── onboarding-30-60-90.md         # Onboarding project plan
│   ├── call-prep-template.md          # Pre-call preparation checklist
│   ├── escalation-template.md         # Escalation documentation
│   └── brag-book-entry.md             # Win documentation template
├── notion-import/
│   ├── accounts-sample.csv            # Sample accounts for Notion import
│   ├── tasks-sample.csv               # Sample tasks
│   ├── calls-sample.csv               # Sample call logs
│   └── brag-book-sample.csv           # Sample brag book entries
└── assets/
    └── screenshots/                   # Setup reference images
```

---

## Who This Is For

- **New CSMs** who want structure from day one
- **Experienced CSMs** who are tired of scattered docs and lost context
- **CS Leaders** who want a replicable system for their team
- **Anyone preparing for performance reviews** who wishes they'd been tracking wins all along

---

## SaaS-Specific Features

This isn't a generic task manager. Every piece is built around SaaS CS realities:

- **ARR/MRR tracking** per account with renewal dates
- **Product adoption metrics** integration points
- **NPS/CSAT** score logging
- **Support ticket correlation** with account health
- **Feature request tracking** to bridge CS ↔ Product
- **Multi-threading** stakeholder management
- **Land and expand** opportunity tracking
- **Churn risk scoring** framework

---

## Contributing

Found something missing? Have a better framework? PRs welcome.

1. Fork the repo
2. Create a feature branch
3. Submit a PR with context on why the change helps CSMs

---

## License

MIT — use it, customize it, share it with your CS team.

---

*Built by a CSM, for CSMs. Because we deserve better tools than a messy spreadsheet and a prayer.*
