---
layout: lab
title: "Part 5: Now look up the VIPR structure in the PDB"
nav: lab
permalink: /lab/part-5/
---

After VIPR was discovered, the same group solved **21 cryo-EM structures** of
real VIPR complexes. That work was published as a companion paper. You can now
check the prediction against a measurement.

1. Go back to the **RCSB PDB** and search for **`35SF`**.
   *(This is VIPR<sub>single</sub>: a VIPR filament bound to its vrRNA, by
   cryo-EM at 2.9 Å.)*
2. Look at what the entry contains. You should find **several identical protein
   chains plus one or more RNA chains**.
3. Pick **one** VIPR protein chain and view it alone. (Make sure it is a protein
   chain, not an RNA chain.)
4. Optionally, run one more alignment: your `6IFN` Csm3 chain against this
   experimental VIPR chain, and compare the metrics to what you got in
   [Part 3]({{ '/lab/part-3/' | relative_url }}).

<div class="record" markdown="1">

**Record:**
- How many VIPR protein chains are in the entry? Which chains are RNA?
- How does your single VIPR protomer compare, by eye, to the AlphaFold model
  from Part 2?

</div>

> ### ⚠️ Not the same protein
>
> `35SF` is the VIPR protein from **Escherichia phage SUSP1**. The AlphaFold model you
> used is `X1U2U4`, from a **marine sediment metagenome**. These are two
> different VIPR proteins from two very different sources.
>
> So a difference between them is **not** necessarily prediction error — it may
> simply be that they are different proteins. Keep that confound in mind when
> answering question 14.

## Questions

{:start="13"}
13. The AlphaFold model was a **single chain**. The experimental structure is a
    **filament of many chains wrapped around an RNA**. Which features of VIPR
    could only have been discovered experimentally?
14. Did the prediction capture the fold well enough that the discovery would have
    worked? Given the confound above, what comparison *would* cleanly separate
    "AlphaFold was wrong" from "these are different proteins"?
15. Return to your answer for question 12. Did the experimental structure settle
    what you said it would?

## How this hit was actually found

The authors ran the Part 3 comparison against **2.3 million predicted
structures**. `X1U2U4` came back ranked **115th** out of 322 hits for the Cas7
query, with a score *below the median* of that hit list. The top hit scored far
higher and was an ordinary, already-known CRISPR protein.

{:start="16"}
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
