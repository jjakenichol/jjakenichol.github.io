---
layout: page
permalink: /software/
title: Software
description: Research software I develop and maintain.
nav: true
nav_order: 3
---

## Published packages

**[CaStLe](https://github.com/jjakenichol/CaStLe)**: Causal Space-Time Stencil Learning. Recovers local causal space-time structures from observational data on gridded domains. Companion code for the [JGR: Machine Learning and Computation paper](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2024JH000546).

**[clif](https://github.com/sandialabs/clif)**: CLImate Fingerprinting. A Python library that computes empirical orthogonal functions, primarily for climate data. Developed with Kenny Chowdhary.

---

## Repositories

{% if site.data.repositories.github_repos %}

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.liquid repository=repo %}
  {% endfor %}
</div>
{% endif %}

{% if site.data.repositories.github_users %}

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for user in site.data.repositories.github_users %}
    {% include repository/repo_user.liquid username=user %}
  {% endfor %}
</div>
{% endif %}
