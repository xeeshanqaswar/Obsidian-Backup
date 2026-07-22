
### Possible Niches

<input type="radio" name="niches"><label>QA testers and bug reporters</label>
<input type="radio" name="niches"><label>UX researchers annotating competitor sites</label>
<input type="radio" name="niches"><label>Students/researchers doing web research</label>
<input type="radio" name="niches"><label>Support agents documenting workflows</label>

### UX researchers and product designers

Here's why it's the strongest fit rather than just a plausible one — your differentiated features map almost 1:1 onto that workflow.

- Floating page-anchored notes = annotating a competitor's actual UI in place.
- Screenshot capture = evidence for the teardown.
- Collections = one folder per competitor.

**Note:** No other cheap in-browser tool owns "annotate live competitor sites for a UX teardown

The heavy incumbents (Maze, Dovetail) are research repositories and usability-testing platforms, expensive and aimed at a different job. There's a genuine gap in the middle.

A positioning statement to work against:

> _Sidekick Notes is the fastest way to run a competitive teardown — capture, screenshot, and annotate any live site right where you're looking, organized per competitor, without leaving your browser._


### Make or Break 

**1. "Why not just paste screenshots into Figma or Notion?"** This is your real competitor — a _habit_, not a product. Many researchers already have that workflow. You're not filling a void; you're displacing muscle memory. So your in-flow speed advantage has to be _obvious in the first 60 seconds_, not marginal. If it's only slightly faster, they won't switch.

**2. Episodic usage breaks subscriptions.** Competitive teardowns happen in bursts — heavy for a week, then nothing for a month. That's poison for monthly recurring revenue (people cancel between projects). Implication: price this as an **annual plan or a one-time/lifetime license**, not $9/month. This is a real strategic constraint, not a detail.

**3. The single-user/local ceiling becomes acute fast.** The moment a researcher wants to hand the teardown to a PM, or open it on their work laptop instead of their personal one, you're stuck. That's actually good news in disguise: it tells you exactly what the paid feature is. **Export (PDF/Markdown) is the wedge, and sync is the eventual upgrade** — which lines up with the export-first monetization plan you'd already landed on. The teardown _deliverable_ is what they'll pay to get out of the tool.

**4. TAM and reachability.** "Everyone who takes notes" is millions; "solo/freelance UX researchers who do competitive teardowns regularly" is a much smaller pool. That's the tradeoff of niching — better conversion, smaller ceiling. You need to confirm the pool is big enough and findable (r/userexperience, UX Twitter/LinkedIn, Designer Hangout, Product Hunt, Maze/Dovetail's own audiences).

The sharpest thing I'd add: your **heuristic-evaluation-template idea is the actual wedge feature**, more than notes-in-general. A one-click "drop Nielsen's 10 heuristics as a checklist onto this page" — where each heuristic becomes a note you fill in against the live site — is something _no_ note tool does and that this exact audience is trained to want. That's the demo that makes a UX researcher stop scrolling. I'd build the positioning around _that_, with general notes as the substrate underneath.


### User Testing Audience

- r/userexperience
- Designer Hangout (Slack)
- the ADPList mentorship community
- UX folks on LinkedIn

- IndieHackers
- r/SideProject
- Product Hunt

## **Features I would add before serious monetization**

The most important paid-feature candidates:

1. **Page-linked notes**  
    Open a site and instantly see notes attached to that page/domain.
2. **Cloud sync**  
    This is almost required for paid productivity software.
3. **Export**  
    Markdown, PDF, CSV, Notion, Google Docs.
4. **Screenshot annotation**  
    Arrows, boxes, blur, text labels. Very useful for QA/design/product users.
5. **AI summary / cleanup**  
    Turn clipped text + screenshots into clean notes, summaries, bug reports, or research cards.
6. **Reminder / revisit system**  
    “Remind me when I visit this page again” or “show this note next time I open this website.”

### Features that would actually make it attractive to this niche

These are the things that convert Sidekick from "a nicer Google Keep" into "the competitive-research tool," roughly in order of impact:

**Export to a deliverable.** Already flagged above but it bears repeating — this is the difference between a toy and a tool for this audience. A clean PDF/Markdown of a collection (each note with its screenshot, source URL, and your comment) is what they hand off. If you build one paid feature, build this.

**Auto-capture source context.** Every note should silently record the URL, page title, and a favicon/timestamp. Researchers live or die by "where did this come from" — an observation without its source is useless in an audit. This is a small lift on top of your existing model and disproportionately valuable.

**Full-page and element screenshots.** Right now you capture the visible tab. This niche needs to grab a whole scrolling pricing page or a single component. Full-page capture is table stakes in this space (it's why GoFullPage has millions of users), and element capture is what makes bug/UX notes precise.

**Screenshot annotation.** Arrows, boxes, and a blur tool on the captured image, so they can point at the exact element and redact anything sensitive. This is standard in every visual-feedback tool and its absence would be noticed immediately.

**A synthesis / board view.** After capturing 40 observations across 5 competitors, they need to _reorganize_ — group by theme, or lay competitors out side by side. A simple board or a comparison-matrix view (competitors as columns, criteria as rows) is the classic competitive-analysis artifact and would be a strong differentiator, since the plain highlighter tools don't do it.

**Templates.** Ship a couple of starter structures — a heuristic-evaluation checklist, a competitive-teardown matrix, a feature-comparison grid. This both speeds them up and teaches them the tool is _for them_.

One honest engineering flag: the free tier fits your current architecture perfectly (vanilla JS, local storage, no backend). But several paid features — cloud sync, team sharing, share links, _and the license check that gates any paid feature at all_ — all require a backend server and accounts. That's a real step up from "no build step, no dependencies," and it's the biggest technical decision on this path. My suggestion: keep everything local-first for the free tier, and treat the backend as a deliberate v2 investment you make only once you've validated that the UX/competitive-research positioning is pulling real, retained users. The export feature is the one high-value paid item you could ship _without_ a full backend (it's client-side generation gated by a lightweight license key), which makes it a good first monetization step.