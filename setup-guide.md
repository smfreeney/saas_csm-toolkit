# Database Schemas — Full Technical Reference

Complete field-level specifications for every database in the CSM Toolkit. Use this to build each database from scratch in Notion, or as a reference when customizing.

---

## 1. Accounts Database

The backbone. Everything else relates back here.

### Fields

| Field Name | Property Type | Configuration | Required | Notes |
|---|---|---|---|---|
| Account Name | Title | — | Yes | Primary identifier |
| ARR | Number | Format: US Dollar | Yes | Annual Recurring Revenue |
| MRR | Formula | `prop("ARR") / 12` | Auto | Monthly Recurring Revenue |
| Renewal Date | Date | Date format, no end date | Yes | Next renewal date |
| Days to Renewal | Formula | `dateBetween(prop("Renewal Date"), now(), "days")` | Auto | Countdown |
| Health Score | Select | Green 🟢 / Yellow 🟡 / Red 🔴 | Yes | Updated monthly minimum |
| Tier | Select | Enterprise / Mid-Market / SMB / Strategic | Yes | Account segmentation |
| Industry | Select | Customize to your vertical | No | For pattern analysis |
| Stage | Select | Onboarding / Adopting / Expanding / Renewing / At-Risk / Churned | Yes | Lifecycle stage |
| CSM Owner | Person | — | Yes | Primary owner |
| Main Contact | Rich Text | — | Yes | Primary stakeholder name + title |
| Secondary Contacts | Rich Text | — | No | Multi-threading contacts |
| Contract Start | Date | — | No | Original contract date |
| Contract Length | Select | Monthly / Annual / 2-Year / 3-Year | No | Term length |
| Product/Plan | Select | Customize to your plans | No | What they're on |
| Seats/Licenses | Number | — | No | License count |
| NPS Score | Number | — | No | Most recent NPS |
| Last NPS Date | Date | — | No | When NPS was collected |
| CSAT Score | Number | — | No | Most recent CSAT |
| Last QBR Date | Date | — | No | When you last did a QBR |
| Next QBR Date | Date | — | No | Scheduled next QBR |
| CRM Link | URL | — | No | Link to Salesforce/HubSpot record |
| Notes | Rich Text | — | No | General context |
| Tasks | Relation | → Tasks DB (two-way) | Auto | Related tasks |
| Calls | Relation | → Calls DB (two-way) | Auto | Related calls |
| Wins | Relation | → Brag Book DB (two-way) | Auto | Related wins |
| Projects | Relation | → Projects DB (two-way) | Auto | Related projects |

### Recommended Views

| View Name | Type | Filters | Sort | Group By |
|---|---|---|---|---|
| All Accounts | Table | None | Name A→Z | None |
| By Health | Board | None | — | Health Score |
| Renewals Next 90 Days | Table | Days to Renewal ≤ 90 AND Stage ≠ Churned | Days to Renewal ASC | None |
| At Risk | Table | Health Score = Red | ARR DESC | None |
| By Tier | Table | None | ARR DESC | Tier |
| My Accounts | Table | CSM Owner = Me | Name A→Z | Stage |

---

## 2. Tasks & Action Items Database

### Fields

| Field Name | Property Type | Configuration | Required | Notes |
|---|---|---|---|---|
| Task | Title | — | Yes | Clear, actionable description |
| Account | Relation | → Accounts DB | Yes | Which account this is for |
| Status | Select | Not Started / In Progress / Waiting / Blocked / Done | Yes | Current state |
| Priority | Select | 🔴 Urgent / 🟡 High / 🔵 Medium / ⚪ Low | Yes | Importance level |
| Due Date | Date | Date only | Yes | Deadline |
| Owner | Person | — | Yes | Who's doing it |
| Source | Select | Call / Email / Slack / Internal / QBR / Support / Ad-hoc | No | Where it came from |
| Related Call | Relation | → Calls DB | No | Meeting that generated this task |
| Category | Select | Follow-up / Internal Request / Customer Request / Deliverable / Research | No | Task type |
| Notes | Rich Text | — | No | Context and details |
| Completed Date | Date | — | No | When finished (for velocity tracking) |
| Created Date | Created time | Auto | Auto | For aging analysis |

### Recommended Views

| View Name | Type | Filters | Sort | Group By |
|---|---|---|---|---|
| My Today | Table | Due Date ≤ Today + Status ≠ Done | Priority | None |
| This Week | Table | Due Date ≤ 7 days from now + Status ≠ Done | Due Date ASC | Account |
| By Account | Board | Status ≠ Done | Due Date ASC | Account |
| Blocked | Table | Status = Blocked | Created Date ASC | None |
| Completed This Month | Table | Completed Date = This month | Completed Date DESC | None |
| Overdue | Table | Due Date < Today + Status ≠ Done | Due Date ASC | Priority |

---

## 3. Calls & Meetings Database

### Fields

| Field Name | Property Type | Configuration | Required | Notes |
|---|---|---|---|---|
| Meeting Title | Title | — | Yes | Format: "[Account] - [Type] - [Date]" |
| Account | Relation | → Accounts DB | Yes | Which account |
| Date | Date | Date + Time | Yes | When it happened |
| Type | Select | Check-in / QBR / EBR / Onboarding / Training / Escalation / Internal / Ad-hoc | Yes | Meeting category |
| Attendees | Rich Text | — | No | Who was there |
| Agenda | Rich Text | — | No | Planned topics |
| Discussion Notes | Rich Text | — | Yes | What was discussed |
| Key Takeaways | Rich Text | — | No | Top 2-3 insights |
| Sentiment | Select | 😊 Positive / 😐 Neutral / 😟 Concerned / 😠 Negative | No | Customer mood |
| Action Items | Relation | → Tasks DB | No | Tasks generated |
| Follow-up Date | Date | — | No | Next planned touchpoint |
| Follow-up Done | Checkbox | — | No | Did the follow-up happen |
| Recording Link | URL | — | No | Zoom/Gong/Chorus link |
| Prep Notes | Rich Text | — | No | What you reviewed before the call |

### Recommended Views

| View Name | Type | Filters | Sort | Group By |
|---|---|---|---|---|
| Upcoming | Table | Date > Today | Date ASC | None |
| This Week | Calendar | Date = This week | — | — |
| By Account | Table | None | Date DESC | Account |
| Needs Follow-up | Table | Follow-up Date ≤ Today + Follow-up Done = False | Follow-up Date ASC | None |
| Recent (Last 30 Days) | Table | Date ≥ 30 days ago | Date DESC | Type |

---

## 4. Brag Book / Wins Database

### Fields

| Field Name | Property Type | Configuration | Required | Notes |
|---|---|---|---|---|
| Win Title | Title | — | Yes | Punchy, specific headline |
| Account | Relation | → Accounts DB | No | Not all wins are account-specific |
| Date | Date | — | Yes | When it happened |
| Category | Multi-select | Retention / Expansion / Advocacy / Process / Adoption / Onboarding / Mentoring / Cross-functional | Yes | What type of win |
| Revenue Impact | Number | Format: US Dollar | No | Dollars saved, added, or influenced |
| Description | Rich Text | — | Yes | The full story |
| Problem | Rich Text | — | No | What challenge existed |
| Action Taken | Rich Text | — | No | What you specifically did |
| Result | Rich Text | — | No | Measurable outcome |
| Metrics | Rich Text | — | No | Hard numbers |
| Who Was Involved | Rich Text | — | No | Collaborators |
| Evidence | Files & Media | — | No | Screenshots, emails, data |
| Review Ready | Checkbox | — | No | Polished enough for a review |
| Quarter | Select | Q1-2025 / Q2-2025 / etc. | Yes | For filtering by period |
| Theme | Select | Customize to your narrative themes | No | For review grouping |
| Visibility | Select | Personal / Team / Company | No | Who should see this win |

### Recommended Views

| View Name | Type | Filters | Sort | Group By |
|---|---|---|---|---|
| All Wins | Table | None | Date DESC | None |
| By Category | Board | None | Date DESC | Category |
| Review Ready | Table | Review Ready = True | Date DESC | Quarter |
| Revenue Impact | Table | Revenue Impact > 0 | Revenue Impact DESC | None |
| This Quarter | Table | Quarter = Current Quarter | Date DESC | Category |
| By Theme | Board | None | Date DESC | Theme |

---

## 5. Projects Database

### Fields

| Field Name | Property Type | Configuration | Required | Notes |
|---|---|---|---|---|
| Project Name | Title | — | Yes | Descriptive project title |
| Account | Relation | → Accounts DB | No | Not all projects are account-level |
| Status | Select | Planning / Active / On Hold / Completed / Cancelled | Yes | Current state |
| Type | Select | Onboarding / Implementation / Migration / Expansion / Internal Initiative / Playbook | Yes | Project category |
| Priority | Select | High / Medium / Low | No | Relative importance |
| Start Date | Date | — | Yes | When it kicked off |
| Target End Date | Date | — | Yes | Expected completion |
| Actual End Date | Date | — | No | When it actually finished |
| Owner | Person | — | Yes | Primary driver |
| Stakeholders | Rich Text | — | No | Everyone involved |
| Objectives | Rich Text | — | Yes | What success looks like |
| Milestones | Rich Text | — | No | Key checkpoints with dates |
| Current Status Update | Rich Text | — | No | Latest update (overwrite weekly) |
| Risks & Blockers | Rich Text | — | No | What could go wrong |
| Tasks | Relation | → Tasks DB | No | Related action items |
| Outcome | Rich Text | — | No | Final result (for Brag Book) |
| Lessons Learned | Rich Text | — | No | Retrospective notes |
| Related Win | Relation | → Brag Book DB | No | Link to the win when complete |

### Recommended Views

| View Name | Type | Filters | Sort | Group By |
|---|---|---|---|---|
| Active Projects | Table | Status = Active | Target End Date ASC | Type |
| All Projects | Table | None | Start Date DESC | Status |
| By Account | Table | Account is not empty | None | Account |
| Timeline | Timeline | Status ≠ Cancelled | Start Date ASC | — |
| Needs Update | Table | Status = Active + Current Status Update is empty | Target End Date ASC | None |

---

## 6. Goals & OKRs Database

### Fields

| Field Name | Property Type | Configuration | Required | Notes |
|---|---|---|---|---|
| Goal | Title | — | Yes | Specific, measurable goal |
| Type | Select | Company / Team / Personal | Yes | Scope |
| Quarter | Select | Q1-2025 / Q2-2025 / etc. | Yes | Time period |
| Key Result 1 | Rich Text | — | No | Measurable outcome |
| KR1 Target | Number | — | No | Target metric |
| KR1 Actual | Number | — | No | Current progress |
| KR1 Progress | Formula | Calculate percentage | Auto | Progress bar |
| Key Result 2 | Rich Text | — | No | Second measurable outcome |
| KR2 Target | Number | — | No | Target metric |
| KR2 Actual | Number | — | No | Current progress |
| Key Result 3 | Rich Text | — | No | Third measurable outcome |
| KR3 Target | Number | — | No | Target metric |
| KR3 Actual | Number | — | No | Current progress |
| Status | Select | On Track / At Risk / Behind / Achieved | Yes | Overall status |
| Notes | Rich Text | — | No | Context and updates |
| Related Wins | Relation | → Brag Book DB | No | Evidence of progress |

---

## 7. Feedback Log Database

### Fields

| Field Name | Property Type | Configuration | Required | Notes |
|---|---|---|---|---|
| Feedback | Title | — | Yes | Summary of feedback received |
| Date | Date | — | Yes | When received |
| Source | Select | Manager / Peer / Customer / Self-reflection / Skip-level | Yes | Who gave it |
| Source Name | Text | — | No | Specific person |
| Type | Select | Positive / Constructive / Mixed | Yes | Nature of feedback |
| Category | Select | Communication / Technical / Strategic / Process / Leadership | No | Area of feedback |
| Action Taken | Rich Text | — | No | What you did about it |
| Resolved | Checkbox | — | No | Have you addressed it |

---

## Formulas Reference

### Days to Renewal
```
dateBetween(prop("Renewal Date"), now(), "days")
```

### Monthly Recurring Revenue
```
prop("ARR") / 12
```

### Task Age (days since creation)
```
dateBetween(now(), prop("Created Date"), "days")
```

### Overdue Flag
```
if(and(prop("Due Date") < now(), prop("Status") != "Done"), "⚠️ OVERDUE", "")
```

### OKR Progress Percentage
```
if(prop("KR1 Target") > 0, round(prop("KR1 Actual") / prop("KR1 Target") * 100), 0)
```

---

## Relation Map

```
Accounts (central)
├── → Tasks (one-to-many)
├── → Calls (one-to-many)
├── → Brag Book (one-to-many)
├── → Projects (one-to-many)
│
Tasks
├── → Accounts
├── → Calls (many-to-one, source meeting)
│
Calls
├── → Accounts
├── → Tasks (one-to-many, generated action items)
│
Brag Book
├── → Accounts
├── → Projects (linked outcome)
│
Projects
├── → Accounts
├── → Tasks (one-to-many)
├── → Brag Book (linked win)
│
Goals/OKRs
├── → Brag Book (evidence)
│
Feedback Log
└── (standalone, no required relations)
```

---

*All field types are Notion-native. No third-party integrations required for core functionality.*
