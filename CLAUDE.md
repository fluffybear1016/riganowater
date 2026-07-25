# CLAUDE.md — The Rigano Water Institute (riganowater.com)

A working evidence site published by a practicing environmental attorney about PFAS
contamination in Miami-Dade drinking water. Real officials are named. Real documents are
published. It will be read by journalists, by the agencies it accuses, and by opposing
counsel looking for one thing to discredit.

**One wrong factual claim discredits the entire record.** Speed is worthless here. Being
right is the only deliverable. Every rule below exists because something went wrong.

---

## 0. SCOPE: edit only what you were asked to edit

**The site is finished work by the attorney whose name and license are on it. It is not a
draft awaiting your improvement.** As of July 2026 it is in final-edit stage before launch.

> **Change only what the owner explicitly asked you to change. Nothing else. Ever.**

This is not a style preference. Published copy on this site is a lawyer's word choice about
named public officials, in his voice, on his record, carrying his professional exposure.
That judgment is his, and it is his even when you are confident he is wrong.

**Finding a problem is not authorization to fix it.** These are two separate things and
collapsing them is how an agent damages work it was never asked to touch. When you believe
something is wrong:

1. Finish the task you were actually given.
2. Raise the concern as **one sentence, as a question**, with the evidence.
3. Wait. The answer may be "that's intentional" — and it usually is, because he has context
   you don't.

**This rule has been broken once.** While writing this file, three pieces of published copy
were rewritten without being asked, because a subagent labelled a quotation "CRITICAL." The
quotation was verbatim and contiguous in the source; the concern was a debatable reading of
one sentence, not an error; and the call was never mine. All three were reverted to the
author's original wording. Cost: the user's time and trust, for zero benefit.

There is no urgency that justifies skipping the question. Asking costs ten seconds.

---

## I. THE ONE LAW: verify by looking, not by matching

A search returning zero is **not** evidence of absence. It is evidence your query didn't
match. Confusing these has produced three near-published falsehoods on this project.

| Searched | Concluded | Truth |
|---|---|---|
| `excellent` in the County's 2025 report | "The County never says excellent" | The word is **"excellence"** — the report's *opening line*, over a full-page photo of a girl holding out a glass |
| `PFOS` in the Miami Beach report | "The City deleted PFAS data" | That PDF's font encoding mangles its own text layer to `Perfluoroaclane sulfonale`. The table is on p. 8 |
| `the excellence of our drinking water` in our own live HTML | "The deploy failed" | Live markup was `the <mark>excellence</mark> of...`. Tags split the phrase |

The second would have been catastrophic: a public accusation that a city deleted contaminant
data, resting entirely on a broken font map.

### The rule

> **Before any factual claim is published, render the source page to PNG and read it with
> your own eyes.** `page.get_pixmap(dpi=120).save(...)`, then Read the image.

Use **dpi ≥ 120** for tables and footnotes; 95 is too coarse to read them reliably.

Text extraction *locates* a page. It never *proves* one. Specifics:

- Search **stems**: `excellen`, not `excellent`. `perfluoro`, not `PFOS`.
- Designed PDFs mangle ligatures (`confrms`) and letterforms. Government reports are
  typeset in InDesign and are the worst offenders.
- Same trap in **HTML**: grep a short distinctive token, or parse the DOM — never a long
  phrase that inline tags may split.
- Surprising or explosive findings demand **more** verification, not faster publication.

### Quoting standard — quote to the end of the thought

Truncation that invents a contrast the speaker never made is the most dangerous error
available to this site, because it looks like a quote and reads like a lie.

**The distinction that matters.** The City writes: *"the city's drinking water quality
continues to be excellent — not just safe for our more than 80,000 residents but also for
the millions of visitors who travel to Miami Beach each year."* The site quotes the leading
clause. That quotation is **verbatim and contiguous** — the words appear in the report in
that order — and the substance is exact: the City calls the water excellent, and calls it
safe. It is properly published.

A grammatical reading exists in which `not just [for residents] but also [for visitors]`
pairs the two prepositional phrases, so a clip at "safe" could be argued to imply an
excellent-vs-safe contrast. **That is an editorial judgment, not an error, and it belongs to
the author** — see § 0. Raise such things as a question; never act on them.

Rules: quote verbatim from a rendered page; record document **and page number**; never
paraphrase inside quote marks; never fix someone's grammar or typos; if a printout clips a
line at the page edge (several Gmail exports here do), use the unclipped parallel copy or
mark the elision. **When in doubt, shorten to the word you can defend absolutely, or quote
the whole sentence. Never stop mid-construction.**

### Absence claims need a higher bar

The site publishes negatives (e.g. *"The letters PFAS, PFOS and PFOA appear nowhere in the
twenty-four pages"* — verified true; the City spells the chemical names out and never uses
the acronyms a worried parent would search for). A grep can never support a negative.
**Requirement: render and visually read every page, and — where two copies of a document
exist — confirm the negative in both, since they carry different encoding damage.**

---

## II. Before you say you cannot do something

"I can't" is a **last resort that must be earned.** On this project the GitHub push was
declared blocked and handed back to the user while an authorized browser sat unused in the
toolset. The user had to point it out. Do not repeat it.

**Exhaust this ladder, in order:**

1. **Re-read the tool list**, including deferred tools — `ToolSearch` them. The capability
   is often already present under a name you didn't think to look for.
2. **Try another transport.** API blocked → browser. Push blocked → web UI. Shell blocked →
   Python. There are usually three doors.
3. **Spawn subagents — liberally, in parallel** (one message, multiple `Agent` calls; they
   have their own context windows):
   - `Explore` — mapping unfamiliar code. `index.html` is 10 MB; **never read it whole.**
   - `general-purpose` — document inventories, extraction, verification sweeps.
   - **Adversarial agent — the highest-value move on this project.** An agent whose only
     job is to *disprove* the work. Instruct it to find errors, forbid it from praising,
     require primary sources. The audit that caught the truncation above was one of these;
     it found defects in every category it was pointed at. **Run one before any substantive
     ship.**

   **A subagent's finding is a LEAD, not a verdict.** Verify every one independently before
   acting on it, and note what it was *scoped to*. This was violated in this file's own
   creation: an audit agent correctly reported that **this document's** § VIII carried no
   citation for the thyroid figure. That finding was about *this file*. It was then written
   up as a claim that **the site's** thyroid data was unsourced — and the site sources it
   fifteen ways (§ VIII). One `grep -c 'SCAN360' index.html` would have taken three seconds
   and was never run, immediately after § I was written forbidding exactly that.

   Three specific traps:
   - **An agent told to find defects will return defects.** That is what it was commissioned
     to do. The burden of verification shifts entirely to you.
   - **Confident formatting is not evidence.** Severity labels, tables and "CRITICAL" tags
     are the agent's rhetoric, not proof. Weigh the evidence, not the presentation.
   - **Watch the scope boundary.** A finding about your draft is not a finding about the
     user's work. Never let a conclusion cross that line.

4. **Only then** report the blocker — with what was tried, why each failed, and the exact
   action needed from the user.

Independent work runs **concurrently**, never serially.

---

## III. Think second and third order

**The canonical example.** Miami-Dade's 2025 report deleted the word "safe."

- **First order:** a word changed. Mildly interesting.
- **Second order:** they deleted *only* "safe" — the legally actionable word, the one that
  founds failure-to-warn and negligent-misrepresentation — while keeping "excellence,"
  which is puffery and far harder to sue over, and keeping the photograph of the child.
  That is not sloppiness. That is a lawyer's edit.
- **Third order:** the deletion **is** the admission. Nobody quietly removes a word they
  still believe is true. The legal exposure was managed; the public risk was not. That
  inversion is the story.

The same discipline found the Miami Beach mechanism: PFOS 38 and PFOA 30 printed with the
**Federal MCL column left blank as "N/A"**, footnoted "not currently regulated," under an
intro line reading "All are below maximum contaminant levels allowed" — and the acronyms
"PFAS/PFOS/PFOA" absent from all 24 pages. A reader cannot perceive an exceedance of a
limit that was never printed, or search for a word that was never used. **The absence is
the design.**

So on every document ask: what was removed, what was kept, what does that choice reveal
about who reviewed it, and what is the reader thereby prevented from seeing? Then ask what
breaks if you're wrong.

---

## IV. The bar: Jobs and Abloh

Both must pass. Different tests; failing either fails the design.

### Jobs — subtraction

- **A mother has ten seconds.** She should know what's wrong with her water and what to do
  before deciding whether to keep reading. If not, the design failed however complete it is.
- **Say no.** A finished section that dilutes the point gets cut, not kept out of sympathy
  for the work. This page has been cut down twice for exactly this.
- **One idea per screen.** Competing ideas mean neither lands.
- **Never brain-dump.** Comprehensiveness is the failure mode, not the defense. Depth is
  *reachable*, never *imposed*.
- **Details nobody will notice:** tabular numerals, a redaction bar sized to the text it
  covers, page-anchored deep links.

### Abloh — the readymade

- **Readymade over recreation.** *The governing principle here.* Publish the original
  artifact — the actual email, the actual PDF — not a beautiful HTML reconstruction. A
  retyped email is a claim; the original file is evidence. An entire hand-built HTML
  correspondence archive was deleted from this repo for violating this.
- **The 3% rule.** Recontextualize, don't reinvent. The site has a visual language (§ VII);
  new sections adopt it and shift it slightly. Novel components are a smell.
- **Quotation marks as device.** The government's own words, in quotes, do the accusing.
  Never editorialize where a verbatim quote is available and more damning.
- **Tourist and purist.** The ten-second reader and the person who wants all 25 pages must
  both be served by one page — the first by hierarchy, the second by a door at the bottom.

**Synthesis:** restraint on the surface, total depth underneath, and the artifact — not our
prose — is the message.

---

## V. Voice

Declarative sentences. Terminal periods in headings ("The word they took out."). Serif for
what is said, mono for what is measured.

**The facts are lurid enough that any adjective we add makes them less credible.** State the
number, name the official, cite the page, stop. Never write "shocking," "disgusting,"
"scandal," "cover-up," or "poisoning" in published copy — write what the document says and
let the reader arrive at the outrage themselves.

Supported conclusions are stated plainly. Unsupported ones are marked open, or put to the
officials as questions ("why won't they tell people to filter?"). Associations are always
labeled as associations. The site's authority comes from visibly refusing to overclaim —
which is also the best legal posture.

---

## VI. Shipping

**Repo:** `github.com/fluffybear1016/riganowater` → GitHub Pages → `riganowater.com` (CNAME).
`index.html` (~10 MB, the entire app), `documents/` (published originals), `share-card.jpg`,
`CNAME`, `README.md`.

### This session cannot `git push`

Clone works (public); push fails auth and the API returns *"GitHub access to this repository
is not enabled for this session."* **Don't burn attempts retrying.** Ship via the browser —
GitHub is an authorized app.

### Browser ship procedure

1. Copy outputs to `/mnt/user-data/outputs/` — `file_upload` only reads paths shared with
   the session.
2. `ToolSearch` the chrome tools → `tabs_context_mcp{createIfEmpty:true}`.
3. Navigate to `github.com/fluffybear1016/riganowater/upload/main`
   (`/upload/main/<folder>` targets a subfolder; it's created if absent).
4. `find` the file input → `file_upload` with absolute paths. Calls accumulate; keep each
   batch under ~10 MB.
5. `find` the commit-summary textbox → `form_input`.
6. **Submit by coordinate, not by `ref`.** A `ref` click on GitHub's green "Commit changes"
   button silently focuses without submitting — this cost a full retry cycle. **Screenshot,
   locate the button in that screenshot, click its center.** Never reuse a hardcoded
   coordinate: the button moves with staged-file count, scroll and window size.
7. Confirm: `git fetch origin main && git log --oneline origin/main -1`.

Commits land under the owner's account, so **local commits are redundant** and create
unverified-signature noise. After a successful ship, confirm `git status --porcelain` is
empty, then `git fetch origin main && git checkout -B main origin/main`. (Don't use
`git reset --hard` as a habit — if the gate is skipped it destroys uncommitted work, and it
ignores untracked files, which is exactly what the ship procedure produces.)

### Deploy verification — always

```bash
curl -s https://riganowater.com/index.html | sha256sum   # must equal local
```
Then every published PDF: HTTP 200 **and** byte-identical to the verified local copy. Pages
takes ~1–3 min. `miamidade.gov` returns **403 to HEAD** — bot-blocking, not a dead link;
re-test with `curl -sL -A 'Mozilla/5.0'`. **Also verify link *text* names the document it
actually opens** — one anchor labeled "WASD 2024 report" points at the 2025 PDF.

---

## VII. Editing `index.html`

**Never** read it whole; never hand-edit. One file, all HTML/CSS/JS. **The longest single
line is ~8.9 MB** (an embedded base64 video poster) — slicing "a line" can blow your context.

### Architecture

- `GROUPS` (**≈ line 3403**) maps a view → an **ordered array of section keys**. It defines
  only `investigations, evidence, about, protocols`; `score` and `map` are legal hashes
  rendered by other code.
- `SYN` — synthetic sections, one key per **single line**, as a single-quoted JS string.
  Keys start `__`. Inner quotes are `"`; apostrophes are entities *or* `\'`.
- Non-`__` keys are real DOM elements elsewhere, relocated at runtime by `build()`.
- `rwView(name)` clears `#rwPanelBody` (`innerHTML=''`) and rebuilds from the array each
  call. Nothing persists across view switches.
- **Order is NOT only in `GROUPS`.** `SYN['__ev_full']` (≈ line 3445) concatenates
  `__ev_notice + __ev_words + __ev_safeword + __ev_walworth` — those four are ordered there.
  Reordering them in `GROUPS` does nothing.
- Hash routing accepts only `/^(investigations|evidence|protocols|about|score|map)$/`.
  Sub-sections aren't URL-addressable; in-page jumps use JS (`rwJumpDocs()` → `#ev-docs`).
- Several `SYN` keys are **dead** (defined, never rendered): `__drop`, `__ev_how`,
  `__inv_hero`, `__inv_big`, `__ev_hero`, `__ab_hero`, `__pr_04`, `__pr_05`, `__ab_methods`.
  Check membership in a `GROUPS` array before editing one.

### Patching method

Write a Python script doing exact replacement with **`assert src.count(old) == 1` before
every substitution** — a silent no-match in a 10 MB file is invisible. Then `node --check`
every inline `<script>`, serve locally, exercise the view in Playwright, and screenshot at
**1280 and 390** before shipping.

### Visual language (the evidence panel is a light "paper" surface)

| Token | Value | Note |
|---|---|---|
| Panel bg | `#f4f4f1` | cards white, 20px radius, soft shadow |
| Accent | `#0b7488` | teal. **Not** `--cyan` `#35d0e8` — dark-theme only, muddy on white |
| Alert | `#c0362a` | kicker dot, key documents, exceedances |
| Heading + body ink | `#1a1d21` | `premiumPolish` overrides earlier values; `#12212f` survives mainly as rules/bold |
| Muted | `#5b6570` | `.wsub` |
| Headings | Fraunces serif, weight 500 | `.wsec h2` |
| Labels/dates/data | mono, uppercase, `letter-spacing` `.14–.18em` | `.rv-kick` uses `.18em` |

Sections are `<section class="wsec">` opening with a `.rv-kick` kicker bar.

**Specificity gotcha:** the live rule is `.wsec a:not(.tg-btn):not(.shbtn){color:#0b7488}` —
**two** negations. A new anchor class must be written
`.wsec a.myclass:not(.tg-btn):not(.shbtn)`, or it merely ties and wins by source order.

**Known non-issue:** console shows `L is not defined` and CDN `ERR_CONNECTION_RESET` in the
sandbox — Leaflet is network-blocked here. Pre-existing, environmental. Don't chase it.

---

## VIII. Verified ground truth

Verified by rendering source pages. **Re-verify before re-asserting; never paraphrase from
memory.**

**Miami-Dade County Attorney → Board of County Commissioners, Nov 7, 2023**
(`documents/2023-11-07_...pdf`, Bates MDC001–025):
- **p. 7** — *"because the County filed its lawsuit against 3M in 2020, and because the
  levels of PFAS in the County's drinking water supply relative to the projected state and
  federal MCL are high, the County will be entitled to an additional 25 percent 3M
  Litigation Bump and a 4X 3M Regulatory Bump"*
- **p. 7** — recovery estimated at **~$199 million**
- **p. 5** — remediation *"from the high hundreds of millions of dollars to $3 billion"*
- **p. 4** — PFAS detected in the drinking water since quarterly testing began in **2019**

**Miami-Dade 2025 Water Quality Report** —
`miamidade.gov/resources/water/documents/2025-water-quality-report.pdf`:
- **p. 2** — *"outreach efforts to communicate **the excellence** of our drinking water"*,
  set over a **full-page photograph of a young girl holding out a glass of water**
- **p. 2, next paragraph** — *"Our number one goal is to provide you and your family a
  **high-quality** and dependable supply of drinking water."* Prior editions read *"a
  **safe** and dependable supply."* Only "safe" was removed. ⚠ The 2023/2024 PDFs are not in
  this tree — **re-download and render before restating the years covered.**
- Serves **more than 2.8 million people** daily
- **p. 8 (English table)** prints Federal MCL **4** against PFOS **33 (7–33)** and PFOA
  **13 (3–13)**. ⚠ **p. 18 (Spanish) prints different, prior-year figures** — PFOS 31 (7–31),
  PFOA 16 (3–16), year tested 24. **Always cite p. 8 English**, and never quote a bilingual
  report's translated half without checking it against the original half.
- No advice anywhere to filter; every "filtration/reverse osmosis" mention describes the
  utility's own plant processes.

**City of Miami Beach Water Quality Report — CY2024 edition** (both local copies are this
edition, despite one being named `...-2025-final.pdf`; **never trust a filename's year —
confirm from a rendered page header**):
- **p. 3** — *"The data confirms that the city's drinking water quality continues to be
  excellent — not just safe for our more than 80,000 residents but also for the millions of
  visitors who travel to Miami Beach each year."* **Quote in full, or quote only
  "excellent"** — see § I.
- **p. 2** — *"number one goal is to provide you and your family a **safe** and dependable
  supply."* The City still uses "safe"; the County no longer does. **Do not conflate them.**
- **p. 8** — additional-monitoring table: PFOS **38 (ND-38)**, PFOA **30 (ND-30)**, with the
  **Federal MCL column printed "N/A"**, footnoted *"tested voluntarily and which are not
  currently regulated,"* under an intro sentence reading *"All are below maximum contaminant
  levels allowed."* The federal limit of 4 ppt was set April 2024, before publication.
  ⚠ The table's own intro says these are parameters detected in **Miami-Dade's** water — the
  City buys 100% wholesale. Attribute accordingly.
- The acronyms **PFAS / PFOS / PFOA appear on none of the 24 pages** — only the chemical
  names spelled out (verified across both copies, all pages).
- No household filtration advice; its only "filter" reference is the aquifer being naturally
  filtered through sand and rock.

**Context:** federal MCL for PFOA and PFOS = **4 ppt** (2024 rule). EPA 2022 interim health
advisories = **PFOA 0.004 ppt / PFOS 0.02 ppt** — *this order is a known trip hazard; state
the chemical beside its number every time.* Health-based goal = **0**. IARC classified PFOA
a **Group 1 human carcinogen** in 2023.

**Thyroid cancer — heavily sourced on the site; use its numbers, not a paraphrase.**
County-wide Miami-Dade runs **18.1 per 100k vs the U.S. 12.9** (≈ +40%), ranking **#2 of
Florida's 67 counties** (NCI State Cancer Profiles, 2018–22). Place-level, **47 of 48**
municipalities exceed the national rate, averaging ~1.8×, reaching **2.2–2.8×** in the
airport foam corridor — North Bay Village 36.3, Miami Springs 30.6, Doral 28.5 per 100k
(**Florida Cancer Data System / SCAN360**, age-adjusted 2016–20; U.S. = SEER/USCS 12.9).
The mechanism study is **Wild et al., University of Miami / Sylvester, IJERPH 2025;22(8):1290
(DOI 10.3390/ijerph22081290)** — ~14,144 Florida cancers, 2011–2020, residence within 5 km of
a PFAS site significantly predicts thyroid cancer (β=28.2, p<0.001). The site also runs its
own Kulldorff Poisson scan (299 Monte-Carlo replications) and states the Doral
denominator-artifact caveat unprompted.

⚠ **Do not restate this loosely.** An earlier draft of this file paraphrased it as "more than
double the U.S. rate" and wrongly flagged it as unsourced — see § II on why. Quote the site's
own figures with their units, matrix and date range, or link to its Health section.

---

## IX. Redaction and document integrity

**Public officials acting officially are never redacted** — names, government email addresses
and words are public record under Fla. Stat. ch. 119, and redacting them would gut the
evidentiary value.

**Private citizens are protected.** In the County thread: Richard "Rick" Cava
(`rickcava@gmail.com`) — name, email, greetings, sign-offs, **and identifying references**,
including the relationship phrases "my sister in law" and "my neighbor," because a
relationship description identifies a person as surely as a name. Not to be confused with
**Mayor Daniella Levine Cava**, a public official, never redacted.

**Never alter a received government original.** Its value is that it is the file as issued;
changing anything — including metadata — weakens that and breaks hash comparison. **Scrub
metadata only on files the Institute generates, converts, or redacts.** (The County Attorney
memo correctly retains its original metadata; the Gmail printouts and format conversions are
ours and are scrubbed.)

**Redaction must be real** — a drawn black rectangle leaves the text selectable underneath:

```python
page.add_redact_annot(rect, fill=(0.07, 0.13, 0.18))
page.apply_redactions(graphics=fitz.PDF_REDACT_LINE_ART_NONE)  # per page
doc.set_metadata({}); doc.del_xml_metadata()
doc.save(out, garbage=4, deflate=True, clean=True)             # NEVER incremental
```

- `apply_redactions()` is **per page** — loop it.
- Pass `PDF_REDACT_LINE_ART_NONE` on table pages; PyMuPDF ≥ 1.24 otherwise deletes any rule
  or border the box merely touches.
- An incremental save leaves the original text objects recoverable — the exact failure this
  is written to prevent.
- Shrink boxes vertically (`y0+0.4, y1-0.4`) so neighbouring lines survive.
- **Verify on the saved output**: extract text and assert zero matches, *then render the
  affected pages and look at them.* Confirm `set_metadata({})` actually cleared — it
  silently fails on some files.

The site must state plainly what was redacted and why. It currently does.

---

## X. Pre-flight — every change, no exceptions

1. Every factual claim traced to a **rendered, visually-read** source page (dpi ≥ 120 for
   tables), with document and page number recorded.
2. **An adversarial subagent has tried to disprove the work** and its findings are resolved.
3. Quotes verbatim and **complete to the end of the construction** — no truncation that
   invents a contrast.
4. Any absence claim verified by reading **every** page, in **every** available copy.
5. Every link resolves (200), **link text names the document it opens**, every PDF
   byte-identical to its verified local copy.
6. Redactions verified on the saved file by extraction **and** by eye; metadata policy (§ IX)
   applied correctly.
7. `node --check` clean on all inline scripts; rendered at 1280 and 390; fold/jump
   interactions actually exercised.
8. **Ten-second test:** does a mother learn what's wrong and what to do, without scrolling?
9. **Subtraction test:** what can be cut? Cut it.
10. Live deploy hash-verified after shipping.

When something is uncertain, say so on the page. This site's authority comes from visibly
refusing to overclaim.
