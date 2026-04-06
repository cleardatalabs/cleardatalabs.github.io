---
layout: page
title: "Neural Network Articles | ClearDataLabs"
permalink: /articles/
description: "Technical articles about neural networks, browser-based AI, and building ML systems from scratch."
---

<ul class="item-list">
  {% for post in site.posts %}
  <li class="item">
    <a href="{{ post.url | relative_url }}"><strong>{{ post.title }}</strong></a>
    <div>
      <time class="date" datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%b %-d, %Y" }}</time>
      {% if post.series %}<span class="badge">{{ post.series }}</span>{% endif %}
    </div>
    {% if post.description %}<p>{{ post.description }}</p>{% endif %}
  </li>
  {% endfor %}
</ul>
