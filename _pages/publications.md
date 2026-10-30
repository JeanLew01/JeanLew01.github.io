---
layout: page
permalink: /publications/
title: publications
description: Research in control, reachability, learning, and cyber-physical systems.
nav: true
nav_order: 2
---

{% include bib_search.liquid %}

<div class="publications">

<h2>Conferences &amp; Workshops</h2>

{% bibliography --query @inproceedings %}

<h2>Preprints</h2>

{% bibliography --query @misc[keywords=preprint] %}

<h2>Journals</h2>

{% bibliography --query @article %}

<h2>Datasets &amp; Benchmarks</h2>

{% bibliography --query @misc[keywords=benchmark] %}

</div>
