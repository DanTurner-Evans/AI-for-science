---
layout: lab
title: "Part 2: Look up the VIPR protein in AlphaFold"
nav: lab
permalink: /lab/part-2/
---

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

> ### ⚠️ Model versions
>
> AFDB updates its models. The paper used **v4** (built 2022); the database now
> serves **v6**. You are looking at a slightly different model than the authors
> did. Expect your numbers in Part 3 to be close to theirs but not identical —
> and note that this is a normal, permanent feature of working with
> computationally generated databases.
