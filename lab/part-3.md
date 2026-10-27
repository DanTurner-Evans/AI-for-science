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

   The tool has an option to fetch predicted coordinates from the AlphaFold
   database for a given UniProt ID — use it, so you do not have to download
   anything. If the tool gives you a chain dropdown for `6IFN`, pick **Csm3** by
   name; that sidesteps the numbering problem entirely.

3. Leave the alignment method on the default, **TM-align**. (jFATCAT rigid and
   flexible, CE, CE-CP and Smith-Waterman 3D are also available — you will use
   one of them in Part 4.)
4. Click **Compare**.

The results page gives you two linked views: a **3D superposition** in the Mol\*
viewer, and a **1D sequence alignment** showing which residues were matched.

**Record all four numbers:**

| Metric | Your value | What it means |
|---|---|---|
| **TM-score** | | How well the overall folds match, 0–1 |
| **RMSD** | | Average distance (Å) between matched residues after superposition |
| **Aligned residues** | | How many residues could be structurally matched |
| **% identity** | | Sequence identity *within the structural alignment* |

{:start="5"}
5. Rotate the superposition. Look at where the structures overlap and where they
   diverge.
6. **Bookmark or copy the results URL** — it is shareable, and you will hand it
   in.

> **Numbers look poor?** Before anything else, confirm the `6IFN` chain you
> used is ~220 residues long. A ~126-residue chain is Csm2, not Csm3 — go back
> to [Part 1]({{ '/lab/part-1/' | relative_url }}) and reselect.

## What the authors got

Table S1 of Yoon et al. 2026 reports this exact pair, aligned with a different
program (DALI):

| Metric | Published (DALI) |
|---|---|
| Z-score | 11.7 |
| RMSD | 3.8 Å |
| Aligned length | 157 residues |
| Target length | 178 residues |

## Questions

{:start="3"}
3. Your **RMSD** and **aligned residues** should be in the same neighborhood as
   the published values. Are they? They will not match exactly — TM-align and
   DALI use different algorithms, and you are using model v6 rather than v4.
4. You cannot reproduce the **Z-score** with this tool at all. Why not? (Hint: a
   Z-score is a statistic about one specific program's score distribution.) What
   does this tell you about quoting a single number from a paper as though it
   were a property of the proteins?
