---
layout: default
title: "Lab: Is VIPR related to CRISPR?"
nav: lab
---

**Comparing a CRISPR protein to a Vipr protein using an AlphaFold prediction**

*Estimated time: 90 minutes. No programming or software installation — browser only.*

---

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

### What you need to know about the two proteins

**Cas7** is a component of class 1 CRISPR-Cas systems — the most common CRISPR
systems in nature. Cas7 proteins stack into a backbone that cradles the guide
RNA. They belong to a family called **RAMPs** (repeat-associated mysterious
proteins), defined by two features:

- a **thumb** domain — a protruding β-hairpin that reaches over the bound RNA
- a **glycine-rich loop (G-loop)** — a flexible loop contacting the RNA backbone

**Vipr** is the protein component of VIPR systems. Multiple copies oligomerize
along a VIPR RNA (**vrRNA**) to form a helical filament that recognizes DNA.

### What is a Csm complex?

Cas9 — the CRISPR protein you have probably heard of — is a single protein that
does everything: it holds the guide RNA and cuts the target. That is a **class
2** system, and it is the exception. Most CRISPR systems in nature are **class
1**, where the job is split across a **multi-subunit complex** of five or more
different proteins that assemble around the guide RNA.

The **Csm complex** is one of these. Specifically it is the interference complex
of **type III-A** CRISPR-Cas systems. Its subunits are named Csm1 through Csm5:

| Subunit | Role |
|---|---|
| **Csm1** | Large subunit; degrades single-stranded DNA and synthesizes signalling molecules that alarm the rest of the cell |
| **Csm2** | Small subunit; packs along the complex |
| **Csm3** | **The backbone.** Several copies stack in a helix, each gripping one segment of the guide RNA. Also cuts the target RNA |
| **Csm4** | Caps one end, holding the guide RNA's 5′ end |
| **Csm5** | Caps the other end |

Type III systems are unusual in that they attack a target *while it is being
transcribed* — they recognize the RNA and then destroy the DNA it came from.

**The part that matters for this lab is Csm3.** Multiple copies of one protein,
stacked into a helical filament, each binding one piece of a guide RNA. Compare
that to the description of Vipr above. The architecture is the thing you are
testing.

### A naming trap: Csm3 *is* Cas7

Type III CRISPR systems were discovered and named before anyone realized their
subunits were the same protein families found in other CRISPR types. So they
carry **two sets of names**: the system-specific one (Csm1–Csm5) and the generic
one used across all CRISPR types (Cas1–Cas13).

For our purposes:

- **Csm3 = Cas7** ← the backbone protein we want
- **Csm4 = Cas5**

The PDB entry labels its chains **Csm3** and **Csm4**. The VIPR paper calls the
same chains **Cas7** and **Cas5**. These are the same molecules under different
naming conventions, not different proteins. When this lab says "Cas7," look for
**Csm3** in the PDB entry.

---

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

---

## Part 1 — Pull up the CRISPR protein in the PDB (15 min)

1. Go to the **RCSB PDB**: <https://www.rcsb.org>
2. Search for **`6IFN`** and open the entry.
3. Read the title: *Crystal structure of Type III-A CRISPR Csm complex*. This is
   the Csm complex described above, from the bacterium *Streptococcus
   thermophilus*, solved by X-ray crystallography at 2.90 Å.
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

## Part 2 — Look up the Vipr protein in AlphaFold (20 min)

**AlphaFold** is a neural network that predicts a protein's 3D structure from
its amino acid sequence. The **AlphaFold Protein Structure Database (AFDB)**
holds pre-computed predictions for over 200 million protein sequences — nearly
every protein sequence known. No experiment is involved. These are the model's
best guesses.

1. Go to the **AlphaFold Protein Structure Database**:
   <https://alphafold.ebi.ac.uk>
2. Search for the accession **`X1U2U4`**, or go directly to
   <https://alphafold.ebi.ac.uk/entry/X1U2U4>
3. Look at what the entry tells you *before* looking at the structure:

   | Field | What you should see |
   |---|---|
   | Entry ID | `AF-X1U2U4-F1` |
   | Protein name | **Uncharacterized protein** |
   | Organism | **marine sediment metagenome** |
   | Length | 178 residues |

4. Sit with that for a moment. This is the protein that reopened the question of
   where CRISPR came from. It is called "Uncharacterized protein." It comes from
   a **metagenome** — DNA sequenced directly out of marine sediment, from an
   organism nobody has ever grown in a laboratory. There is no paper about it. It
   was a sequence in a database with a predicted shape attached.

5. Open the 3D viewer. By default the model is coloured by **pLDDT**, AlphaFold's
   per-residue confidence score:

   | pLDDT | Confidence | Typical colour |
   |---|---|---|
   | > 90 | Very high | Dark blue |
   | 70 – 90 | Confident | Light blue |
   | 50 – 70 | Low | Yellow |
   | < 50 | Very low — often disordered | Orange |

   This entry's mean pLDDT is about **94** — very high. The model thinks it knows
   what this protein looks like.

6. Find the **Predicted Aligned Error (PAE)** plot. It shows how confident the
   model is about the *relative position* of each pair of residues. Low error
   (dark) in a block means that whole region is reliably placed.

**Record:**
- Mean pLDDT for this model
- Are there any low-confidence (yellow/orange) regions? Where are they —
  internal, or at the termini?
- Does this predicted structure appear to have a protruding hairpin like the
  thumb you identified in Part 1?

> ### ⚠️ Model versions
>
> AFDB updates its models. The paper used **v4** (built 2022); the database now
> serves **v6**. You are looking at a slightly different model than the authors
> did. Expect your numbers in Part 3 to be close to theirs but not identical —
> and note that this is a normal, permanent feature of working with
> computationally generated databases.

**Questions:**

1. A pLDDT of 94 means the model is confident. Does confident mean **correct**?
   What is the difference?
2. This model is a **single chain** with no RNA, no other proteins, no ligands.
   What does AFDB structurally *not* tell you about this protein, no matter how
   high the confidence?

## Part 3 — Compare the two structures (20 min)

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

5. Rotate the superposition. Look at where the structures overlap and where they
   diverge.
6. **Bookmark or copy the results URL** — it is shareable, and you will hand it
   in.

### What the authors got

Table S1 of Yoon et al. 2026 reports this exact pair, aligned with a different
program (DALI):

| Metric | Published (DALI) |
|---|---|
| Z-score | 11.7 |
| RMSD | 3.8 Å |
| Aligned length | 157 residues |
| Target length | 178 residues |

**Questions:**

3. Your **RMSD** and **aligned residues** should be in the same neighborhood as
   the published values. Are they? They will not match exactly — TM-align and
   DALI use different algorithms, and you are using model v6 rather than v4.
4. You cannot reproduce the **Z-score** with this tool at all. Why not? (Hint: a
   Z-score is a statistic about one specific program's score distribution.) What
   does this tell you about quoting a single number from a paper as though it
   were a property of the proteins?

## Part 4 — Interpret (20 min)

### Reading a TM-score

TM-score is the headline number. Unlike RMSD, it does not get worse simply
because the proteins are different lengths, which is why it is the better
measure here.

| TM-score | Interpretation |
|---|---|
| < 0.17 | Indistinguishable from two random structures |
| 0.17 – 0.3 | Weak; not evidence on its own |
| 0.3 – 0.5 | Ambiguous zone — needs supporting evidence |
| **≥ 0.5** | **Same fold.** The threshold that matters |
| > 0.8 | Very close; usually the same family |

**Questions:**

5. Does your TM-score clear 0.5?
6. Your **% identity** is probably around 10%, maybe lower. At that identity,
   would a BLAST search have found this relationship? Why is structural
   comparison able to?
7. Compare **aligned residues** to the total length of each protein. Did the
   whole protein align, or just part of it? What might the unaligned portion be?
8. Your RMSD is likely in the 3–5 Å range. Two structures of the *same* protein
   typically align at under 1 Å. Does a 3–5 Å RMSD argue against a relationship?
   (Think about what RMSD measures when proteins are only distantly related — and
   why TM-score was designed to replace it.)
9. In the superposition, **which regions overlap best?** Do the thumb and G-loop
   land on top of each other? That specific overlap matters more for the
   evolutionary argument than the global numbers do — explain why.
10. *Optional:* re-run with **jFATCAT (rigid)** instead of TM-align. Same answer?
    What does it mean that two programs disagree slightly about the same pair?

### The harder question

11. You have now shown that a CRISPR protein and a Vipr protein share a fold. The
    paper claims something stronger: that **Vipr is ancestral to CRISPR
    effectors** — that CRISPR came from something VIPR-like, not the other way
    around.

    Your alignment alone cannot establish direction. **What additional evidence
    would you need?** List at least three things.

    <details>
    <summary markdown="span">Discuss after attempting</summary>

    What the authors actually did: built a phylogenetic tree of RAMPs and Vipr
    proteins rooted on an outgroup outside the family; showed VIPR systems are
    phage-encoded rather than host-encoded; showed VIPR loci lack CRISPR arrays
    and acquisition genes entirely; found VIPR systems across hundreds of
    distinct loci rather than in one lineage. A single pairwise alignment shows
    *relatedness*; direction requires a tree plus an outgroup.
    </details>

12. Everything you have done so far rests on a **prediction**. If the AlphaFold
    model were wrong in some important way, what would happen to the conclusion?
    Before you continue, write down what you think would settle the matter.

## Part 5 — Now look up the Vipr structure in the PDB (15 min)

After VIPR was discovered, the same group solved **21 cryo-EM structures** of
real VIPR complexes. That work was published as a companion paper. You can now
check the prediction against a measurement.

1. Go back to the **RCSB PDB** and search for **`35SF`**.
   *(This is VIPR<sub>single</sub>: a Vipr filament bound to its vrRNA, by
   cryo-EM at 2.9 Å.)*
2. Look at what the entry contains. You should find **several identical protein
   chains plus one or more RNA chains**.
3. Pick **one** Vipr protein chain and view it alone. (Make sure it is a protein
   chain, not an RNA chain.)
4. Optionally, run one more alignment: your `6IFN` Csm3 chain against this
   experimental Vipr chain, and compare the metrics to what you got in Part 3.

**Record:**
- How many Vipr protein chains are in the entry? Which chains are RNA?
- How does your single Vipr protomer compare, by eye, to the AlphaFold model
  from Part 2?

> ### ⚠️ Not the same protein
>
> `35SF` is the Vipr from **Escherichia phage SUSP1**. The AlphaFold model you
> used is `X1U2U4`, from a **marine sediment metagenome**. These are two
> different Vipr proteins from two very different sources.
>
> So a difference between them is **not** necessarily prediction error — it may
> simply be that they are different proteins. Keep that confound in mind when
> answering question 14.

**Questions:**

13. The AlphaFold model was a **single chain**. The experimental structure is a
    **filament of many chains wrapped around an RNA**. Which features of VIPR
    could only have been discovered experimentally? Go back to your answer to
    question 2 and see how well you predicted this.
14. Did the prediction capture the fold well enough that the discovery would have
    worked? Given the confound above, what comparison *would* cleanly separate
    "AlphaFold was wrong" from "these are different proteins"?
15. Return to your answer for question 12. Did the experimental structure settle
    what you said it would?

### How this hit was actually found

The authors ran the Part 3 comparison against **2.3 million predicted
structures**. `X1U2U4` came back ranked **115th** out of 322 hits for the Cas7
query, with a score *below the median* of that hit list. The top hit scored far
higher and was an ordinary, already-known CRISPR protein.

16. **So how was this one noticed at all?**

    <details>
    <summary markdown="span">Discuss after attempting</summary>

    Not by its score. Nearly every hit above it was a RAMP sitting next to a
    CRISPR array — i.e. an ordinary CRISPR protein. The authors inverted the
    usual filter: instead of keeping hits *with* a CRISPR array nearby, they
    looked at the ones **without** one. Five RAMP-fold proteins turned out to sit
    as lone genes or two-gene operons with no CRISPR repeats anywhere near them.
    That anomaly — not the alignment score — was the discovery.

    The lesson: a ranked list is a starting point, not an answer. The interesting
    thing was in the middle of the list, and it took a biological question to
    see it.
    </details>

17. *Optional, for discussion:* here are all five founding hits, with what AFDB
    knows about them.

    | Accession | Length | Mean pLDDT | Organism | Annotation |
    |---|---|---|---|---|
    | `A0A2D6XG06` | 234 | 80 | *Candidatus* Pacearchaeota archaeon | Type III-B CRISPR module RAMP |
    | `X1U2U4` | 178 | 94 | marine sediment metagenome | Uncharacterized protein |
    | `A0A1F4YLN4` | 229 | 74 | candidate division Zixibacteria bacterium | Uncharacterized protein |
    | `A0A661D0E2` | 198 | 96 | Gammaproteobacteria bacterium | Uncharacterized protein |
    | `A0A0F9A1L0` | 255 | 90 | marine sediment metagenome | Uncharacterized protein |

    Not one comes from a cultured organism — they are metagenomes, candidate
    divisions, and unnamed bacteria. Four of five are labelled "Uncharacterized."
    What does this say about where new biology is currently hiding, and about
    what made this kind of discovery possible only recently?

---

## What to hand in

1. Your completed metrics table from Part 3, plus the **shareable results URL**
2. A screenshot of the Part 3 superposition, with the thumb and G-loop labelled
   if you can identify them
3. Written answers to questions 1–16
4. Two or three sentences: **does the structural evidence convince you that VIPR
   and CRISPR are related? What would change your mind?**

