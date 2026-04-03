---
layout: post
title: "Making a Neural Network Dream: DeepDream-Style Visualization in JavaScript"
date: 2026-04-02
description: "A DeepDream-style technique in pure JavaScript: optimize a blank image until a neural network confidently sees a digit. Visualize what an MNIST network has learned."
image: /assets/img/mnist3.jpg
series: knowledge-extract
series_part: 2
demo_url: https://cleardatalabs.github.io/knowledge-extract-ffnn-mnist/
---

*This is Chapter 2 of a two-part series on knowledge extraction from neural networks. [Live demo](https://cleardatalabs.github.io/knowledge-extract-ffnn-mnist/) · [Source on GitHub](https://github.com/cleardatalabs/knowledge-extract-ffnn-mnist)*

---

Iterative input adaptation is a technique for visualizing what a neural network has learned: start with a blank image, randomly perturb individual pixels, and keep changes that increase the network's confidence for a target class. The result is a DeepDream-style image that reveals the network's internal concept of each digit — implemented here in pure JavaScript with no ML libraries.

## Recap

In [Chapter 1](/articles/knowledge-extract-chapter-1/), we extracted knowledge from a feed-forward neural network by computing the causal index — a weighted sum of paths from each input pixel to each output class. The result was a set of static heat maps that reveal which pixels matter most for each digit.

That approach is fast and analytical, but it has a limitation: it only considers the linear contribution of weights, ignoring the non-linear activation functions that make neural networks powerful. Can we do better?

## A Different Approach: Optimizing the Input

Instead of analyzing weights directly, we can take a completely different path: start with a random (mostly blank) image and iteratively modify it until the network confidently classifies it as a specific digit. This is conceptually similar to Google's [DeepDream](https://en.wikipedia.org/wiki/DeepDream), though applied to a much simpler network.

The idea is straightforward:

1. Start with a near-blank 28x28 image (pixel values near -1, with small random noise).
2. Randomly perturb a single pixel by a small amount.
3. Run the modified image through the network and check the output probability for the target digit.
4. If the probability improved (i.e., the error decreased), keep the change. Otherwise, discard it.
5. Repeat thousands of times.

This is essentially a form of **stochastic hill climbing** — a simple optimization technique that doesn't require computing gradients.

## The Error Function

The core of the optimization is the error function. At its simplest, the error for a target digit `k` is:

```
error = 1 - network_output[k]
```

We want to minimize this, meaning we want the network's confidence in digit `k` to approach 1.0.

### Optional: Smoothness Regularization

Raw optimization can produce noisy, speckled images. To encourage smoother, more natural-looking results, we add a regularization term that penalizes pixels that differ significantly from their neighbors:

```
regularization = sum of (pixel - average_of_neighbors)^2
```

The final error becomes `error + lambda * regularization`, where `lambda` is a small weighting factor. In the demo, this is controlled by the "Force Smoothness" checkbox.

## The Implementation

The `Model` object handles the full optimization loop:

- `initInputs()` — creates a near-blank starting image
- `inputsChanged()` — generates a candidate image by randomly perturbing one pixel
- `calcErr(inputs, out)` — computes the error (with optional regularization)
- `run()` — the main loop: tries 100 random perturbations per frame, keeps improvements, redraws, and schedules the next frame

```javascript
this.run = function () {
    var out = selectedDigit;
    var bestErr = this.calcErr(this.inputs, out);

    for (var i = 0; i < 100; i++) {
        var newInputs = this.inputsChanged();
        var newErr = this.calcErr(newInputs, out);
        if (newErr < bestErr) {
            bestErr = newErr;
            this.inputs = newInputs;
        }
    }

    this.draw();
    setTimeout(function () { self.run(); }, 0);
};
```

## Results

After several seconds of running, recognizable digit shapes emerge from the noise. With smoothness regularization enabled, the images are cleaner and more closely resemble human handwriting. Without it, the network finds noisier patterns that still achieve high confidence — revealing the kinds of subtle pixel arrangements the network responds to, even if they don't look natural to us.

Try it yourself in the [interactive demo](https://cleardatalabs.github.io/knowledge-extract-ffnn-mnist/). Select a digit, click Run, and watch the image evolve in real time.

## Takeaways

This approach demonstrates that even a simple optimization strategy (no gradients, no backpropagation through the input) can reveal what a neural network has learned. The generated images serve as a form of **model visualization** — they show us the network's internal concept of each digit.

Comparing the two chapters: the causal index method (Chapter 1) gives a quick analytical snapshot, while iterative adaptation (Chapter 2) lets the network actively construct its ideal input. Both are valuable perspectives on the same model.

---

<div class="post-nav">
  <a href="/articles/knowledge-extract-chapter-1/">&larr; Chapter 1: Causal Index</a>
  <span></span>
</div>
