---
layout: lab
title: "Part 3: Compare the two structures"
nav: lab
permalink: /lab/part-3/
---

**This is the comparison that made the discovery.** An experimental CRISPR
protein against a predicted structure of an uncharacterized metagenomic protein.

You will use the RCSB PDB's **Pairwise Structure Alignment** tool. It runs in
the browser, needs no account, and can fetch AlphaFold models directly.

1. Go to <https://www.rcsb.org/alignment>
2. Set up two structures:

   | | Source | Identifier |
   |---|---|---|
   | Structure 1 (reference) | PDB entry | `6IFN`, the **Csm3** chain from Part 1 |
   | Structure 2 | AlphaFold DB, by UniProt accession | `X1U2U4` |

   **You must select the Csm3 chain for Structure 1.** `6IFN` contains the
   whole Csm complex, so after you enter it the tool asks which chain to use.
   Do not leave it on whatever it picks by default: open the chain menu and
   choose a chain labelled **Csm3** (any of the three copies works).

   For Structure 2, use the tool's option to fetch predicted coordinates from
   the AlphaFold database by UniProt ID, so you do not have to download
   anything.

3. Leave the alignment method on the default, **TM-align**. (jFATCAT rigid and
   flexible, CE, CE-CP and Smith-Waterman 3D are also available — you will use
   one of them in Part 4.)
4. Click **Compare**.

The results page gives you two linked views: a **3D superposition** in the Mol\*
viewer, and a **1D sequence alignment** showing which residues were matched.

<div class="record" markdown="1">

**Record all four numbers:**

| Metric | Your value | What it means |
|---|---|---|
| **TM-score** | | How well the overall folds match, 0–1 |
| **RMSD** | | Average distance (Å) between matched residues after superposition |
| **Aligned residues** | | How many residues could be structurally matched |
| **% identity** | | Sequence identity *within the structural alignment* |

</div>

{:start="5"}
5. Rotate the superposition. Look at where the structures overlap and where they
   diverge.

## What the authors got

Table S1 of Yoon et al. 2026 reports this exact pair, aligned with a different
program (DALI):

| Metric | Published (DALI) |
|---|---|
| Z-score | 11.7 |
| RMSD | 3.8 Å |
| Aligned length | 157 residues |
| Target length | 178 residues |
