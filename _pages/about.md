---
permalink: /
title: ""
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

<h2 id="about">About</h2>

Hihi, I am Ruining Yang (pronounce: ray-ning-young), a second year PhD in
Computer Engineering at Northeastern University. I am fortunate to be
advised by Prof. [Lili Su](https://lilisu3.sites.northeastern.edu/).
Previously, I received my MS in Computer Science from Northeastern
University, and BA in Communication from University of Colorado Denver.

My research focuses on scalable and trustworthy foundation-model-based
autonomous driving systems, with an emphasis on robust decision-making in
complex real-world scenarios. Currently, I am investigating
Vision-Language-Action (VLA) models and data-efficient learning strategies
for autonomous driving.

<h2 id="research-interests" class="no-underline">Research Interests</h2>

<div class="interest-tags">
  <span>Autonomous Driving</span>
  <span>Vision-Language-Action Models</span>
  <span>Data Efficiency</span>
</div>

<h2 id="publications" class="pub-heading">📝 Selected Publications
  <span class="pub-heading-meta">
    | <a href="{{ site.author.googlescholar }}">See All Publications &gt;</a>
    | *: Equal Contributions
  </span>
</h2>

{% assign sorted_pubs = site.publications | sort: 'sort_order' %}
{% for post in sorted_pubs %}
<div class="paper-box">
  <div class="paper-box-image">
    <img src="{{ '/images/' | append: post.teaser | default: '/images/paper-placeholder.svg' }}" alt="paper teaser">
  </div>
  <div class="paper-box-text">
    <p class="paper-title">{{ post.title }}</p>
    <p class="paper-authors">{{ post.citation }}</p>
    {% if post.description %}
    <p class="paper-desc">{{ post.description }}</p>
    {% endif %}
    <p class="paper-links">
      {% if post.paperurl and post.paperurl != '' %}
        <a class="pub-venue" href="{{ post.paperurl }}" target="_blank" rel="noopener noreferrer">{{ post.venue }}</a>
      {% else %}
        <span class="pub-venue">{{ post.venue }}</span>
      {% endif %}
      {% if post.paperurl and post.paperurl != '' %}
        &nbsp;|&nbsp;<a class="pub-text-link" href="{{ post.paperurl }}" target="_blank" rel="noopener noreferrer"><i class="fas fa-file-pdf"></i> Paper</a>
      {% endif %}
      {% if post.projecturl and post.projecturl != '' %}
        &nbsp;|&nbsp;<a class="pub-text-link" href="{{ post.projecturl }}" target="_blank" rel="noopener noreferrer"><i class="fas fa-globe"></i> Project</a>
      {% endif %}
      {% if post.coderepo and post.coderepo != '' %}
        &nbsp;|&nbsp;<a href="{{ post.codeurl }}" target="_blank" rel="noopener noreferrer"><img src="https://img.shields.io/github/stars/{{ post.coderepo }}?style=social&label=Code%20Stars&logoColor=2c4a88" alt="Code Stars" class="stars-badge"></a>
      {% endif %}
    </p>
  </div>
</div>
{% endfor %}

<h2 id="education">Education</h2>

<ul class="timeline">
  <li>
    <strong>PhD in Computer Engineering</strong>, Northeastern University
    <span class="timeline-meta">09/2024 – Present · Boston, MA</span>
  </li>
  <li>
    <strong>MS in Computer Science</strong>, Northeastern University
    <span class="timeline-meta">01/2022 – 08/2024 · Boston, MA</span>
  </li>
</ul>

<h2 id="experience">Experience</h2>

<ul class="timeline">
  <li>
    <strong>Research Intern</strong>, Bosch Research
    <span class="timeline-meta">05/2026 – Present · Sunnyvale, CA</span>
  </li>
  <li>
    <strong>Research Intern</strong>, Motional
    <span class="timeline-meta">09/2025 – 05/2026 · Boston, MA</span>
  </li>
</ul>

<style>
/* widen the main container on large screens, add more left breathing room */
#main { padding-left: 3em; }
@media (min-width: 80em) {
  #main { max-width: 1380px; padding-left: 4em; }
}
h2.no-underline {
  border-bottom: none;
  padding-bottom: 0;
}
html {
  scroll-behavior: smooth;
}
/* Offset anchor jumps so content isn't hidden under the sticky masthead */
h2[id] {
  scroll-margin-top: 80px;
}
.interest-tags {
  display: flex;
  gap: 0.6rem;
  flex-wrap: wrap;
  margin-top: 0.6rem;
}
.interest-tags span {
  background: #f2f3f3;
  border: 1px solid #e0e0e0;
  padding: 0.35rem 0.9rem;
  border-radius: 20px;
  font-size: 0.85rem;
  color: #3f3f3f;
  line-height: 1.3;
}
.pub-note {
  font-size: 0.9rem;
  color: #555;
  margin-bottom: 1rem;
}
.pub-heading-meta {
  font-size: 0.8rem;
  font-weight: normal;
  color: #555;
}
.pub-heading-meta a {
  color: #52adc8;
}
.paper-box {
  display: flex;
  gap: 1rem;
  padding: 0.9rem 0;
  border-bottom: 1px solid #efefef;
  align-items: stretch;
}
.paper-box:last-child { border-bottom: none; }
.paper-box-image {
  flex: 0 0 260px;
  max-width: 260px;
  align-self: stretch;
  position: relative;
  overflow: hidden;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
}
.paper-box-image img {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: contain;
  display: block;
}
.paper-box-text { flex: 1; min-width: 0; }
.paper-box-text p { margin: 0.25rem 0; }
.paper-title {
  font-weight: 600;
  font-size: 0.98rem;
  line-height: 1.4;
  color: #3f3f3f;
}
.paper-box .paper-authors {
  font-size: 0.8rem !important;
  color: #555;
  line-height: 1.5;
}
.paper-authors b { color: #3f3f3f; font-weight: 600; }
.paper-desc {
  font-size: 0.87rem;
  color: #666;
  line-height: 1.5;
}
.paper-box .paper-links { font-size: 0.72rem !important; color: #888; }
.paper-box .paper-links .pub-text-link {
  color: #3f3f3f !important;
  font-size: 0.65rem !important;
  text-decoration: none;
}
.paper-box .paper-links .pub-text-link:hover { text-decoration: underline; }
.paper-box .paper-links .stars-badge { height: 18px; vertical-align: -20%; }
.pub-venue { font-weight: 600; color: #52adc8; }
.paper-links a {
  font-size: 0.8rem;
  padding: 0.1rem 0.5rem;
  background: #f2f3f3;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
  color: #52adc8;
  text-decoration: none;
  margin-left: 0.25rem;
}
.paper-links a:hover {
  background: #52adc8;
  color: #fff;
  text-decoration: none;
}
@media (max-width: 600px) {
  .paper-box { flex-direction: column; }
  .paper-box-image { flex: unset; max-width: 100%; }
}
ul.timeline {
  list-style: none;
  padding-left: 0;
}
ul.timeline li {
  padding: 0.5rem 0;
  border-left: 2px solid #e0e0e0;
  padding-left: 1rem;
  margin-bottom: 0.4rem;
}
.timeline-meta {
  display: block;
  color: #777;
  font-size: 0.88rem;
  margin-top: 0.15rem;
}
</style>
