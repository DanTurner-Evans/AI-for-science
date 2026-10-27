---
layout: lab
title: "Lab: Is VIPR related to CRISPR?"
nav: lab
---

**Comparing a CRISPR protein to a Vipr protein using an AlphaFold prediction**

*Estimated time: 90 minutes. No programming or software installation — browser only.*

## The question

In 2026, a group at Berkeley reported a new kind of RNA-guided system called
**VIPR** (Viral Interference Programmable Repeat), encoded by bacteriophages.
They argued it is **ancestral to CRISPR-Cas** — that the machinery bacteria use
for adaptive immunity may have originated in warfare between viruses.

How do you make a claim like that? The Vipr protein and CRISPR proteins share
almost no recognizable sequence similarity. Standard tools for finding related
proteins — BLAST, HMM searches — compare sequences, and they fail here.

But **protein structure is conserved long after sequence has diverged.** Two
proteins can descend from a common ancestor, retain the same fold, and share
barely 10% of their amino acids. If you only look at sequence, you see nothing.
If you look at shape, you see the relationship.

There is a catch. When the authors made this discovery, **nobody had ever
determined the structure of a Vipr protein.** No crystal, no cryo-EM map,
nothing. So they used an **AlphaFold prediction** instead — and the entire claim
about the origin of CRISPR rested, at first, on a computer's guess about a
protein's shape.

In this lab you will retrace that exact reasoning:

1. Pull up a real, experimentally determined CRISPR protein structure
2. Look up the predicted structure of a Vipr protein in AlphaFold
3. Compare them — **this is the comparison that made the discovery**
4. Then look up the Vipr structure that was solved experimentally *afterward*,
   and find out whether the prediction was right

## The lab, step by step

Work through the pages in order. Start with the background — it explains a
naming trap that will otherwise trip you up in Part 1.

<ul class="lab-parts" markdown="0">
{% for step in site.data.lab %}
  <li><a href="{{ step.url | relative_url }}">
    <span class="tag">{{ step.label }} · {{ step.time }}</span>
    <span class="title">{{ step.title }}</span>
    <span class="meta">{{ step.summary }}</span>
  </a></li>
{% endfor %}
</ul>

Keep a document open as you go. Each part has a **Record** list and numbered
**Questions** (1–17, numbered continuously across parts); you will hand in your
answers at the end.

## Learning goals

By the end of this lab you should be able to:

1. Retrieve and inspect a macromolecular structure in the RCSB PDB
2. Retrieve an AlphaFold prediction and read its per-residue confidence scores
3. Explain why structural comparison detects homology that sequence comparison
   misses
4. Run a pairwise structural alignment in the browser
5. Interpret a TM-score, RMSD, alignment length, and percent identity — and say
   which of them matters for an evolutionary claim
6. Articulate the difference between a predicted structure and a measured one,
   and what each can and cannot establish

## What you'll use

All free, all in the browser, no account needed:

| Resource | Used in | What it is |
|---|---|---|
| [RCSB Protein Data Bank](https://www.rcsb.org) | Parts 1, 3, 5 | Archive of experimentally determined structures, with the Mol\* 3D viewer |
| [AlphaFold Protein Structure Database](https://alphafold.ebi.ac.uk) | Part 2 | Pre-computed AlphaFold predictions for over 200 million proteins |
| [RCSB Pairwise Structure Alignment](https://www.rcsb.org/alignment) | Parts 3, 4 | Aligns two structures and reports TM-score, RMSD and more |

## What to hand in {#hand-in}

1. Your completed metrics table from Part 3, plus the **shareable results URL**
2. A screenshot of the Part 3 superposition, with the thumb and G-loop labelled
   if you can identify them
3. Written answers to questions 1–16
4. Two or three sentences: **does the structural evidence convince you that VIPR
   and CRISPR are related? What would change your mind?**

## If something goes wrong

- **Your alignment looks bad.** Check your `6IFN` chain before blaming the
  software. It must be **Csm3, about 220 residues**. A ~126-residue chain is
  Csm2, the wrong protein (see [Part 1]({{ '/lab/part-1/' | relative_url }})).
- **A UniProt search for `X1U2U4` fails.** The UniProt entry has been removed,
  but AlphaFold still serves the model. Go straight to
  <https://alphafold.ebi.ac.uk/entry/X1U2U4>.
- **The RCSB alignment tool is down.** Alternatives that accept PDB codes:
  [US-align](https://zhanggroup.org/US-align/),
  [PDBeFold](https://www.ebi.ac.uk/msd-srv/ssm/), or
  [Foldseek](https://search.foldseek.com) (a fast search tool rather than a
  pairwise aligner, and less sensitive).

## Sources

- Yoon et al., "A noncontiguous code for RNA-guided DNA recognition at the
  origin of CRISPR-Cas," *Science* **393**, 1230–1235 (2026) — the discovery
- Yoon et al., "VIPR RNA-guided DNA recognition by noncontiguous geometric
  triplex formation," *Science* **393**, 1236 (2026) — the cryo-EM structures
- Guo et al., "Structure Studies of the CRISPR-Csm Complex Reveal Mechanism of
  Co-transcriptional Interference," *Cell* **176** (2019) — `6IFN`
- Varadi et al., "AlphaFold Protein Structure Database," *Nucleic Acids Res.*
  **50**, D439–D444 (2022)
- Bittrich et al., "RCSB Protein Data Bank: exploring protein 3D similarities via
  comprehensive structural alignments," *Bioinformatics* **40**, btae370 (2024)
- Zhang & Skolnick, "TM-align," *Nucleic Acids Res.* **33**, 2302–2309 (2005)
