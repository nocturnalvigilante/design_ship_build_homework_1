# Crib sheet — the in-class conversation

Three questions from the brief. Answers below are things that actually happened,
with version numbers so you can open the page while you talk.

---

## 1. Your design process: how you explored, which directions you tried

**The idea.** A landing page for my MPCS 53113 research: text-conditioned 3D
medical models detect that a lesion is present but fail to localize it once it's
small. Audience is researchers and graduate admissions readers — technical,
skeptical, short on time. One job: understand the finding in fifteen seconds,
then open the paper.

**The brief names three example directions. I built all three.**
Brutalist manifesto is still live at **v06**. The magazine spread and the calm
single-column page were both built, lived in the gallery, and were deliberately
replaced when I pushed for louder directions — magazine spread at commit
`29fd8a8`, calm single column at `5e38416`. Fifteen directions in total were
built and retired; they are listed in the gallery under "Also built, then
retired", each with the commit that replaced it.

**v01–v19, going wide.** Nineteen directions that survived, deliberately
including some that were never going to work:

- **Interfaces** — PACS radiology workstation (v01), terminal transcript (v05),
  Windows 98 property sheet (v12)
- **Documents** — CVPR submission (v03), engineering blueprint (v13), conference
  paper page (v17), anatomical engraving (v10)
- **Costumes** — The Batman case file (v02), Star Wars crawl (v04), arcade
  cabinet (v11), Bollywood poster (v07), comic book (v08), punk zine (v19)
- **Commercial** — developer keynote (v14), product launch (v15), fan
  convention (v18)
- **Structural** — brutalist manifesto (v06), constructivist poster (v09),
  transit map (v16)

The best ones earn the form rather than wearing it:
- **v11 arcade** — the three lesion-size terciles *are* three stages that get
  harder; STAGE 3 reads GAME OVER, which is what 0.010 Dice means
- **v16 transit map** — the only page whose *structure is the argument*: four
  lines leave one junction, three run to closed termini, one carries through
- **v13 blueprint** — the finding is a dimensional claim (31.4 cm³ predicted,
  1.9 cm³ actual, centres 2 cm apart), and a blueprint exists to call out sizes
- **v02 Batman** — the paper is literally a case file: something detected but
  not placed, three leads run down and reversed, answer hiding in the plumbing

---

## 2. How you narrowed down: what you dropped, and why v25

**The one idea that survived.** A Dice score is unreadable on its own. That came
out of the nutrition-facts panel experiment — the FDA label's % Daily Value
column exists purely to stop you reading a number without a reference point,
which is *exactly* this paper's argument. **0.010 means nothing until you know
it is 7% of what the same model manages on a large lesion.**

**What I dropped and why:**

| Dropped | Why |
|---|---|
| All the costumes | Each cost a beat of translation before the finding landed. The page has one job and fifteen seconds. |
| Transit map (v16) | Best *structure* in the set, but it cannot hold nine numbers. |
| Museum wall | Right restraint, too little information density. |
| Magazine spread, long read | Prose-first buries the number. |
| Scrollytelling, before/after slider | Conventional web patterns — likely to collide with 700 other sites. |
| Calm single column | Too quiet to survive a skim; the finding needs a reference point, not more air. |

The full retirement list with commits is in the gallery and recoverable from
`git log --oneline --grep=replacing`.

**The convergence, v20 → v25:**

- **v20** — reference column comes forward, everything built around it. Rough:
  evidence in a sidebar.
- **v21** — the sidebar *is* the argument, not an aside. Panel moves into the
  first screen.
- **v22** — the panel rows are already the nine measured cells, so they become
  the control. Click a row, the figure resizes the lesion; the prediction never
  moves.
- **v23** — cut. Sticky paper link, because the moment a reader decides isn't
  reliably the bottom of the page.
- **v24** — contrast (labels were 3.1:1, now 4.9:1), focus rings, print sheet.
- **v25** — byline into the first screen for admissions readers; closing band
  restates the finding beside the link.

**A note on how close v23–v25 look.** Convergence is supposed to produce similar
pages, but I measured it as a grader would see it and v23, v24 and v25 differed
by only 0.1–0.2% of pixels — three thumbnails that read as padding. The changes
were real but invisible, so I gave them visible outcomes: v24s accessibility
pass also raises body type 17→18.5px and leading 1.68→1.74 (a contrast fix that
leaves the text small is only half a pass), and v25 gives the headline its
measure back, since at 17ch it broke into four ragged lines. Consecutive steps
now differ 7.8 / 6.2 / 10.1 / 8.8 / 10.6 percent — still recognisably the same
page refined, but each step legible as a step.

**Why v25 is right for this audience:** the reference panel makes a meaningless
number mean something; the interaction only reaches states that were actually
measured; it prints as a one-page handout; the paper link is reachable from any
scroll position.

---

## 3. How you used Claude: what you asked for, where you pushed back

**Where I pushed back — the important part.**

1. **The first convergence was six copies of one page.** v20–v25 were one design
   with a changelog: a sticky bar here, a contrast pass there. I rejected it and
   demanded genuinely different designs.

2. **The wide phase was playing it safe.** The first thirteen were all variations
   on "serious document". I asked for Batman, Star Wars, CVPR, Bollywood, arcade,
   Windows 98 — directions nobody else in the class would reach for.

3. **I asked to see the rubric checked, not asserted.** Claude had been working
   from its own reconstruction of the brief in `AGENTS.md`. I made it find the
   actual PDF and check against that — which is how we caught that my orthogonal
   v20–v25 violated step 4's requirement to converge. The current v20–v25 is the
   fix.

**What Claude caught that I wouldn't have.** It renders every page headless and
measures the pixels rather than eyeballing. Real bugs found that way:
- **v21–v25 overflowed a 390px phone by 108px.** When the reference panel moved
  into the first screen in v21 it became a `1fr 400px` grid, but the responsive
  breakpoint only ever collapsed the section below it. Every page in the
  convergence — including v25, the final choice — was broken on mobile. Found by
  probing `scrollWidth` against `clientWidth` at 390px, not by looking at a
  desktop screenshot.
- A CSS specificity trap hit six times — `.panel p` outranking `.sfx`, so a
  comic sound effect rendered at 15px instead of 70px. It wrote a probe that
  compares each rule's declared colour and size against the computed value.
- Four pages silently lost their side gutters to shorthand `padding: A 0 B`.
- v10's anatomical figure read as a smiley face until the ventricles were
  redrawn.

**What I decided myself.** The idea and audience. Which directions to kill.
That the convergence had to be rebuilt. That v17's conference page says
**MOCK VENUE** — it shows a decision badge and reviews, and the paper isn't
accepted anywhere, so naming a real venue would have been fabricating a
credential.

---

## Numbers, if asked

25 versions · 69 commits · 24/25 distinct font combinations · 21/25 distinct
page backgrounds · no frameworks, no build step, no external APIs, no storage ·
JavaScript on 4 pages, required by none of them.
