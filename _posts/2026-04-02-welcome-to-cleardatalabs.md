---
layout: post
title: "Building AI in the Browser: What ClearDataLabs Is About"
date: 2026-04-02
description: "An introduction to the blog, the projects, and the philosophy of building neural networks from scratch without ML frameworks."
---

Most machine learning tutorials hand you a library and a dataset. You call `model.fit()`, watch the accuracy climb, and walk away with a trained model and no particular understanding of what just happened.

That's useful. But it's not the only way to learn.

ClearDataLabs exists for the other approach: build it yourself. Take a neural network — the math, the weights, the gradient updates — and write it from scratch in JavaScript. No TensorFlow. No PyTorch. No NumPy. Just arithmetic, running in your browser.

## Why JavaScript

The browser is the most accessible runtime in the world. No install, no environment setup, no GPU required. If it runs here, anyone with a laptop can see it work and inspect the source. That constraint also keeps things honest: if the implementation is too complex to run in a browser tab, it's probably too complex to explain clearly.

## The projects

**[Handwriting Recognition in the Browser](/projects/)** — a feedforward neural network that reads handwritten characters in real time. You draw a letter, the network classifies it. It trains in the browser, using backpropagation implemented from first principles in TypeScript. The entire model is under 300 lines of code.

**[Knowledge Extraction from a Neural Network](/projects/)** — an MNIST digit classifier, trained and frozen, dissected two ways. First, by computing a causal index that measures how much each input pixel influenced each output class. Second, by optimizing a blank image until the network "sees" a specific digit in it — a browser-native version of DeepDream.

## What you'll find here

Articles that go deep on the implementation. Not "here's the concept," but "here's the code, here's why it works, here's where it breaks." Written for anyone curious enough to want to understand neural networks, not just use them.

Start with the [projects page](/projects/) for the demos, or jump straight into [the articles](/articles/).
