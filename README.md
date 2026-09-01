But What If? 🌀

Because apparently one thought needed 47 browser tabs.

A playful, single-page reasoning tool for overthinkers. Drop in whatever your brain is currently spiraling on, answer a few quick context questions, and get back an Overthink-O-Meter score, the top 3 reasons you might be stuck, a Facts-vs-Story breakdown, a verdict, one concrete next move, a "Brain's Performance Review" one-liner, and a Bollywood song to reset your mood.

It's entertainment + light decision support — not therapy, not diagnosis, and it knows the difference (see Responsible design below).

🔗 Live demo: https://<your-username>.github.io/<your-repo>/

✨ Features
Guided intake — thought input, category + trigger dropdowns, and four context questions (evidence, control, impact, duration)
Deterministic reasoning engine — no API, no backend; scores are computed client-side from weighted evidence/impact/control inputs
Overthink-O-Meter — a 0–100 signal score with five color-coded bands, from "Mostly Noise" to "Factual Signal — Take Action"
Top 3 reasons you might be stuck, each with a likelihood tag
Facts vs The Movie My Brain Directed — separates what's actually known from what's been invented
Verdict + one next action — never a 14-step plan, just one move
Bollywood Mood Reset 🎧 — a curated song recommendation matched to category/verdict, with a gentler, calmer set automatically swapped in for Grief / Trauma categories
Challenge This Result — add missing context and see the score recalculate live
What Would I Tell a Friend? — reframes the thought as advice-to-a-friend
Built-in safety bypass — if the input suggests real danger, abuse, or self-harm, the humor engine is skipped entirely in favor of a grounded, resource-pointing message
Session-only privacy — nothing is stored, transmitted, or persisted; a visible "Clear my thoughts" action wipes the current session
Vibrant, floating-emoji visual theme — fully responsive, mobile-first
🛠 Tech stack

Plain HTML + CSS + vanilla JavaScript in a single file. No build step, no dependencies, no backend.

Fonts loaded from Google Fonts (Fraunces, Inter, Caveat)
All app logic — scoring engine, reason bank, song catalogue, quote bank — lives inline in <script>, organized into clearly separated data/logic blocks so it can be swapped for an LLM-backed engine later without touching the UI
🚀 Deploy to GitHub Pages
Option A — Project site from the repo root
Create a new repo (or use an existing one) and add this file as index.html at the root.
Push to GitHub.
Go to Settings → Pages.
Under Build and deployment, set Source to Deploy from a branch.
Set Branch to main (or master) and folder to / (root).
Save. Your site will be live at https://<your-username>.github.io/<your-repo>/ within a minute or two.
Option B — Serve from a /docs folder
Add this file as docs/index.html.
In Settings → Pages, set the branch folder to /docs instead of root.
Save and wait for the deploy.
Option C — User/organization site

If this repo is named <your-username>.github.io, just commit this file as index.html at the root and push — GitHub Pages serves it automatically with no settings changes needed.

Note: if you keep the filename as but-what-if.html instead of renaming it to index.html, GitHub Pages will serve it at /but-what-if.html rather than at the site root — either works, just adjust the link you share.

💻 Run it locally

No install required — it's a static file.

bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
open index.html   # or double-click the file, or use a local server:
python3 -m http.server 8000

Then visit http://localhost:8000.

📁 Project structure
.
├── index.html   # entire app — markup, styles, and engine logic
└── README.md

Everything is intentionally kept in one file for zero-friction deployment. If the project grows, the natural next split is:

/data     → categories, triggers, song catalogue, reason bank, quotes
/engine   → analyseThought.js, scoring.js, safety.js
/styles   → styles.css
index.html
🎛 Customizing

All the editable content lives in clearly labeled constants near the top of the <script> block:

What	Where
Categories & triggers	CATEGORIES, TRIGGERS
Scoring weights	runEngine()
Reasoning patterns	REASON_BANK + pickReasons()
Bollywood catalogue	SONGS + songSetForCategory()
"Brain's Performance Review" one-liners	REVIEW_QUOTES, GENTLE_REVIEW_QUOTES
Safety-bypass keyword patterns	SAFETY_PATTERNS
Loading messages	LOADER_MSGS

To plug in a real LLM later, replace the body of runEngine() with an API call and keep the same return shape — the rendering code doesn't need to change.

🔒 Privacy
Thoughts are kept only in in-memory JavaScript state for the current browser session.
Nothing is sent to a server, logged, or persisted to storage.
Refreshing the page or clicking Clear my thoughts wipes everything.
⚠️ Responsible design

This tool is entertainment and reflective decision support. It does not:

diagnose mental-health conditions
judge whether trauma or distress is "real"
invalidate serious distress
provide medical advice
present its scores as psychological fact

If input suggests immediate danger, abuse, self-harm, or a serious health concern, the app skips the humor/scoring engine entirely and shows a direct message encouraging the person to contact a trusted person, a qualified professional, or emergency services.

📄 License
Add a license of your choice (MIT is a common default for personal projects) — create a LICENSE file at the repo root.
