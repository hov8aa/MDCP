# Post-Stream Pipeline Prompts

---

## v0.3.1

Prompt: Run the daily post-stream pipeline for Hari Om Vashishtha (hov8a) — 3rd Innings series.
North star: Generate $1M for Salesforce clients by December 31, 2026. Every output must be anchored to this goal.
All credentials and steps are in the loaded skill. Execute the full 11-step pipeline:
1. Mint a fresh OAuth access token using the refresh token
2. Find the latest completed live stream on the channel via YouTube Data API
3. List its caption tracks, download content using the OAuth Bearer token (tfmt=vtt)
4. Clean the VTT to plain text (strip timestamps, tags, deduplicate adjacent lines)
5. Fetch the previous day's Notion session page and extract its task list
6. Run Parser prompt on today's transcript → JSON  [parallel with step 7]
7. Run Summary Generator on today's transcript → prose  [parallel with step 6]
8. Run Alignment Engine on parser JSON → JSON  [waits for step 6]
9. Run Task Reconciler on {previous day's tasks + today's parser tasks} → carry-forward list  [waits for steps 5 and 6]
10. Run Next Actions Generator on {alignment output + carry-forward list} → recommended actions  [waits for steps 8 and 9]
11. Push one structured Notion page with all sections using the template in the skill

After pushing the Notion page, deliver a concise summary back to the user containing:
- Page title created
- Alignment verdict and score
- Whether ICP contact occurred today
- Whether a revenue signal occurred today
- The 3-5 recommended next actions
- A direct link to the Notion page created

Draft a story on the notion page about the evolution of the event in my tone.

If no new completed stream is found since the last pipeline run, report that clearly and do not create a duplicate Notion page, and do not start running the pipeline.

Be blunt. No hedging. Every recommendation must connect directly to $1M by December 31, 2026.

---

## v0.3.2

Run the daily post-stream pipeline for Hari Om Vashishtha (hov8a) — 3rd Innings series.
North star: Generate $1M for Salesforce clients by December 31, 2026.
Every output must be anchored to this goal. Be blunt. No hedging.
Every recommendation must connect directly to $1M by December 31, 2026.

If no new completed stream is found since the last pipeline run, report that
clearly and do not create a duplicate Notion page and do not start the pipeline.

PIPELINE STEPS — execute in order:
1. Mint a fresh OAuth access token using the refresh token
2. Find the latest completed live stream on the channel via YouTube Data API
3. List its caption tracks, download content using the OAuth Bearer token (tfmt=vtt)
4. Clean the VTT to plain text (strip timestamps, tags, deduplicate adjacent lines)
5. Fetch the previous day's Notion session page and extract its task list
6. Run Parser on today's transcript → extract tasks, artifacts, ICP interactions,
   learnings, content created [parallel with step 7]
7. Run Summary Generator on today's transcript → prose narrative in Hari's tone,
   telling the story of how the session evolved [parallel with step 6]
8. Run Alignment Engine on parser output → score, verdict, drift analysis
   [waits for step 6]
9. Run Task Reconciler on {previous tasks + today's parser tasks} →
   consolidated task list grouped by project [waits for steps 5 and 6]
10. Run Next Actions Generator on {alignment output + task list} →
    3-5 recommended actions, each with explicit revenue connection
    [waits for steps 8 and 9]
11. Push one structured Notion page using the layout below
12. Update the YouTube video description with the session summary +
    outreach hook + Notion page link

After pushing, deliver a concise terminal summary:
- Page title created
- Alignment score and verdict
- ICP contact: YES / NO
- Revenue signal: YES / NO
- 3-5 next actions
- Direct link to Notion page

---

### NOTION PAGE LAYOUT

Page title: [Date] — [Stream Title] — 3rd Innings

**Section 1: ALIGNMENT VERDICT** (visible, not in toggle)
Score | Verdict | ICP Contact | Revenue Signal
One paragraph: what this session means for the $1M goal. Blunt.

**Section 2: SESSION STORY** (toggle — "The Story")
Narrative prose in Hari's tone. Tell the arc of the session —
what was attempted, what landed, what didn't, what it means.
Not a list. A story.

**Section 3: NEXT ACTIONS** (toggle — "Next Actions")
3-5 actions only. Each action on one line:
[Action] → [Direct revenue connection to $1M goal]
Ranked by revenue proximity. Highest leverage first.

**Section 4: TASKS BY PROJECT** (toggle — "Tasks by Project")
Group all tasks under these projects. Add new projects if the
session surfaces them. For each project show:
- In Progress
- Carry Forward (with priority: LEVERAGE / OVERHEAD / NEUTRAL)
- Completed this session

Projects (in priority order):
1. Outbound / ICP
2. Teardown Product
3. Hermes Agent / Pipeline
4. Content / YouTube
5. Infrastructure
[+ any new projects surfaced this session]

Each task scored:
- Effort: LOW / MED / HIGH
- Revenue impact: DIRECT / INDIRECT / NONE
- Priority: derived from effort + revenue impact

**Section 5: LEARNINGS** (toggle — "What This Session Taught")
Bullet list. Factual. No padding.

**Section 6: ARTIFACTS** (toggle — "Artifacts Built")
Name | Status | Deployed: YES/NO

**Section 7: DRIFT ANALYSIS** (toggle — "Drift Analysis")
Streak counters: sessions without ICP contact, sessions without
revenue signal, sessions without published artifact.
One blunt paragraph. No softening.

---

### YOUTUBE DESCRIPTION FORMAT

[Session summary — 3-4 sentences in Hari's tone, what was built and learned]

---

If you are a Salesforce SI leader dealing with system complexity, broken
architecture, or unclear AI integration — I run a 5-Day Salesforce Systems
Teardown. I act as a blunt researcher with read access to your full Salesforce
architecture. I map it, cost the broken nodes, and design a 3-week experiment
with a verifiable outcome goal agreed by leadership before it starts.

Full session notes and task tracker: [Notion page link]

Book a conversation: [google calendar]
