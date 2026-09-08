---
layout: home
title: About
permalink: /
description: Chengle Fan is an undergraduate researcher at SUSTech working on topological photonics, synthetic gauge fields, and engineered wave transport.
announcements:
  enabled: true
  scrollable: false
  limit: 3
---
<section class="home-intro" aria-labelledby="intro-title">
  <div class="intro-copy">
    <p class="eyebrow">Metamaterials · Topological Photonics · Light-Matter Interaction</p>
    <h1 id="intro-title">Chengle Fan</h1>
    <p class="intro-role">Undergraduate researcher at <a href="https://sustech.edu.cn/en/">SUSTech</a></p>
    <p class="intro-lead">I study how engineered photonic structures control the propagation of light.</p>
    <p>My work connects topological band theory, full-wave simulation, and microwave experiments, with a focus on nonreciprocal transport and synthetic gauge fields.</p>
    <div class="action-links">
      <a class="button-primary" href="{{ '/projects/' | relative_url }}">Explore my research <span aria-hidden="true">↗</span></a>
    </div>
    <div class="intro-contact"><a class="intro-email" href="mailto:{{ site.data.socials.email }}">{{ site.data.socials.email }}</a></div>
  </div>
  <figure class="intro-portrait">
    <img src="{{ '/assets/img/prof_pic.jpg' | relative_url }}" alt="Portrait of Chengle Fan" width="480" height="600" fetchpriority="high">
    <figcaption>Southern University of Science and Technology<br>Shenzhen, China</figcaption>
  </figure>
</section>

<section class="home-section" aria-labelledby="about-heading">
  <div class="section-heading"><h2 id="about-heading">About me</h2><span class="section-kicker">Background & interests</span></div>
  <div class="about-columns">
    <div>
      <p>I am pursuing a B.Eng. in Optoelectronic Information Science and Engineering at SUSTech, with graduation expected in June 2027. Since February 2025, I have worked in Prof. Zhen Gao’s Topological Physics Research Group in the Department of Electronic and Electrical Engineering.</p>
      <p>From January to April 2026, I was a visiting research student with <a href="https://personal.ntu.edu.sg/blzhang/">Prof. Baile Zhang</a> at Nanyang Technological University, developing fabrication-compatible terahertz photonic structures.</p>
    </div>
    <div class="research-interests">
      <h3>Research interests</h3>
      <ul>
        <li>Topological photonics & nonreciprocity</li>
        <li>Photonic crystals & metamaterials</li>
        <li>Synthetic gauge fields & duality</li>
        <li>Time-varying & spatiotemporal photonics</li>
      </ul>
      <p>I hope to extend this work toward integrated photonic platforms for reconfigurable control of light.</p>
    </div>
  </div>
</section>

<section class="home-section" aria-labelledby="research-heading">
  <div class="section-heading"><h2 id="research-heading">Selected research</h2><a href="{{ '/projects/' | relative_url }}">All projects <span aria-hidden="true">↗</span></a></div>
  <div class="featured-research">
    {% assign featured = site.projects | sort: 'importance' %}
    {% for project in featured limit: 3 %}
    <article class="research-preview">
      <a class="research-image" href="{{ project.url | relative_url }}" tabindex="-1" aria-hidden="true">
        {% assign image_stem = project.img | split: '.' | pop | join: '.' %}
        <picture>
          {% if site.imagemagick.enabled %}<source type="image/webp" srcset="{{ image_stem | relative_url }}-480.webp 480w, {{ image_stem | relative_url }}-800.webp 800w" sizes="(max-width: 680px) 90vw, 340px">{% endif %}
          <img src="{{ project.img | relative_url }}" alt="" width="640" height="400" loading="lazy">
        </picture>
      </a>
      <p class="eyebrow">{{ project.platform }}</p>
      <h3><a href="{{ project.url | relative_url }}">{{ project.short_title }}</a></h3>
      <p>{{ project.summary }}</p>
      <p class="research-status">{{ project.status }}</p>
    </article>
    {% endfor %}
  </div>
</section>

<section class="home-section" aria-labelledby="news-heading">
  <div class="section-heading"><h2 id="news-heading">Recent updates</h2><a href="{{ '/news/' | relative_url }}">All updates <span aria-hidden="true">↗</span></a></div>
  {% include news.liquid limit=true %}
</section>

<section class="home-section" aria-labelledby="manuscript-heading">
  <div class="section-heading"><h2 id="manuscript-heading">Manuscript in preparation</h2><a href="{{ '/publications/' | relative_url }}">Manuscript details <span aria-hidden="true">↗</span></a></div>
  <div class="publications">{% bibliography --query @*[selected=true] %}</div>
</section>

<div class="contact-strip">
  <div><h2>Get in touch</h2><p>I am interested in graduate research opportunities in photonics and related areas.</p></div>
  <a href="mailto:{{ site.data.socials.email }}">Email me <span aria-hidden="true">↗</span></a>
</div>
