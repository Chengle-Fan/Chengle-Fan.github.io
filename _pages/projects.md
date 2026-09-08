---
layout: page
title: Research
permalink: /projects/
description: Topological photonics and engineered wave transport, from theoretical models to experimental characterization.
nav: true
nav_order: 2
---

<div class="research-index">
{% assign sorted_projects = site.projects | sort: 'importance' %}
{% for project in sorted_projects %}
<article class="research-row{% unless project.img %} research-row-text{% endunless %}">
  {% if project.img %}
  <a class="research-image" href="{{ project.url | relative_url }}" tabindex="-1" aria-hidden="true">{% assign image_stem = project.img | split: '.' | pop | join: '.' %}
        <picture>
          {% if site.imagemagick.enabled %}<source type="image/webp" srcset="{{ image_stem | relative_url }}-480.webp 480w, {{ image_stem | relative_url }}-800.webp 800w" sizes="(max-width: 680px) 90vw, 340px">{% endif %}
          <img src="{{ project.img | relative_url }}" alt="" width="640" height="400" loading="lazy">
        </picture></a>
  {% endif %}
  <div class="research-row-copy">
    <p class="eyebrow">{{ project.platform }}</p>
    <h2><a href="{{ project.url | relative_url }}">{{ project.short_title }}</a></h2>
    <p>{{ project.summary }}</p>
    <p class="project-role">{{ project.role }}</p>
    <div class="research-row-footer"><span class="research-status">{{ project.status }}</span><a href="{{ project.url | relative_url }}" aria-label="Read about {{ project.short_title }}">Read project <span aria-hidden="true">↗</span></a></div>
  </div>
</article>
{% endfor %}
</div>
