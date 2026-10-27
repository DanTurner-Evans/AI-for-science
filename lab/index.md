---
layout: lab
title: "Finding next gen CRISPR-like complexes"
nav: lab
---

<p class="paper">Based on <a href="https://doi.org/10.1126/science.aei0498">Yoon et al., "A noncontiguous code for RNA-guided DNA recognition at the origin of CRISPR-Cas," <em>Science</em> 393, 1230–1235 (2026)</a></p>

**Using AlphaFold to find alternative CRISPR candidates**

{% assign conf = site.data.x1u2u4_plddt %}
{% if conf %}VIPR
<figure class="plddt">
<div class="plddt-strip" markdown="0" role="img" aria-label="AlphaFold confidence for each of the {{ conf.residues.size }} residues of protein X1U2U4. Mean pLDDT {{ conf.mean }}; most residues are very high confidence.">{% for r in conf.residues %}<span class="r {{ r[2] }}" style="--i:{{ forloop.index0 }}" title="Residue {{ r[0] }}: pLDDT {{ r[1] }}"></span>{% endfor %}
</div>
<figcaption>
<p>AlphaFold's confidence in each of the {{ conf.residues.size }} residues of X1U2U4, an uncharacterized protein from marine sediment that reopened the question of where CRISPR came from. You'll look it up in <a href="{{ '/lab/part-2/' | relative_url }}">Part 2</a>.</p>
<ul class="legend">
<li style="--c: var(--vhigh)">Very high</li>
<li style="--c: var(--high)">Confident</li>
<li style="--c: var(--low)">Low</li>
<li style="--c: var(--vlow)">Very low</li>
</ul>
</figcaption>
</figure>
{% endif %}

## The question

CRISPR gene editing has already reached patients: in 2023, Casgevy became the
first approved CRISPR therapy, for sickle cell disease and β-thalassemia. But
the Cas9 protein behind it is a bacterial immune protein, not a medicine. It is
large and hard to package into the viruses used to deliver genes, many people
already have immune responses to it, and it can only reach some parts of the
genome. So researchers are hunting for **new CRISPR-like systems** that are
smaller, less familiar to our immune systems, or able to do different jobs.
(The [introduction]({{ '/lab/intro/' | relative_url }}) explains these limits
in more detail.)

Where do you look? Increasingly, in the millions of protein sequences pulled
out of environmental DNA, most of which nobody has ever studied. The problem is
recognizing a relative of CRISPR when you find one.

In 2026, a group at Berkeley reported exactly that kind of find: a new
RNA-guided system called **VIPR** (Viral Interference Programmable Repeat),
encoded by bacteriophages. They argued it is **ancestral to CRISPR-Cas**, so
that the machinery bacteria use for adaptive immunity may have originated in
warfare between viruses. They also suggest it could be engineered into new
genome-editing tools.

How do you make a claim like that? The VIPR protein and CRISPR proteins share
almost no recognizable sequence similarity. Standard tools for finding related
proteins (BLAST, HMM searches) compare sequences, and they fail here.

But **protein structure is conserved long after sequence has diverged.** Two
proteins can descend from a common ancestor, retain the same fold, and share
barely 10% of their amino acids. If you only look at sequence, you see nothing.
If you look at shape, you see the relationship.

When the authors made this discovery, **nobody had ever determined the**
**structure of a VIPR protein.**  So they used an **AlphaFold prediction** 
instead, and the entire claim rested on an AI prediction about a protein's
shape.

In this lab you will retrace that exact reasoning:

1. Pull up a real, experimentally determined CRISPR protein structure
2. Look up the predicted structure of a VIPR protein in AlphaFold
3. Compare them — **this is the comparison that made the discovery**
4. Interpret what that comparison can and cannot tell you

## The lab, step by step

Work through the pages in order. If CRISPR is new to you, start with the
introduction. Don't skip the background page: it explains a naming trap that
will otherwise trip you up in Part 1.

<ol class="protocol" markdown="0">
{% for step in site.data.lab %}
  <li><a href="{{ step.url | relative_url }}"><span class="label">{{ step.label }}</span><span class="title">{{ step.title }}</span><span class="summary">{{ step.summary }}</span></a></li>
{% endfor %}
</ol>

## What you'll use

All free, all in the browser, no account needed:

| Resource | Used in | What it is |
|---|---|---|
| [RCSB Protein Data Bank](https://www.rcsb.org) | Parts 1, 3 | Archive of experimentally determined structures, with the Mol\* 3D viewer |
| [AlphaFold Protein Structure Database](https://alphafold.ebi.ac.uk) | Part 2 | Pre-computed AlphaFold predictions for over 200 million proteins |
| [RCSB Pairwise Structure Alignment](https://www.rcsb.org/alignment) | Parts 3, 4 | Aligns two structures and reports TM-score, RMSD and more |


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

- Yoon et al., ["A noncontiguous code for RNA-guided DNA recognition at the
  origin of CRISPR-Cas,"](https://doi.org/10.1126/science.aei0498) *Science*
  **393**, 1230–1235 (2026) — the discovery
- Guo et al., "Structure Studies of the CRISPR-Csm Complex Reveal Mechanism of
  Co-transcriptional Interference," *Cell* **176** (2019) — `6IFN`
- Varadi et al., "AlphaFold Protein Structure Database," *Nucleic Acids Res.*
  **50**, D439–D444 (2022)
- Bittrich et al., "RCSB Protein Data Bank: exploring protein 3D similarities via
  comprehensive structural alignments," *Bioinformatics* **40**, btae370 (2024)
- Zhang & Skolnick, "TM-align," *Nucleic Acids Res.* **33**, 2302–2309 (2005)
