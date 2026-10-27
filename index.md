---
layout: default
nav: home
---

<section class="hero" id="about">
<p class="eyebrow">Tech Labs 2026</p>
<h1>AI for Science</h1>
<p class="lede">How AI is accelerating discovery, where it can cause harm, and what policymakers can do about it.</p>
</section>

<section class="prose" markdown="1">

## About the session

AI is accelerating scientific workflows and driving discovery. Scientists use large language models for hypothesis generation and data analysis. New AI models capture previously unknown natural laws. Autonomous labs test hypotheses and optimize experimental protocols. The federal government has taken note and acted accordingly, launching programs like the Genesis Mission, coordinated by the Department of Energy, to double U.S. research productivity by applying AI to the federal research enterprise.

AI in science can also cause harm. AI models can commit scientific misconduct, like fabricating data or manipulating statistics, or hallucinate results. AI also lowers the barrier for bad actors to develop new bioweapons, among other national security concerns. Further, as in other fields, AI will likely disrupt the training pipeline as principal investigators increasingly turn to AI agents, instead of graduate students or postdocs, to perform research tasks. Finally, some research areas risk being left behind as scientists focus on the fields where AI is most readily applied.

In this course, we will cover each of these aspects of AI-for-science, walk through a hands-on demonstration, and discuss open policy opportunities.

</section>

<section id="slides">
<h2>Slides</h2>
<div class="embed">
<iframe src="{{ site.slides_embed }}" title="AI for Science slides" allowfullscreen loading="lazy"></iframe>
</div>
<p class="muted"><a href="{{ site.slides_url }}">Open the slides in Figma ↗</a></p>
</section>

<section id="readings">
<h2>Suggested readings</h2>
<ul class="readings">
{% for r in site.data.readings %}
<li class="reading">
<p class="tag">{{ r.topic }}{% if r.optional %} <span class="badge">Optional</span>{% endif %}</p>
<a class="title" href="{{ r.url }}">{{ r.title }}</a>
<p class="meta">{{ r.authors }} · {{ r.source }}</p>
</li>
{% endfor %}
</ul>
</section>

<section id="lab" class="lab-cta">
<div>
<p class="eyebrow">Hands-on lab · 90 min · browser only</p>
<h2>Is VIPR related to CRISPR?</h2>
<p>Retrace a 2026 discovery: compare an experimental CRISPR protein structure to an AlphaFold prediction of an uncharacterized protein, then find out whether the prediction held up.</p>
</div>
<a class="button" href="{{ '/lab/' | relative_url }}">Start the lab →</a>
</section>
