---
layout: page
title: "Projects"
permalink: /projects/
description: "Browser-based AI demos — neural networks running in JavaScript, no server required."
---

Two interactive demos. No backend. No ML framework. Just JavaScript, math, and your browser.

---

<div class="projects-list">

<div class="project-item">

## Handwriting Recognition in the Browser

<a href="https://cleardatalabs.github.io/hwrjs/">
  <img src="{{ '/assets/img/ai.gif' | relative_url }}" alt="Handwriting recognition demo" width="640" height="480">
</a>

A feedforward neural network that classifies handwritten characters in real time. Built with Angular and TypeScript, with the neural network implemented from scratch — no TensorFlow, no ONNX, no ML library of any kind.

The network takes a 12×12 binary grid derived from your pen strokes as input (144 numbers), passes it through a hidden layer with the same width, and outputs a probability distribution over characters. Training runs in the browser using backpropagation with periodic `setTimeout` yields to keep the UI responsive.

<div class="project-links">
  [<a href="https://cleardatalabs.github.io/hwrjs/" target="_blank" rel="noopener">Live Demo</a>]&nbsp;
  [<a href="https://github.com/cleardatalabs/hwrjs" target="_blank" rel="noopener">Source on GitHub</a>]
</div>

**Articles:**
- [Handwriting Recognition in the Browser, from Scratch](/articles/2026/04/02/hwrjs-handwriting-recognition-in-the-browser/) — overview
- [Seeing in Cells: How a Computer Reads Your Handwriting](/articles/2026/04/02/seeing-in-cells/) — input preprocessing
- [144 Numbers In, One Letter Out](/articles/2026/04/02/144-numbers-in-one-letter-out/) — network architecture
- [Backprop in the Browser](/articles/2026/04/02/backprop-in-the-browser/) — training

</div>

---

<div class="project-item">

## Knowledge Extraction from a Neural Network

<a href="https://cleardatalabs.github.io/knowledge-extract-ffnn-mnist/">
  <img src="{{ '/assets/img/mnist3.jpg' | relative_url }}" alt="Neural network knowledge visualization" width="640" height="427">
</a>

An educational project that asks: what has a network trained on MNIST actually learned? Two approaches are implemented, both in pure JavaScript:

1. **Causal Index** — compute the influence of each input pixel on each output by summing weighted paths through the network, then render as a heat map per digit.
2. **Iterative Input Adaptation** — start from random noise, apply stochastic hill climbing until the network confidently classifies the input as a target digit. A technique similar to DeepDream.

No compilation, no build step — open the HTML file and it runs.

<div class="project-links">
  [<a href="https://cleardatalabs.github.io/knowledge-extract-ffnn-mnist/" target="_blank" rel="noopener">Live Demo</a>]&nbsp;
  [<a href="https://github.com/cleardatalabs/knowledge-extract-ffnn-mnist" target="_blank" rel="noopener">Source on GitHub</a>]
</div>

**Articles:**
- [Extracting Knowledge Using Causal Index](/articles/2026/04/02/knowledge-extract-chapter-1/) — Chapter 1
- [Iterative Input Adaptation — Making the Network Dream](/articles/2026/04/02/knowledge-extract-chapter-2/) — Chapter 2

</div>

</div>
