# Setup Guide

Getting this workspace running shouldn't take more than an hour. Probably less if you've built Notion databases before.

---

## Before You Start

You'll need:
- A Notion account (free tier works, but Pro is better for the database features)
- Access to your company's account list (even a rough one)
- About 45-60 minutes of uninterrupted time

A heads up — don't try to set up everything at once. Start with the core databases, get comfortable, then layer on the extras.

---

## Step 1: Create Your Workspace Structure

Create a top-level page called **CSM Operating System** (or whatever you want — it's your workspace).

Under that, create these sub-pages:
- 📋 Tasks & Action Items
- 📞 Calls & Meetings
- 📊 Account Health
- 🏆 Brag Book
- 📈 Projects
- 📖 Playbook
- 🔄 Performance & Growth

Each of these will house one or more databases plus supporting documentation.

---

## Step 2: Build Core Databases

Build these in order — later databases reference earlier ones.

### Database 1: Accounts
This is your master account list. Everything else links back here.

| Field | Type | Notes |
|-------|------|-------|
| Account Name | Title | Company name |
| ARR/MRR | Number (currency) | Current contract value |
| Renewal Date | Date | Next renewal |
| Health Score | Select | Green / Yellow / Red |
| CSM Owner | Person | You (or team members) |
| Tier | Select | Enterprise / Mid-Market / SMB |
| Industry | Select | Customize to your book |
| Main Contact | Text | Primary stakeholder |
| Stage | Select | Onboarding / Adoption / Expansion / Renewal |
| Notes | Text | Quick context |
| Days to Renewal | Formula | `dateBetween(prop("Renewal Date"), now(), "days")` |

### Database 2: Tasks & Action Items
Your daily workhorse database.

| Field | Type | Notes |
|-------|------|-------|
| Task | Title | What needs doing |
| Account | Relation | Links to Accounts DB |
| Status | Select | Not Started / In Progress / Blocked / Done |
| Priority | Select | 🔴 Urgent / 🟡 High / 🔵 Medium / ⚪ Low |
| Due Date | Date | When it's due |
| Source | Select | Call / Email / Internal / QBR / Support Ticket |
| Owner | Person | Who's responsible |
| Related Call | Relation | Links to Calls DB |
| Notes | Text | Context and details |
| Completed Date | Date | For tracking velocity |

### Database 3: Calls & Meetings
Every customer interaction, logged.

| Field | Type | Notes |
|-------|------|-------|
| Meeting Title | Title | Account + meeting type |
| Account | Relation | Links to Accounts DB |
| Date | Date | When it happened |
| Type | Select | Check-in / QBR / EBR / Onboarding / Escalation / Ad-hoc |
| Attendees | Text | Who was there |
| Agenda | Text | What you planned to cover |
| Discussion Notes | Text | What actually happened |
| Action Items | Relation | Links to Tasks DB |
| Follow-up Date | Date | Next touchpoint |
| Sentiment | Select | Positive / Neutral / Concerned / Negative |
| Recording Link | URL | Zoom/Gong link if applicable |

### Database 4: Brag Book (Wins)
This is the one you'll thank yourself for later.

| Field | Type | Notes |
|-------|------|-------|
| Win Title | Title | Clear, specific description |
| Account | Relation | Links to Accounts DB |
| Date | Date | When it happened |
| Category | Multi-select | Retention / Expansion / Advocacy / Process / Adoption / Onboarding |
| Revenue Impact | Number (currency) | Dollars saved or generated |
| Description | Text | The full story |
| Metrics | Text | Quantified outcomes |
| Who Was Involved | Text | Collaborators to credit |
| Evidence | Files & Media | Screenshots, emails, Slack messages |
| Review Ready | Checkbox | Polished enough for a review conversation |
| Quarter | Select | Q1 / Q2 / Q3 / Q4 + Year |

### Database 5: Projects
For anything that spans multiple weeks and needs milestone tracking.

| Field | Type | Notes |
|-------|------|-------|
| Project Name | Title | What you're working on |
| Account | Relation | Links to Accounts DB |
| Status | Select | Planning / Active / On Hold / Complete |
| Type | Select | Onboarding / Implementation / Migration / Expansion / Internal |
| Start Date | Date | Kickoff |
| Target End Date | Date | Deadline |
| Milestones | Text | Key checkpoints |
| Stakeholders | Text | Everyone involved |
| Risks | Text | What could go wrong |
| Tasks | Relation | Links to Tasks DB |
| Outcome | Text | Fill in when complete — feeds into Brag Book |

---

## Step 3: Create Your Views

For each database, set up these views at minimum:

### Tasks Database Views
- **My Today** — Filter: Due date is today or overdue + Status is not Done. Sort by priority.
- **This Week** — Filter: Due date is within the next 7 days. Group by account.
- **By Account** — Board view grouped by Account. Good for prep.
- **Blocked** — Filter: Status is Blocked. Review weekly.
- **Completed This Month** — Filter: Completed Date is this month. Useful for standups and reports.

### Calls Database Views
- **Upcoming** — Filter: Date is in the future. Sort by date ascending.
- **This Week's Calls** — Filter: Date is this week.
- **By Account** — Table grouped by Account. Timeline view.
- **Needs Follow-up** — Filter: Follow-up Date is today or overdue.

### Brag Book Views
- **All Wins** — Default table, sorted by date descending.
- **By Category** — Board view grouped by Category.
- **Review Ready** — Filter: Review Ready is checked. This is your review prep gold.
- **By Quarter** — Group by Quarter for periodic summaries.
- **Revenue Impact** — Sort by Revenue Impact descending. Your greatest hits.

---

## Step 4: Set Up Your Dashboard

Create a page called **📊 Weekly Dashboard** with these linked database views embedded:

1. Tasks due this week (filtered view)
2. Upcoming calls this week
3. Accounts with renewal in next 90 days
4. Recent wins (last 30 days)
5. Blocked items that need attention

This becomes your Monday morning starting point.

---

## Step 5: Import Your Accounts

Get your account list from your CRM (Salesforce, HubSpot, Gainsight, whatever) and add them to the Accounts database. You don't need every field filled in right away — just get the names, ARR, and renewal dates in there.

Pro tip: Notion's CSV import works, but it's finicky. Sometimes it's faster to just copy-paste from a spreadsheet.

---

## Step 6: Start Using It

Here's the habit loop that makes this work:

**Daily (5 min)**
- Check your "My Today" tasks view
- Log any calls/meetings after they happen
- Add action items from calls immediately (not later — you'll forget)

**Weekly (15 min)**
- Review blocked items
- Check next week's call schedule
- Log any wins from the week (seriously, do this weekly)
- Update account health scores if anything changed

**Monthly (30 min)**
- Review your Brag Book entries
- Update project statuses
- Clean up completed/stale tasks
- Check renewal timelines

**Quarterly (1 hour)**
- Prep your review materials from the Brag Book
- Update goals and OKRs
- Archive completed projects
- Refresh your account health assessments

---

## Common Setup Mistakes

- **Overcomplicating it on day one.** Start simple. Add complexity as you need it.
- **Not linking databases.** The power is in the relations. Every task should link to an account. Every call should link to tasks.
- **Forgetting to log wins.** Set a weekly reminder. Friday afternoon works well.
- **Making it too rigid.** This is YOUR system. Rename fields, add properties, delete what doesn't serve you.

---

## Next Steps

- Read the [Best Practices Playbook](best-practices-playbook.md) for CSM frameworks to embed into your workflow
- Check [Database Schemas](database-schemas.md) for the full technical specs
- See the [Performance Review Guide](performance-review-guide.md) for review prep strategies
