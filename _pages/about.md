---
layout: home
title: About
permalink: /
description: Chengle Fan is an undergraduate researcher at SUSTech combining electromagnetic modeling, photonic design, and microwave experiments, with interests in nanophotonics and integrated photonic devices.
featured_projects:
  - /projects/1_pseudospin_locked_chiral_edge/
  - /projects/4_mdec/
  - /projects/0_photonic_time_crystals/
announcements:
  enabled: true
  scrollable: false
  limit: 3
---
<section class="home-intro" aria-labelledby="intro-title">
  <div class="intro-copy">
    <p class="eyebrow">Photonic Structures · Wave Control · Device Design</p>
    <h1 id="intro-title">Chengle Fan</h1>
    <p class="intro-role">Undergraduate researcher at <a href="https://sustech.edu.cn/en/">SUSTech</a></p>
    <p class="intro-lead">I explore how structure shapes light, turning physical insight into photonic design.</p>
    <p>My work connects electromagnetic modeling, photonic design, and microwave experiments. I am interested in extending this approach to reconfigurable nanophotonic and integrated devices for optical information processing and sensing.</p>
    <div class="action-links">
      <a class="button-primary" href="{{ '/projects/' | relative_url }}">Explore my research <span aria-hidden="true">↗</span></a>
      <a class="button-secondary" href="{{ '/cv/' | relative_url }}">View my CV</a>
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
      <p>I am pursuing a B.Eng. in Optoelectronic Information Science and Engineering at SUSTech, with graduation expected in June 2027. Since February 2025, I have worked in Prof. Zhen Gao’s Artificial Microstructure Physics Research Group.</p>
      <p>My main research project brings together full-wave modeling, sample design, experimental characterization, and manuscript preparation for pseudospin-locked chiral edge states. I also contribute to experiments on cavity-controlled photonic systems and am exploring cavity-controlled refraction.</p>
      <p>From January 12 to April 27, 2026, I was enrolled as a Visiting Research Student (Non-Graduating) at Nanyang Technological University, working with Prof. Baile Zhang on numerical modeling and optimization of terahertz photonic structures.</p>
    </div>
    <div class="research-interests">
      <h3>Research interests</h3>
      <ul>
        <li>Nanophotonics & integrated photonic devices</li>
        <li>Optical modes & light–matter interactions</li>
        <li>Reconfigurable photonic structures</li>
        <li>Topological & time-varying wave systems</li>
      </ul>
    </div>
  </div>
</section>

<section class="home-section" aria-labelledby="research-heading">
  <div class="section-heading"><h2 id="research-heading">Selected research</h2><a href="{{ '/projects/' | relative_url }}">All projects <span aria-hidden="true">↗</span></a></div>
  <div class="featured-research">
    {% for project_url in page.featured_projects %}
    {% assign project = site.projects | where: "url", project_url | first %}
    <article class="research-preview{% unless project.img %} research-preview-text{% endunless %}">
      {% if project.img %}
      <a class="research-image" href="{{ project.url | relative_url }}" tabindex="-1" aria-hidden="true">
        {% assign image_stem = project.img | split: '.' | pop | join: '.' %}
        <picture>
          {% if site.imagemagick.enabled %}<source type="image/webp" srcset="{{ image_stem | relative_url }}-480.webp 480w, {{ image_stem | relative_url }}-800.webp 800w" sizes="(max-width: 680px) 90vw, 340px">{% endif %}
          <img src="{{ project.img | relative_url }}" alt="" width="640" height="400" loading="lazy">
        </picture>
      </a>
      {% endif %}
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
  <div class="section-heading"><h2 id="manuscript-heading">Manuscripts</h2><a href="{{ '/publications/' | relative_url }}">Manuscript details <span aria-hidden="true">↗</span></a></div>
  <div class="publications">{% bibliography --query @*[selected=true] %}</div>
</section>

<div class="contact-strip">
  <div><h2>Get in touch</h2><p>I am seeking PhD opportunities starting in Fall 2027 in photonics and related areas.</p></div>
  <a href="mailto:{{ site.data.socials.email }}">Email me <span aria-hidden="true">↗</span></a>
</div>
