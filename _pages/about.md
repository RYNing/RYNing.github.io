---
permalink: /
title: ""
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

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

<h2 id="publications">Publications</h2>

<p class="pub-note">
  You can also find my publications on
  <a href="{{ site.author.googlescholar }}">my Google Scholar</a>.
</p>

<ul class="pub-list">
{% for post in site.publications reversed %}
  <li>
    {{ post.authors_html | default: post.citation | markdownify | remove: '<p>' | remove: '</p>' }}
    &ldquo;{{ post.title }}.&rdquo;
    <span class="pub-venue">{{ post.venue }}</span>.
    {% if post.paperurl and post.paperurl != '' %}
      <span class="pub-links"><a href="{{ post.paperurl }}" target="_blank" rel="noopener noreferrer">arXiv</a></span>
    {% endif %}
  </li>
{% endfor %}
</ul>

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
.pub-list {
  list-style: none;
  padding-left: 0;
}
.pub-list li {
  padding: 0.6rem 0;
  font-size: 0.9rem;
  line-height: 1.7;
  padding-left: 1rem;
  position: relative;
  color: #3f3f3f;
}
.pub-list li::before {
  content: "\2022";
  color: #52adc8;
  font-weight: 700;
  position: absolute;
  left: 0;
  top: 0.6rem;
}
.pub-list li b {
  font-weight: 600;
  color: #3f3f3f;
}
.pub-venue {
  font-weight: 600;
  color: #52adc8;
}
.pub-links a {
  font-size: 0.8rem;
  margin-left: 0.3rem;
  padding: 0.1rem 0.4rem;
  background: #f2f3f3;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
  color: #52adc8;
  text-decoration: none;
}
.pub-links a:hover {
  background: #52adc8;
  color: #fff;
  text-decoration: none;
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
