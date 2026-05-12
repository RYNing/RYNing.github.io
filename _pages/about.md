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

You can also find my publications on
<a href="{{ site.author.googlescholar }}">my Google Scholar profile</a>.

<ol class="pub-list" reversed>
{% for post in site.publications reversed %}
  <li>
    <span class="pub-title">{{ post.title }}</span><br>
    <span class="pub-citation">{{ post.citation | markdownify | remove: '<p>' | remove: '</p>' }}</span>
    {% if post.paperurl and post.paperurl != '' %}
      &nbsp;<a href="{{ post.paperurl }}" class="pub-link">[paper]</a>
    {% endif %}
  </li>
{% endfor %}
</ol>

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
.pub-list {
  padding-left: 1.2rem;
}
.pub-list li {
  padding: 0.5rem 0;
  line-height: 1.6;
}
.pub-title {
  font-weight: 600;
}
.pub-citation {
  font-size: 0.9rem;
  color: #555;
}
.pub-link {
  font-size: 0.8rem;
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
