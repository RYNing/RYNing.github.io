---
permalink: /
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

<h2 id="about">About</h2>

Hi, I am Ruining Yang (pronounce: ray-ning-young), a third year PhD in
Computer Engineering at [TRUST AI Lab](https://lilisu3.sites.northeastern.edu/),
<span class="nowrap"><img class="inline-logo" src="{{ '/images/logos/northeastern.jpeg' | relative_url }}" alt="Northeastern">Northeastern</span> University. I am fortunate to be
advised by Prof. [Lili Su](https://coe.northeastern.edu/people/su-lili/).
My research focuses on efficient learning from informative samples for
End-to-End, Vision-Language-Action (VLA), and World Action Model (WAM)
approaches in autonomous driving, with an emphasis
on robust decision-making in complex real-world scenarios.

<h2 id="education">Education</h2>

<ul class="timeline with-logos">
  <li>
    <img class="timeline-logo" src="{{ '/images/logos/northeastern.jpeg' | relative_url }}" alt="Northeastern University logo">
    <div>
      <strong>PhD in Computer Engineering</strong>, Northeastern University
      <span class="timeline-meta">09/2024 – Present · Boston, MA</span>
    </div>
  </li>
  <li>
    <img class="timeline-logo" src="{{ '/images/logos/northeastern.jpeg' | relative_url }}" alt="Northeastern University logo">
    <div>
      <strong>MS in Computer Science</strong>, Northeastern University
      <span class="timeline-meta">01/2022 – 08/2024 · Boston, MA</span>
    </div>
  </li>
  <li>
    <img class="timeline-logo" src="{{ '/images/logos/cu-denver.png' | relative_url }}" alt="University of Colorado Denver logo">
    <div>
      <strong>BA in Communications</strong>, University of Colorado Denver
      <span class="timeline-meta">03/2018 – 07/2021 · Denver, CO</span>
    </div>
  </li>
</ul>

{% include experience.html %}

<h2 id="publications" class="pub-heading">📝 Selected Publications
  <span class="pub-heading-meta">
    | <a href="{{ '/publications/' | relative_url }}">See All Publications &gt;</a>
    | <span class="pub-legend"><sup>*</sup> Equal contribution &nbsp; <sup>†</sup> Corresponding author</span>
  </span>
</h2>

{% assign sorted_pubs = site.publications | where_exp: "p", "p.selected != false" | sort: 'sort_order' %}
{% for post in sorted_pubs %}
{% include paper-box.html pub=post %}
{% endfor %}

{% include page-styles.html %}
