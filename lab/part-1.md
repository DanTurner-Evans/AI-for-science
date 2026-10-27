---
layout: lab
title: "Part 1: Pull up the CRISPR protein in the PDB"
nav: lab
permalink: /lab/part-1/
---

1. Go to the **RCSB PDB**: <https://www.rcsb.org>
2. Search for **`6IFN`** and open the entry.
3. Read the title: *Crystal structure of Type III-A CRISPR Csm complex*. This is
   the Csm complex described in the
   [background]({{ '/lab/background/' | relative_url }}), from the bacterium
   *Streptococcus thermophilus*, solved by X-ray crystallography at 2.90 Å.
4. Find the **Macromolecules** section and list the chains. You should be able
   to pick out Csm1, Csm2, Csm3, Csm4, Csm5 and an RNA chain. Note that **Csm3
   appears several times** — those are the stacked backbone copies.
5. We want **one Csm3 chain**, because Csm3 is Cas7. The published search used
   **author chain E**. See the warning below before you select it.

> ### ⚠️ Two chain-numbering systems
>
> PDB entries can carry **two sets of chain IDs**, and `6IFN` is one where they
> disagree. RCSB shows them as `D [auth E]`: the first ID is the *label* ID,
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

## Look at one Csm3 chain in 3D

RCSB's 3D viewer is called **Mol\***. It runs in the browser; nothing to
install.

1. **Open the viewer.** On the `6IFN` entry page, find the line **Explore in
   3D** just below the structure image, and click **Structure**. (Or go
   straight to <https://www.rcsb.org/3d-view/6IFN>.) The whole Csm complex
   loads, with the guide RNA running through it.
2. **Get your bearings.** Drag to rotate, scroll to zoom, and right-drag to
   move the molecule. Hover over any part of the structure: the viewer names
   what is under your cursor, including the chain ID and protein name. Hover
   along the stacked backbone until you find a chain labelled Csm3.
3. **Switch on selection mode.** Click the **Selection Mode** icon (an arrow
   cursor) in the buttons at the top right of the viewer. A selection toolbar
   appears along the top of the 3D view.
4. **Select a whole chain.** In that toolbar, change the **Picking Level** from
   *Residue* to *Chain*. Now click on your Csm3 chain. The whole chain turns
   green. Wrong chain? Click on empty space to clear the selection and try
   again.
5. **Make it its own component.** In the selection toolbar, click **Create
   Component of Selection** (hover over the icons to see their names) and
   choose **Cartoon**. A new entry appears in the **Components** panel on the
   right.
6. **Hide everything else.** In the Components panel, click the **eye** icon
   next to each of the other components (such as *Polymer* and *Ligand*) to
   hide them. You should be left with a single protein chain.

> **The buttons look different?** Mol\* updates its interface from time to
> time. Hovering over any icon shows its name, and the
> [Mol\* viewer documentation](https://molstar.org/viewer-docs/) has pictures
> of each panel.
{: .tip}

> **Why one chain and not the whole complex?** The published search used a single
> Cas7/Csm3 protomer — `6ifnE` — as its query. The stacking is what builds the
> backbone, but one protomer carries the fold we are comparing.
{: .tip}

**This structure is a measurement.** Someone grew crystals, shot X-rays at them,
and solved the phases. Keep that in mind, because the next structure is not.
