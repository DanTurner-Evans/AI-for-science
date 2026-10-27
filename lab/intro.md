---
layout: lab
title: "Introduction: what CRISPR is and how it works"
nav: lab
permalink: /lab/intro/
---

## An immune system in bacteria

Bacteria and archaea are under constant attack from viruses called
**bacteriophages** (phages). Many defend themselves with **CRISPR-Cas**, an
*adaptive* immune system: it remembers viruses it has seen before and destroys
them faster the next time. Roughly 40% of sequenced bacteria and most archaea
carry at least one CRISPR system.

The name describes the memory bank. **CRISPR** stands for *Clustered Regularly
Interspaced Short Palindromic Repeats*: a stretch of the genome where a short
**repeat** sequence alternates with unique **spacers**. Each spacer is a
snippet of DNA taken from a past invader. Next to this array sit the **cas
genes** (CRISPR-associated), which encode the proteins that do the work.

## How it works, in three stages

1. **Adaptation.** When a new phage infects the cell, the proteins **Cas1** and
   **Cas2** cut out a short piece of its DNA and insert it into the CRISPR array
   as a new spacer. The cell now has a record of the infection, and passes it on
   when it divides.
2. **Making guides.** The array is transcribed into one long RNA, which is cut
   into short **CRISPR RNAs (crRNAs)**. Each crRNA carries one spacer: it is a
   guide that matches one invader.
3. **Interference.** Cas proteins load a crRNA and patrol the cell. When the
   guide base-pairs with a matching sequence in an invading genome, the Cas
   machinery cuts it. Many systems also require a short **PAM** (protospacer
   adjacent motif) next to the target before they cut. The CRISPR array itself
   lacks the PAM, which stops the cell attacking its own memory.

The key idea for everything that follows: **the protein does the cutting, the
RNA decides where.** Change the guide, and you change the target.

## The Cas proteins

CRISPR systems fall into two classes, depending on how the interference step is
organized:

- **Class 1** systems use a **multi-protein complex**: several different Cas
  proteins assemble around the guide RNA. These are the most common in nature.
  This lab's CRISPR protein, **Cas7**, is the repeating backbone of these
  complexes.
- **Class 2** systems use a **single large protein** that holds the guide and
  cuts the target. Cas9 is the famous example. These are rarer in nature but
  much easier to use as tools, because there is only one protein to deliver.

| Protein | Class | What it does |
|---|---|---|
| **Cas1, Cas2** | Both | Capture new spacers from invaders (adaptation) |
| **Cas7** | 1 | Forms the backbone of multi-protein complexes, gripping the guide RNA |
| **Cas3** | 1 (type I) | Shreds target DNA once the complex has found it |
| **Cas10** | 1 (type III) | Large subunit of type III complexes; cuts DNA and sounds the alarm |
| **Cas9** | 2 (type II) | Single protein that cuts both strands of target DNA |
| **Cas12** | 2 (type V) | Single protein that cuts DNA; often smaller than Cas9 |
| **Cas13** | 2 (type VI) | Single protein that targets **RNA** rather than DNA |

The [background page]({{ '/lab/background/' | relative_url }}) introduces the
specific class 1 complex you will look at, and a naming quirk that comes with
it.

## From bacterial immunity to gene editing

In 2012, Jennifer Doudna, Emmanuelle Charpentier and colleagues showed that
Cas9 could be given an engineered guide RNA and would then cut **any** DNA
sequence that matched it. Within months other labs, including Feng Zhang's and
George Church's, had it working in human cells. Doudna and Charpentier shared
the 2020 Nobel Prize in Chemistry.

Cutting is only the first step. The cell repairs the break, and the repair is
what makes the edit: often it is imperfect and switches a gene off; with a
supplied template, it can write in a new sequence. Newer tools, **base
editors** and **prime editors**, fuse a modified Cas9 to other enzymes so they
can change DNA letters without cutting both strands at all.

In late 2023, regulators in the UK and then the US approved **Casgevy**, the
first CRISPR-based therapy, for sickle cell disease and β-thalassemia.

## Why look for new CRISPR-like systems?

Cas9 transformed biology, but it was never designed to be a medicine. It is a
bacterial immune protein, and several of its properties get in the way:

- **Size.** The workhorse Cas9, from *Streptococcus pyogenes*, is about 1,370
  amino acids long. The viral vectors most often used to deliver genes into
  the body (AAV) can carry only about 4.7 kb of DNA, which leaves little room
  for anything else, and base and prime editors are bigger still. Much smaller
  effectors, such as Cas12f and the IscB and TnpB proteins that Cas9 and Cas12
  evolved from, fit far more easily.
- **The immune system.** The most widely used Cas9s come from bacteria that
  commonly live on or infect people, and many adults already carry antibodies
  and T cells that recognize them. Proteins from microbes humans rarely meet
  may avoid that response.
- **Where it can go.** Every system has its own PAM requirement, which limits
  the sites in the genome it can reach. A larger toolkit of systems means more
  of the genome is in reach.
- **What it can do.** Different systems do different jobs: Cas13 edits RNA,
  which is temporary rather than permanent; CRISPR-associated transposases
  insert whole genes without a double-strand break; class 1 systems can delete
  long stretches of DNA.
- **Who owns it.** The core Cas9 patents have been fought over for years.
  Newly discovered systems open routes to therapies outside that dispute.

So researchers now search for new systems deliberately, by mining metagenomes
(DNA sequenced directly from the environment) and, increasingly, predicted
protein structures. That is the search you will retrace in this lab. The VIPR
paper's authors suggest engineered VIPR proteins could be adapted for genome
editing, imaging DNA in cells, or switching genes on and off. Those uses are
proposals, so far tested only in the lab.

**As you work through the lab, keep a policy question in mind:** AI tools like
AlphaFold make this kind of search faster and cheaper. Who benefits when
anyone can mine a database for the next gene-editing tool, and what new risks
come with that?