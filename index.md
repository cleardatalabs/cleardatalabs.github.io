---
layout: default
title: "ClearDataLabs"
description: "Complex AI concepts, explained clear and easy way."
---

<div class="home-intro">
  <p>Complex AI concepts, explained clear and easy way. Interactive experiments, in-depth articles, and hands-on projects — explore how AI actually works, from the math up.</p>
</div>

<div class="recent-articles">
  <h2>Recent Articles</h2>
  <ul class="post-list">
    {% for post in site.posts limit:5 %}
    <li class="post-item">
      <a class="post-item-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <div class="post-item-meta">
        <time class="post-item-date" datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%b %-d, %Y" }}</time>
        {% if post.series %}<span class="post-item-series">{{ post.series }}</span>{% endif %}
      </div>
      {% if post.description %}<p class="post-item-desc">{{ post.description }}</p>{% endif %}
    </li>
    {% endfor %}
  </ul>
  <p><a href="/articles/">More articles</a></p>
</div>

<div class="featured-projects">
  <h2>Featured Projects</h2>

  <div class="project-item">
    <a href="https://cleardatalabs.github.io/hwrjs/">
      <img src="{{ '/assets/img/ai.gif' | relative_url }}" width="640" height="480" alt="Handwriting recognition demo">
    </a>
    <h3>Handwriting Recognition in the Browser</h3>
    <p>A neural network that reads your handwriting — trained and running entirely in JavaScript, no server, no ML library. Draw a letter and watch it classify in real time.</p>
    <div class="project-links">
      [<a href="https://cleardatalabs.github.io/hwrjs/">Live Demo</a>]&nbsp;
      [<a href="https://github.com/cleardatalabs/hwrjs">Source on GitHub</a>]&nbsp;
      [<a href="/articles/2026/04/02/hwrjs-handwriting-recognition-in-the-browser/">Read the article</a>]
    </div>
  </div>

  <div class="project-item">
    <a href="https://cleardatalabs.github.io/knowledge-extract-ffnn-mnist/">
      <img src="{{ '/assets/img/mnist3.jpg' | relative_url }}" width="640" height="427" alt="Neural network knowledge visualization">
    </a>
    <h3>Knowledge Extraction from a Neural Network</h3>
    <p>What does a network trained on MNIST actually learn? Two methods to find out: causal index heat maps and iterative input optimization — both running in pure JavaScript.</p>
    <div class="project-links">
      [<a href="https://cleardatalabs.github.io/knowledge-extract-ffnn-mnist/">Live Demo</a>]&nbsp;
      [<a href="https://github.com/cleardatalabs/knowledge-extract-ffnn-mnist">Source on GitHub</a>]&nbsp;
      [<a href="/articles/2026/04/02/knowledge-extract-chapter-1/">Read Chapter 1</a>]
    </div>
  </div>
</div>
