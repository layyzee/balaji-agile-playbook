# 📝 Meeting Action Items & Decision Extractor

Transform messy, unstructured meeting transcripts (from Teams, Zoom, Google Meet) or rough handwritten bullet points into executive-ready meeting summaries, RACI action item tables, and follow-up communication in seconds.

---

## 🎯 What This Solves
- **Eliminates post-meeting fatigue:** Saves 20–30 minutes after every refinement, planning, or stakeholder meeting.
- **Enforces accountability:** Assigns explicit owners and completion metrics using the RACI framework.
- **Prevents forgotten decisions:** Logs architectural and product commitments in writing.

---

## 🤖 The Production Prompt (Copy & Paste into Chat)

```markdown
You are an Executive Agile Delivery Assistant and Chief of Staff.

I will provide raw meeting notes or an unedited meeting transcript from a recent Scrum/project session.

Analyze the notes thoroughly and output a structured report using the exact format below:

---

### 1. 📌 Executive Summary (BLUF - Bottom Line Up Front)
- Provide exactly 3 bullet points summarizing the most critical outcomes, overall sprint posture, and high-level milestones agreed upon.

### 2. 🎯 Action Items Table (RACI Framework)
Format as a clean markdown table with these columns:
| # | Action Item | Assignee / Owner | RACI Role | Target Completion Date | Success Metric / Verification |
- Use explicit names from the transcript. If an owner is unassigned, flag as `⚠️ Unassigned - Needs Scrum Master Review`.
- RACI Key: (R)esponsible for doing it, (A)ccountable for final sign-off, (C)onsulted, (I)nformed.

### 3. ⚖️ Decisions & Agreements Log
- List all architectural, scope, or workflow decisions formally finalized during the call.
- Format: **[Decision Title]**: [Brief rationale and impacted components].

### 4. 🚧 Unresolved Blockers & Dependencies
- List any impediments that were raised but not resolved during the call.
- For each, recommend an unblocking owner and target escalation cutoff time.

### 5. ✉️ Ready-to-Send Follow-Up Message (Slack / Email)
- Draft a concise, professional 4-sentence summary ready to post in the team Slack/Teams channel to keep all attendees aligned.

---

Here is the raw meeting text:
[PASTE YOUR RAW MEETING TRANSCRIPT OR ROUGH NOTES HERE]
```

---

## 🧪 Demonstration & Test Case

### Sample Raw Input:
> *"Dave: Morning everyone. Let's talk about the search feature. Priya, did you finish the schema?  
> Priya: Almost, but the auth team didn't send the token specs. I can finish it in 3 hours once they do.  
> Balaji: I'll ping Marcus from Auth right after this call to get those specs by 1 PM today.  
> Sarah (PO): We also need to decide on the export button. Marketing wants PDF, but devs say CSV is faster.  
> Dave: Let's ship CSV in Sprint 14, and defer PDF to Sprint 15 so we don't delay the release.  
> Sarah: Agreed, let's do CSV first. Dave, make sure QA has test data by Thursday.  
> Dave: Will do. Also, our staging server rebooted twice yesterday. We need DevOps to inspect memory logs."*

### Sample Generated Output:

#### 1. 📌 Executive Summary
- **Search Schema Dependent on Auth Specs:** Schema design is 80% complete; pending token specs from the Auth team with an agreed 1:00 PM unblocking cutoff.
- **Export Scope Sliced:** Sliced export deliverable—delivering high-speed CSV in Sprint 14 and deferring PDF export to Sprint 15.
- **Staging Infrastructure Risk:** Unstable staging server rebooted twice; requires prioritized DevOps memory diagnostic before QA kickoff.

#### 2. 🎯 Action Items Table
| # | Action Item | Assignee | RACI | Target Date | Success Metric |
| :-: | :--- | :--- | :-: | :--- | :--- |
| 1 | Escalate and secure Auth token specifications | Balaji | **R** | Today, 1:00 PM | Token specs delivered to Priya |
| 2 | Finalize search database schema | Priya | **R** | Today +3 hrs from specs | Schema PR submitted |
| 3 | Provision synthetic test data for QA | Dave | **R** | Thursday, EOD | QA Lead confirms data availability |
| 4 | Investigate staging server crash & memory logs | ⚠️ DevOps Lead | **R** | Wednesday, 12:00 PM | Root cause ticket logged & resolved |

#### 3. ⚖️ Decisions & Agreements Log
- **Export Format Phasing:** Team agreed to ship CSV export for Sprint 14 to safeguard the release milestone, while PDF export is scheduled for Sprint 15 refinement.

#### 4. 🚧 Unresolved Blockers
- **Staging Server Stability:** Two crash events occurred yesterday. *Recommended Owner:* Balaji to escalate with DevOps on-call engineer by 11:30 AM today.

#### 5. ✉️ Ready-to-Send Team Slack Broadcast
> *"Hi Team — Thanks for a focused sync today. Key takeaways: Search schema is tracking for completion today pending Auth specs (Balaji following up by 1 PM). We finalized shipping CSV export for Sprint 14 and moving PDF to Sprint 15. Dave is providing QA test data by Thursday, and we are escalating the staging reboot issue with DevOps. Full action items logged in Jira!"*
