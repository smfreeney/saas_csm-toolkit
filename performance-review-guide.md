# Customization Guide

This toolkit is a starting point — not a straitjacket. Here's how to bend it to fit your specific situation.

---

## Adapting to Your Company Size

### Startup / Early Stage (< 50 customers)

You probably don't need all seven databases on day one. Start with:
- **Accounts** (keep it simple — name, ARR, renewal, health)
- **Tasks** (this is your daily driver)
- **Brag Book** (start early, trust me)

Skip for now: Projects database (overkill at this stage), Goals/OKRs (your goals are "don't let anything catch fire"), Feedback Log (you're getting feedback in real-time from your founders).

Add databases as your book of business grows past 20 accounts.

### Mid-Market / Growth Stage

Use everything, but customize the Select options:
- Tier field might be "Growth / Scale / Enterprise" instead of SMB/MM/Ent
- Account Stage might include "Pilot" or "POC" if you do proof-of-concept deals
- Add a "CSM Pod" or "Team" field if you're working in pods

### Enterprise

Add complexity:
- **Stakeholder Map Database** — separate from Accounts, tracking every contact, their role, influence level, and sentiment
- **Risk Register Database** — formal risk tracking with probability and impact scores
- **Executive Sponsor Tracking** — who's assigned, last touchpoint, escalation history
- You'll probably want a "Region" field on Accounts if you're global

---

## Adapting to Your Industry

### Vertical SaaS (Healthcare, Legal, Fintech, etc.)

Add industry-specific fields:
- Compliance requirements tracking
- Implementation complexity score
- Regulatory timeline awareness
- Certification status

### Developer Tools / PLG (Product-Led Growth)

Usage data matters more than meeting frequency:
- Add detailed usage metrics fields (DAU, feature adoption %, API call volume)
- Reduce emphasis on call tracking — your customers may prefer async
- Add a "Community Engagement" field (forum posts, GitHub contributions)
- Consider a "Technical Health" score separate from relationship health

### Horizontal SaaS (CRM, HR, Marketing tools)

Multi-department tracking becomes important:
- Add "Department" field to Accounts or create sub-accounts
- Track multiple use cases per account
- Add "Executive Sponsor" and "Day-to-Day Contact" as separate fields

---

## Adapting to Your CS Model

### High-Touch (1:1)

The toolkit as-is works well for high-touch. Add:
- More detailed call templates
- Deeper stakeholder mapping
- Executive alignment tracking
- Custom success plans per account

### Mid-Touch (1:Few)

Simplify and batch:
- Focus on the Account Health board view
- Use grouped views extensively (batch similar tasks)
- Create email templates for common touchpoints instead of custom calls
- Lean on the "By Tier" views to prioritize where to spend time

### Low-Touch / Tech-Touch (1:Many)

You need a different structure entirely:
- Replace Calls database with "Customer Touchpoints" (includes automated emails, in-app messages, webinars)
- Health Score should be almost entirely usage-driven
- Focus on "cohort" views instead of individual accounts
- Add automation triggers: "If usage drops below X, create task"

### Hybrid Model

Most CS teams are hybrid. The key customization:
- Add a "Touch Model" field to Accounts: High / Mid / Low
- Create filtered views for each model
- Adjust your expected cadence per model:
  - High: Weekly/biweekly calls
  - Mid: Monthly calls + async check-ins
  - Low: Quarterly check-ins + automated journey

---

## Common Customizations

### Adding Custom Properties

Good candidates for custom Select/Multi-select fields:
- **Use Case** — What the customer is primarily using your product for
- **Integration Status** — What other tools they've connected
- **Champion Strength** — Strong / Moderate / Weak / None
- **Decision Maker Access** — Direct / Through Champion / No Access
- **Competitive Presence** — Are they also using a competitor?
- **Expansion Likelihood** — High / Medium / Low / None
- **Implementation Complexity** — Simple / Moderate / Complex

### Connecting to External Tools

Notion works best when it's your single source of truth for CS context. But you'll need to sync or reference:

**CRM (Salesforce, HubSpot)**
- Add a CRM Link URL field to Accounts
- Sync ARR and renewal dates periodically (or use a Notion integration if available)
- Don't try to duplicate your CRM — reference it

**CS Platform (Gainsight, Totango, ChurnZero)**
- Your CS platform handles automation and data aggregation
- This Notion workspace handles planning, documentation, and personal tracking
- They're complementary, not competitive

**Communication (Slack, Email)**
- Use Notion's web clipper to save important Slack messages or emails
- Link to Slack channels in your Account Notes

**Recording (Gong, Chorus, Zoom)**
- Add recording links to your Calls database
- Pull key quotes into your call notes

### Creating Automations

Notion's native automation (available on paid plans) can handle:
- Auto-assign "Not Started" status to new tasks
- Change status when a date passes (limited but useful)
- Notify you when a property changes

For more complex automation, consider:
- **Zapier/Make** — Trigger on Notion database changes
- **Notion API** — Build custom scripts for data sync
- **Slack integration** — Get notifications for overdue tasks

---

## What NOT to Customize (At Least Not Right Away)

Some things are tempting to change but will hurt you later:

1. **Don't remove the Brag Book categories.** They map to common review discussion areas. Add to them, but don't remove.

2. **Don't skip the Relations.** They're annoying to set up but they're what make the whole system actually useful. A task without an account link is just a to-do list.

3. **Don't over-engineer formulas on day one.** Get the data in first. You can always add calculations later.

4. **Don't create too many views.** Start with the recommended ones. Add views only when you find yourself filtering the same way repeatedly.

5. **Don't rename core fields to "creative" names.** "Health Score" is better than "Vibe Check" when you need to explain your system to someone else. (I know. I tried.)

---

## Sharing With Your Team

If you want to roll this out to a CS team:

### As a Team Template
1. Set up one pristine version with all databases empty
2. Share as a Notion template with your team workspace
3. Each CSM duplicates it for their personal workspace
4. Shared databases (Accounts) stay centralized; personal databases (Brag Book, Feedback Log) are individual

### As a Shared Workspace
1. One instance, everyone uses the same databases
2. Use "CSM Owner" filters for personal views
3. Managers get an overview dashboard across all accounts
4. Works better for team visibility but requires more governance

### Hybrid Approach
- Shared: Accounts, Tasks, Calls, Projects
- Personal: Brag Book, Goals/OKRs, Feedback Log
- This is usually the best balance

---

*Start simple. Add complexity only when it solves a real problem you're experiencing. The best system is the one you actually use.*
