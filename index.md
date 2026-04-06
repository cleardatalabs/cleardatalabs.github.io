---
layout: default
title: "Neural Networks Explained — Interactive Demos and Articles"
description: "AI experiments and in-depth articles explaining neural networks, backpropagation, and machine learning from scratch — running live"
image: /assets/img/ai.gif
---
<h1>Neural Networks Explained — Interactive Demos in the Browser</h1>
<p class="lead">Complex AI concepts, explained clearly and simply. Interactive experiments, in-depth articles, and hands-on projects — explore how AI actually works, from the math up.</p>

<h2 class="section-title">Recent Articles</h2>
<ul class="item-list">
  {% for post in site.posts limit:5 %}
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
<p><a href="/articles/">More articles</a></p>

<h2 class="section-title">Featured Projects</h2>

<div class="item">
  <a href="https://cleardatalabs.github.io/hwrjs/">
    <img src="{{ '/assets/img/ai.gif' | relative_url }}" width="640" height="480" alt="Handwriting recognition demo">
  </a>
  <h3>Handwriting Recognition in the Browser</h3>
  <p>A neural network that reads your handwriting — trained and running entirely in JavaScript, no server, no ML library. Draw a letter and watch it classify in real time.</p>
  <div class="item-links">
    <a href="https://cleardatalabs.github.io/hwrjs/">Live Demo</a>
    <a href="https://github.com/cleardatalabs/hwrjs">Source on GitHub</a>
    <a href="/articles/hwrjs-handwriting-recognition-in-the-browser/">Read the article</a>
  </div>
</div>

<div class="item">
  <a href="https://cleardatalabs.github.io/knowledge-extract-ffnn-mnist/">
    <img src="{{ '/assets/img/mnist3.jpg' | relative_url }}" width="640" height="427" alt="Neural network knowledge visualization">
  </a>
  <h3>Knowledge Extraction from a Neural Network</h3>
  <p>What does a network trained on MNIST actually learn? Two methods to find out: causal index heat maps and iterative input optimization — both running in pure JavaScript.</p>
  <div class="item-links">
    <a href="https://cleardatalabs.github.io/knowledge-extract-ffnn-mnist/">Live Demo</a>
    <a href="https://github.com/cleardatalabs/knowledge-extract-ffnn-mnist">Source on GitHub</a>
    <a href="/articles/knowledge-extract-chapter-1/">Read Chapter 1</a>
  </div>
</div>
