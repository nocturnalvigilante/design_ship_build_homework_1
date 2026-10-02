# AGENTS.md

## The idea

A landing page for a research project: **why text-conditioned 3D medical models can
tell that a lesion exists but fail to localize it once it is small.**

Repo: github.com/rajhansini/Diagnosing-Small-Lesion-Grounding-Failure-in-Text-Conditioned-3D-Medical-Localization

## Who it is for

Researchers in medical imaging and vision-language, and graduate admissions readers.
Technical, skeptical, short on time. They have seen a hundred project pages and will
leave in five seconds if the claim is not in front of them.

## What a visitor should do

1. Understand the finding within fifteen seconds of landing.
2. Open the paper or the repo.

Nothing else. No newsletter, no contact form, no scroll-to-learn-more.

## Material to draw on

The strongest lines, use them, do not invent new claims:

- Text-conditioned 3D models detect that a lesion exists but collapse to oversized,
  imprecise regions when it is small.
- Localization degrades monotonically with lesion size: **2.4x to 14.4x** Dice loss
  from large to small.
- A supervised U-Net degrades only **1.2x to 1.3x**, so small lesions are learnable.
  It is the text conditioning that fails.
- Swapping PubMedBERT for **random vectors** changes almost nothing. *"The query
  functions as an opaque class identifier that happens to be spelled in English."*
- The winning fix is the simplest one: reweight window contributions toward their
  centres. **+0.145 Dice, no retraining.** Small enhancing tumour went from 0 to 7
  of 21 patients.
- 171 paired Wilcoxon tests, Benjamini-Hochberg corrected. 9 of 9 comparisons
  replicated across three independent splits.
- *"A shared confound is not a cancelled confound."*
- Data: BraTS2020, 369 patients, 128^3 volumes.

## Constraints

- Plain HTML and CSS. JavaScript only where it earns its place.
- **No frameworks, no build step, no external APIs, no data storage.** If you are
  about to suggest a package, do not.
- Google Fonts is the only permitted external resource.
- Every version is one self-contained file at `v/vNN.html`.
- Every version carries a link back to `../index.html`.
- `index.html` is the gallery: 25 thumbnails, each linking to its version, each with
  a one-line note on what changed and why.

## Process

- v01 to v19 go wide. Genuinely different layout, audience framing, mood, era, tone.
  **Changing only colours or fonts is not a new direction and does not count.**
- v20 to v25 narrow down: take the one idea that survived contact with the audience,
  combine the pieces of earlier versions that worked, and refine until v25 is the one.
  Each of these states what changed from the version before it and why.
- Commit after each version. The history is part of the grade.
- At least 20 of the 25 must be unique against roughly 700 sites from the class, so
  avoid every obvious default: no purple-to-blue gradient hero, no cream background
  with a serif display face, no centred everything, no rounded cards with an accent
  bar. The subject is medical imaging, which affords looks nobody else will reach for.

## Due

Tuesday 6 October, 5:30 PM. Vercel URL plus GitHub URL, submitted in Google Classroom.
