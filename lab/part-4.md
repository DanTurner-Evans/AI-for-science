---
layout: lab
title: "Part 4: Interpret"
nav: lab
permalink: /lab/part-4/
---

Have your four numbers from [Part 3]({{ '/lab/part-3/' | relative_url }}) in
front of you.

## Reading a TM-score

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

## Questions

{:start="5"}
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

## The harder question

{:start="11"}
11. You have now shown that a CRISPR protein and a VIPR protein share a fold. The
    paper claims something stronger: that **VIPR is ancestral to CRISPR
    effectors** — that CRISPR came from something VIPR-like, not the other way
    around.

    Your alignment alone cannot establish direction. **What additional evidence
    would you need?** List at least three things.

    <details>
    <summary markdown="span">Discuss after attempting</summary>

    What the authors actually did: built a phylogenetic tree of RAMPs and VIPR
    proteins rooted on an outgroup outside the family; showed VIPR systems are
    phage-encoded rather than host-encoded; showed VIPR loci lack CRISPR arrays
    and acquisition genes entirely; found VIPR systems across hundreds of
    distinct loci rather than in one lineage. A single pairwise alignment shows
    *relatedness*; direction requires a tree plus an outgroup.
    </details>

12. Everything you have done so far rests on a **prediction**. If the AlphaFold
    model were wrong in some important way, what would happen to the conclusion?
    What evidence would settle the matter?
