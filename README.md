# 25 ways to land one finding

Twenty-five landing pages for one idea, plus a gallery, built for
**MPCS 51238 Design, Build, Ship — Assignment 1: Accelerated Prototyping**.

The idea is a research project: *why text-conditioned 3D medical models can tell
that a lesion exists but fail to localize it once it is small.*
[The paper and code are here.](https://github.com/rajhansini/Diagnosing-Small-Lesion-Grounding-Failure-in-Text-Conditioned-3D-Medical-Localization)

## Looking at it

Open `index.html`. There is no build step, no package manager and no server —
every page is a single self-contained HTML file with its CSS inline. The gallery
previews each version in a live iframe, so opening it from the filesystem works
the same as opening it from a host.

```
index.html      the gallery: 25 previews, each with what changed and why
v/v01.html      one version per file
...
v/v25.html      the final
AGENTS.md       the brief: idea, audience, constraints, process
```

## How it was made

[`EXPLAIN.md`](EXPLAIN.md) walks through the design process, which directions were
dropped and why, and where the agent was pushed back on. The gallery also lists the
fifteen directions that were built and retired, each with the commit it can be
recovered from.

## The process

**v01–v13, going wide.** Thirteen genuinely different directions, including
several that were always going to fail: a PACS reading room, a clinical incident
report, a Swiss grid, a lab notebook, a terminal transcript, a brutalist
manifesto, a magazine spread, a scrolling data story, a before/after slider, a
nineteenth-century anatomical plate, a quiet single column, a conference poster,
and a bedside observation chart.

**v14–v19, cross-breeding.** Six combinations of what survived. The Swiss grid
met the scan overlay; the terminal's narrowing sequence met the quiet column; the
comparison slider met the plotted chart.

**v20–v25, converging.** The metaphors come off, everything moves onto one grid,
the evidence table becomes the only control, the copy is cut, and the last two
passes are contrast, print and audience.

Each version is its own commit, and the commit message says what changed and why
— including the bugs that only showed up when the page was actually rendered and
measured, which is most of them.

## The final

`v/v25.html`. One screen carries the headline, the overlay figure, the nine
measured cells and the ratio that matters. Below it, four hypotheses with three
ruled out. The only interaction is the evidence table: its nine numbers are
buttons, and every state they can reach is a measurement rather than an
interpolation.

## Constraints it was built under

Plain HTML and CSS. JavaScript only where it earns its place — three versions
use it, none of them require it. Google Fonts is the only external resource.
Nothing is stored, nothing is sent anywhere, and there is no API behind any of it.

---

Raj Hansini Akara · University of Chicago
