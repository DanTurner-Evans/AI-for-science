---
layout: lab
title: "Background: the two proteins"
nav: lab
permalink: /lab/background/
---

## Cas7 and Vipr

**Cas7** is a component of class 1 CRISPR-Cas systems — the most common CRISPR
systems in nature. Cas7 proteins stack into a backbone that cradles the guide
RNA. They belong to a family called **RAMPs** (repeat-associated mysterious
proteins), defined by two features:

- a **thumb** domain — a protruding β-hairpin that reaches over the bound RNA
- a **glycine-rich loop (G-loop)** — a flexible loop contacting the RNA backbone

**Vipr** is the protein component of VIPR systems. Multiple copies oligomerize
along a VIPR RNA (**vrRNA**) to form a helical filament that recognizes DNA.

## What is a Csm complex?

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

## A naming trap: Csm3 *is* Cas7

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
