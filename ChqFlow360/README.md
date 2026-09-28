# ChqFlow360 — Prototype Source (V4 Live Demo, Dummy Branding)

This folder is the full, self-contained source of the last prototype —
the V4 Live Demo with dummy branding ("ChqFlow360" / "Workspace A").
No build step, no Node.js, no install of any kind required — everything
(HTML, CSS, and JavaScript) lives in the one file below.

## Latest feedback round (applied)

- **Alert colors lightened**: `--success`/`--warning`/`--danger`/`--info`
  were dark, muddy values left over from the old dark-theme-first design
  (e.g. amber was `#B45309`, a near-brown). Both files now use brighter,
  proper alert colors (`#22C55E` / `#F59E0B` / `#EF4444` / `#38BDF8`) —
  fixes the amber badges/pills that were hard to read on the light theme.
  Base text color was also nudged slightly darker (`#0A1638`) for
  readability.
- **Font size**: every `font-size` declaration in both files was
  increased by 1.5px, across every screen. Matching the exact
  SupplySphereAI font/size is still pending that reference.
- **Straight-Through Processing (STP) is now a real, working toggle**
  in `index.html` (previously just styled to look like one) — click it
  to actually flip STP on/off, and drag the new Signature-Match
  Threshold slider (85%–100%, each workspace's Admin sets their own —
  no more hardcoded 95%). `test-console.html`'s threshold control was
  also changed from a free-typed number box to the same 85–100 slider.
- **AI Agents page redesigned**: instead of a static grid of cards, it's
  now an illustrative pipeline diagram (OCR → Validation → Signature-
  Match → Fraud → Mapping → Notification → Analytics, with RedactAI
  shown branching off in parallel since it only runs on KYC uploads).
  Every agent box is clickable and opens a detail panel below with
  that agent's stats, recent activity, and an **Evals** section —
  see the note below.
- **Clickable navigation**: every tab and side-list that used to be
  decorative — Cheque Inbox's filters, Capture & Review's four modes,
  Cheque Lifecycle's customer list, Cheque Transfers' two tabs, the
  Masters list (all 8 masters), and Audit Logs' module filters — now
  actually switches what's shown, in `index.html`.

### Does this prototype have "Evals"?

Not before this round, and still not in the strict AI/ML sense (a
harness that scores a model's output against ground truth and tracks
that score over time). What's there now, added to answer this
directly: each AI Agent's detail panel on the AI Agents page has an
illustrative "Evals" box — dummy accuracy/sample-size/last-run figures,
labelled as illustrative. The one agent with genuinely real output
today is OCR (via Tesseract.js in `test-console.html`) — that's the one
place a real eval (recognized text vs. a hand-labelled ground truth set)
could actually be built if useful. Everything else (Validation, Fraud,
Signature-Match, etc.) is rule-based or simulated, so "accuracy" for
those is more honestly a test-pass-rate than a model eval.

## Two files in here

- **`index.html`** — the scripted Live Demo (5 pre-written cheques,
  auto-playing or step-through). This is for *presenting* the product.
- **`test-console.html`** — a separate, genuinely functional tool for
  *testing* the product. See below.

## test-console.html — real upload, rules, workflow, duplicate detection

Unlike `index.html`, this one isn't scripted. It's real, working logic
running entirely in your browser (still no backend, no install):

- **Real file upload** — pick or drag-and-drop an actual image; you see
  what you actually uploaded, not a stand-in graphic.
- **Real hygiene checks** — amount-in-words is checked against
  amount-in-figures using an actual Indian-numbering (Lakh/Crore)
  word converter, not a hardcoded pass/fail. Post-dated and stale
  (>3 months) date checks use real date math against today's actual date.
- **Real duplicate-cheque detection** — approved cheque numbers are
  remembered (via your browser's local storage) and checked against
  every new submission, including after you refresh the page.
- **Real workflow** — Approve / Reject / Resubmit / Fraud-Review actually
  change each cheque's status and write a real, timestamped Audit Log
  entry; the Dashboard's numbers are computed live from that state, not
  fixed.
- **Real OCR** — a "Run OCR Agent" button appears once you upload an
  image. It runs Tesseract.js (a real, open-source OCR engine, entirely
  in your browser via WebAssembly — not a server call) and shows the
  actual recognized text plus a confidence score. It reads printed text
  reasonably well; handwriting is unreliable, which is a genuine limit
  of general-purpose OCR, not this tool. It also tries a simple pattern
  match to auto-fill the Amount and Date fields when it spots something
  that looks right (marked so you know it was a guess) — Bank/Payee/
  Amount-in-words are not auto-mapped, since reliably knowing "this line
  is the payee" needs the cheque-trained model the real backend provides.
  **Requires internet on first use** (fetches the OCR engine from a CDN,
  a few MB, cached after) — works from the local file or the GitHub
  Pages link, but not from inside an Artifact preview (blocked by its
  sandbox).
- **Still simulated:** the signature-match score. Each of the 12
  built-in test cases seeds this with a starting value, which you can
  edit freely before running the checks — clearly labeled in the tool
  itself so nothing pretends to be real signature analysis.

Open it the same way as `index.html` — double-click, or Live Server in
VS Code. Start on the **Test Case Library** tab; it lists all 12 cases
with a one-click **Run**. A **Reset All Test Data** button clears
everything if you want to start the suite over clean.

## How to open it

- **Just to view it:** double-click `index.html`. It opens directly in
  your default browser (Chrome/Edge) and works fully offline.
- **To edit it:** open this whole `ChqFlow360` folder in VS Code
  (File → Open Folder...), then open `index.html` from the sidebar.
  Save your changes, then refresh the browser tab to see them.

### Optional: live-reloading preview while you edit

VS Code has a free extension called **"Live Server"** (by Ritwick Dey)
that auto-refreshes the browser every time you save — no admin rights
needed, it installs to your user profile only, not system-wide.
Install it from the Extensions panel (the square-icon on the left
sidebar in VS Code), then right-click `index.html` → **"Open with Live
Server."**

## Making cosmetic changes

Everything below is plain text — use VS Code's **Find** (Ctrl+F) to
jump straight to it, no coding knowledge required.

### Colors / theme
Search for this line near the top of the file (around line 74):
```
--bg:#0B0B10; --surface:#15151D; --card:#181823; ...
```
These are the master color values — change a hex code here and every
screen using that color updates everywhere (this is the same "change
once, apply everywhere" behavior the real product will have). Key ones:
- `--bg` — main background
- `--primary` — the blue accent used on buttons/links
- `--success` / `--warning` / `--danger` — the green/amber/red status colors

### Text / branding
Search for `Workspace A` to find every place the dummy tenant name
appears, or `ChqFlow360` for the product name. Replace either with
plain text — no HTML changes needed since these are just labels.

### Logo / title
Search for `<title>` (very top of the file) to change the browser tab
title.

## What NOT to touch

Avoid editing anything between `<script>` and `</script>` (the very
large block toward the bottom of the file) unless you're comfortable
with JavaScript — that section drives navigation, the live demo player,
and the theme switch. Cosmetic changes (colors, wording, images) never
need to touch this section.

## Where this fits with everything else

This is a **prototype** — HTML/CSS/JS only, no backend, no database, no
real OCR or AI processing. It's meant for demos and stakeholder review.
The actual product (Node.js/Python/PostgreSQL, real AI agents, a real
database) is a separate, much larger build that hasn't started yet —
see `01_Documentation` in the parent folder for the Business
Requirements Document and Operating Manual describing that build.

Other prototype versions (V1 Standalone, V2 Embedded/SDK, V3 Dummy
Branding, and the real-branded V4) live in their own numbered folders
one level up, if you need those too.
