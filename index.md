---
layout: default
nav: home
---

<section class="hero">
<h1>AI for Science</h1>
<p class="lede">How AI is accelerating discovery, where it can cause harm, and what policymakers can do about it.</p>
<p class="byline">A Tech Labs 2026 session with Dan Turner-Evans, PhD</p>
<p class="actions"><a class="button" href="#slides">View the slides</a><a class="button secondary" href="{{ '/lab/' | relative_url }}">Start the lab</a></p>

</section>

<section class="home-section about" id="about" markdown="1">

## About the session

AI is accelerating scientific workflows and driving discovery. Scientists use large language models for hypothesis generation and data analysis. New AI models capture previously unknown natural laws. Autonomous labs test hypotheses and optimize experimental protocols. The federal government has taken note and acted accordingly, launching programs like the Genesis Mission, coordinated by the Department of Energy, to double U.S. research productivity by applying AI to the federal research enterprise.

AI in science can also cause harm. AI models can commit scientific misconduct, like fabricating data or manipulating statistics, or hallucinate results. AI also lowers the barrier for bad actors to develop new bioweapons, among other national security concerns. Further, as in other fields, AI will likely disrupt the training pipeline as principal investigators increasingly turn to AI agents, instead of graduate students or postdocs, to perform research tasks. Finally, some research areas risk being left behind as scientists focus on the fields where AI is most readily applied.

In this course, we will cover each of these aspects of AI-for-science, walk through a hands-on demonstration, and discuss open policy opportunities.

</section>

<section class="home-section" id="slides">
<h2>Slides</h2>
<div class="embed">
<iframe src="{{ site.slides_embed }}" title="AI for Science slides" allowfullscreen loading="lazy"></iframe>
</div>
<p><a href="{{ site.slides_url }}">Open the slides in Figma</a></p>
</section>

<section class="home-section" id="readings">
<h2>Readings</h2>
{% assign required = site.data.readings | where_exp: "r", "r.optional != true" %}
{% assign optional = site.data.readings | where_exp: "r", "r.optional == true" %}
<div class="readings-group">
<h3>Before the session</h3>
<ul class="readings">
{% for r in required %}
<li><a class="title" href="{{ r.url }}">{{ r.title }}</a><span class="topic">{{ r.topic }}</span><span class="by">{{ r.authors }}, <em>{{ r.source }}</em></span></li>
{% endfor %}
</ul>
</div>
<div class="readings-group">
<h3>If you want to go further</h3>
<ul class="readings">
{% for r in optional %}
<li><a class="title" href="{{ r.url }}">{{ r.title }}</a><span class="topic">{{ r.topic }}</span><span class="by">{{ r.authors }}, <em>{{ r.source }}</em></span></li>
{% endfor %}
</ul>
</div>
</section>

<section class="lab-panel" id="lab">
<h2>Lab: Finding next gen CRISPR-like complexes</h2>
<p>Using AlphaFold to find alternative CRISPR candidates. Retrace a 2026 discovery: compare an experimental CRISPR protein to an AlphaFold prediction of an uncharacterized protein, then find out whether the prediction held up.</p>
<p class="facts">90 minutes in your browser. Nothing to install, no account needed.</p>
<a class="button" href="{{ '/lab/' | relative_url }}">Start the lab</a>
</section>
