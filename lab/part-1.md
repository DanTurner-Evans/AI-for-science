---
layout: lab
title: "Part 1: Pull up the CRISPR protein in the PDB"
nav: lab
permalink: /lab/part-1/
---

1. Go to the **RCSB PDB**: <https://www.rcsb.org>
2. Search for **`6IFN`** and open the entry.
3. Read the title: *Crystal structure of Type III-A CRISPR Csm complex*. This is
   the Csm complex described in the
   [background]({{ '/lab/background/' | relative_url }}), from the bacterium
   *Streptococcus thermophilus*, solved by X-ray crystallography at 2.90 Å.
4. Find the **Macromolecules** section and list the chains. You should be able
   to pick out Csm1, Csm2, Csm3, Csm4, Csm5 and an RNA chain. Note that **Csm3
   appears several times** — those are the stacked backbone copies.
5. We want **one Csm3 chain**, because Csm3 is Cas7. The published search used
   **author chain E**. See the warning below before you select it.
6. Open the 3D viewer and display that chain on its own (use the chain selector
   in the Mol\* viewer).

> ### ⚠️ Two chain-numbering systems
>
> PDB entries can carry **two sets of chain IDs**, and `6IFN` is one where they
> disagree. RCSB shows them as `D [E]` — the bare ID is the *entity* (label) ID,
> the one in brackets is the *author* ID.
>
> | Protein | Entity chains | Author chains | Length |
> |---|---|---|---|
> | **Csm3** (what we want) | B, D, G | **E**, F, G | **220 aa** |
> | **Csm2** (wrong protein) | **E**, F | C, D | **126 aa** |
>
> **So "chain E" means Csm3 under author numbering, and Csm2 under entity
> numbering.** Do not type "E" and trust it.
>
> **The reliable check is length.** Whatever chain you select, confirm it is
> **about 220 residues**. If it is around 126, you have Csm2 — the alignment in
> Part 3 will look bad for reasons that have nothing to do with biology.
>
> Any of the three Csm3 copies works; the paper used author chain E.

**Record:**
- How many protein chains does `6IFN` contain in total? How many are Csm3?
- Which chain ID did you use for Csm3, and under which numbering system?
- **How long is your chain? It must be ~220 residues.** If it is ~126, you have
  Csm2 — go back and reselect.
- Looking at that chain alone, can you see a protruding hairpin that would reach
  over an RNA? Sketch or screenshot it. This is the thumb.

> **Why one chain and not the whole complex?** The published search used a single
> Cas7/Csm3 protomer — `6ifnE` — as its query. The stacking is what builds the
> backbone, but one protomer carries the fold we are comparing.

**This structure is a measurement.** Someone grew crystals, shot X-rays at them,
and solved the phases. Keep that in mind, because the next structure is not.
