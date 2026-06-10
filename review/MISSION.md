# Mission

Grounds the arc check (Pass 2) and argument-integrity check (Pass 5). Over/underselling
and scope-drift are judged against this file, not against vibes.

## Research questions
*(Validation-led framing, confirmed in the initialization interview 2026-06-10.)*

1. **RQ1 (headline).** Can `asap` — with BIC-driven magnetic-component selection
   (`bic_scan.py`) and per-star line-list filtering (`check_region_quality.py`), applied
   **uniformly** to every star — yield a *self-consistent* set of atmospheric and magnetic
   parameters for a sample of M dwarfs from PolarBase that **validate** against the published
   values of Cristofari+2023 (arXiv:2310.08386) and Passegger+2019?
2. **RQ2 (second-tier).** For stars with both optical (NARVAL/ESPaDOnS) and NIR (SPIRou)
   data, do the retrieved parameters agree — i.e. is there **cross-instrument consistency**?
   (A property of the *results*, distinct from "self-consistent"; see CONTEXT.md.)

## Intended contribution
A homogeneous, reproducible retrieval of atmospheric **and** magnetic parameters for the
PolarBase M-dwarf sample, produced by one pipeline applied identically to every star and
benchmarked against existing SPIRou-based measurements. The per-star line-list filter + BIC
scan are framed as **methodological enablers** of that homogeneity, not as the headline
contribution. The work extends homogeneous magnetic measurements to the less-studied
new-targets campaign stars beyond the Cristofari overlap.

## Scope boundaries
- **In scope:** uniform atmospheric + magnetic retrieval across the sample; validation
  against Cristofari+2023 and Passegger+2019; cross-instrument (optical/NIR) consistency as
  a second-tier claim; expository explanation of the ZeeTurbo grid and the pipeline.
- **Explicitly out of scope** (the conclusion must not claim these):
  - **ZeeTurbo grid generation** — built by Cristofari and supplied; ch.3 is expository, no
    novelty claimed in grid construction.
  - **Sampler comparison** — `emcee` only; `dynesty`/`UltraNest` exist in `asap` but are not
    exercised here. No claim that sampler choice was evaluated.
  - **Absolute parameter accuracy** — the contribution is homogeneity/self-consistency +
    validation, not establishing ground-truth absolute accuracy.
  - **Rotation / activity physics** — no v sin i, P_rot, or activity-cycle modelling fitted;
    field measurements are not interpreted as a rotation–activity study.

## Audience
MSc Research Project (MRP), Leiden. Examiners: **supervisor + a second examiner, both
spectroscopy-literate**. Likely lines of attack: method rigour (BIC vs. Bayesian evidence
for component count; the post-hoc, no-re-MCMC nature of the scan), parameter degeneracies
(⟨B⟩ vs. v sin i, ζ_RT), the per-star line filter as a possible selection bias, and whether
"self-consistent" / the validation claim is overstated. Grilling weighted toward these.

## Author-owned grounding docs (authoritative — do not duplicate here)
- `CLAUDE.md` — central argument, method pegs (BIC scan, MCMC flags, line filter,
  wavelength conventions), factual-claim rules. The argument spine until `docs/argument.md`
  is written.
- `CONTEXT.md` — glossary and controlled terminology (asap, the sample, Cristofari sample,
  self-consistent vs. cross-instrument consistency, magnetic component, filling factor, …).
- `docs/notation.md` — symbols, units, parameter conventions.
- `docs/style_guide.md` — voice/tense, hedging tiers, sentence/paragraph rules.
- `docs/argument.md` — **not yet written** (CLAUDE.md promises it). Until it exists, this
  MISSION + CLAUDE.md carry the argument spine; when it lands, link to it here.
- No `docs/adr/` directory yet — no settled architecture decisions recorded as ADRs.

## Status (per chapter — calibrates which passes pay off)
| Ch | File | State |
|----|------|-------|
| 1. Introduction | `mainmatter/1-Introduction.tex` | stub (~9 ln) — skip until prose exists |
| 2. Observations & data reduction | `mainmatter/2-Observations.tex` | drafted (~80 ln) — full review |
| 3. ZeeTurbo grids | `mainmatter/3-ZeeTurbo.tex` | short/expository (~13 ln) — reverse-outline |
| 4. Methods (MCMC) | `mainmatter/4-Methods.tex` | **live draft (~296 ln)** — full review |
| 5. Results | `mainmatter/5-Results.tex` | **live draft (~117 ln)** — full review |
| 6. Discussion | `mainmatter/6-Discussion.tex` | stub (~13 ln) — skip until prose exists |
| 7. Conclusions | `mainmatter/7-Conclusions.tex` | stub (~6 ln) — skip until prose exists |

Review scope chosen at init: **everything with prose** — full passes on ch.2, 4, 5;
reverse-outline ch.3; skip the near-empty stubs (1, 6, 7) until they carry text.
