---
permalink: /
title: ""
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

<h2 id="about">About</h2>

I am a PhD Candidate in Computer Engineering at Northeastern University,
advised by Prof. [Lili Su](https://lilisu3.sites.northeastern.edu/). My
research focuses on autonomous driving and data efficiency, with an
emphasis on trajectory prediction, data curation, and scalable training
for self-driving systems.

Previously, I received my MS in Computer Science from Northeastern
University. I have been a research intern at Motional working on
autonomous driving, and I am currently a research intern at Bosch
Research in Sunnyvale, CA.

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
      <span class="pub-venue">{{ post.venue }}</span>
      {% if post.paperurl and post.paperurl != '' %}
        &nbsp;<a href="{{ post.paperurl }}" target="_blank" rel="noopener noreferrer">arXiv</a>
      {% endif %}
      {% if post.projecturl and post.projecturl != '' %}
        &nbsp;<a href="{{ post.projecturl }}" target="_blank" rel="noopener noreferrer">project</a>
      {% endif %}
      {% if post.codeurl and post.codeurl != '' %}
        &nbsp;<a href="{{ post.codeurl }}" target="_blank" rel="noopener noreferrer">code</a>
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
  align-items: flex-start;
}
.paper-box:last-child { border-bottom: none; }
.paper-box-image {
  flex: 0 0 180px;
  max-width: 180px;
}
.paper-box-image img {
  width: 100%;
  height: auto;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
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
.paper-links { font-size: 0.85rem; color: #888; }
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
