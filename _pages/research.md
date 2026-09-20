---
layout: page
title: research
permalink: /research/
description: Data-driven, learning-based, and generative safety verification for safe and reliable autonomous systems.
nav: true
nav_order: 3
---

I study safe and reliable autonomous systems at the intersection of control theory, robotics, and machine learning. My research develops data-driven, learning-based, and generative methods for safety verification, particularly for complex systems where exact computation is intractable and guarantees must be obtained from limited data drawn from complex distributions.

Using system symmetries, structural inductive biases, and compact latent representations, I aim to enable real-time, data-efficient safety verification that can be deployed in real-world robotic systems.

## Research Overview

<figure>
  <img
    src="{{ '/assets/img/research/reasearch_summary_1.png' | relative_url | bust_file_cache }}"
    alt="Research challenges in robot learning: safety with limited data and task-dependent safety beyond collision avoidance."
    width="1121"
    height="629"
    loading="lazy"
    decoding="async"
    style="display: block; width: 80%; height: auto; border-radius: 0.5rem;"
  >
  <figcaption>Safety challenges in robot learning: limited data and compute, and safety requirements that vary across tasks.</figcaption>
</figure>

<figure>
  <img
    src="{{ '/assets/img/research/research_summary_2.gif' | relative_url | bust_file_cache }}"
    alt="Animated research framework connecting labeled robot trajectories, diffusion models, latent-space safety verification, and physics-informed inductive biases."
    width="1600"
    height="900"
    loading="lazy"
    decoding="async"
    style="display: block; width: 80%; height: auto; border-radius: 0.5rem;"
  >
  <figcaption>Data-efficient, task-aware safety verification in latent space, guided by physical structure and prior knowledge.</figcaption>
</figure>

My research asks how robots can obtain meaningful safety guarantees with limited data and computation, across tasks where safety extends beyond collision avoidance to preventing object damage, spills, and hazardous interactions. I investigate diffusion models that learn compact latent dynamics and unsafe regions from labeled robot trajectories, together with safety certificates and filters for efficient verification in these learned spaces. A central goal is to understand the fundamental data requirements for safety and how physical priors, such as energy conservation, symmetry, and equivariance, can reduce them. By combining these inductive biases with task-dependent safety specifications, I aim to develop robot learning and control methods that are both data-efficient and verifiably safe.

## Funding Projects

<div class="funding-projects">
  {% for funding in site.data.funding %}
    <article class="funding-card" aria-labelledby="funding-{{ funding.id }}">
      <div class="funding-card-media funding-card-media--{{ funding.id }}">
        <img
          src="{{ funding.image | relative_url | bust_file_cache }}"
          alt="{{ funding.image_alt | escape }}"
          width="{{ funding.image_width }}"
          height="{{ funding.image_height }}"
          loading="lazy"
          decoding="async"
        >
      </div>
      <div class="funding-card-body">
        <h3 id="funding-{{ funding.id }}">{{ funding.title | escape }}</h3>
        <p>{{ funding.description | escape }}</p>
      </div>
    </article>
  {% endfor %}
</div>

## Selected related work

### Reachability and sample complexity

I study sampling-based reachability, including the roles of geometry, dynamics, and sample complexity. I also work on data-driven target reachability in Hamiltonian systems using symplectic inductive bias.

- **[On the Limits of Sampling-Based Reachability: Geometry, Dynamics, and Sample Complexity]({{ '/publications/' | relative_url }}#liu2026limits)** — Conference on Robot Learning, 2026.
- **[Symplectic Inductive Bias for Data-Driven Target Reachability in Hamiltonian Systems]({{ '/publications/' | relative_url }}#ouyang2026symplectic)** — IEEE Conference on Decision and Control, 2026.

### Recurrent methods for safety-critical control

My work on recurrent tracking functions and recurrent control barrier functions explores safety-critical control and nonparametric safety verification.

- **[Safety-Critical Control via Recurrent Tracking Functions]({{ '/publications/' | relative_url }}#liu2026tracking)** — American Control Conference, 2026.
- **[Recurrent Control Barrier Functions: A Path Towards Nonparametric Safety Verification]({{ '/publications/' | relative_url }}#liu2025recurrent)** — IEEE Conference on Decision and Control, 2025.

### Learning, optimization, and energy systems

My earlier research includes predict-then-optimize methods with dependent data and shared storage for net zero energy buildings.

- **[Smart Predict-then-Optimize Method with Dependent Data: Risk Bounds and Calibration of Autoregression]({{ '/publications/' | relative_url }}#liu2024predict)** — arXiv preprint, 2024.
- **[Enabling Net Zero Energy Buildings With Shared Storage: A Cyber-Physical Perspective]({{ '/publications/' | relative_url }}#cui2023netzero)** — IEEE Internet of Things Journal, 2023.

Full citations are available on the [publications page]({{ '/publications/' | relative_url }}).
