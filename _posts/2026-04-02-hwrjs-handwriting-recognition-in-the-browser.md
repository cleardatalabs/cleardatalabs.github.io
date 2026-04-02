---
layout: post
title: "Handwriting Recognition in the Browser, from Scratch"
date: 2026-04-02
description: "A neural network that runs entirely in your browser, written in TypeScript with no ML libraries. Here's how it works and how to build it yourself."
image: /assets/img/ai.gif
demo_url: https://cleardatalabs.github.io/hwrjs/
---

Draw a letter. The network classifies it. No server, no cloud API, no GPU — just TypeScript and a browser tab.

[![Handwriting recognition demo](/assets/img/ai.gif)](https://cleardatalabs.github.io/hwrjs/)

[**Try the live demo →**](https://cleardatalabs.github.io/hwrjs/)

---

## What this is

[hwrjs](https://github.com/cleardatalabs/hwrjs) is a handwritten character recognizer built with Angular and TypeScript. The neural network inside it is implemented from scratch — every neuron, every weight, every gradient update is written by hand. No TensorFlow. No ONNX. No ML library of any kind.

You train it yourself: draw a few examples of each letter you want to recognize, click Train, and within seconds the network learns to distinguish your handwriting. Then draw a new letter and watch it predict.

The whole network is under 300 lines of TypeScript spread across three files.

## How it works

The pipeline has three stages:

**1. Input encoding** — When you draw on the canvas, the raw pen coordinates get normalized into a 12×12 binary grid. This grid is scale-invariant (it doesn't matter how big or small you draw) and position-invariant (it doesn't matter where on the canvas you draw). The result is 144 numbers, each 0 or 1.

**2. The network** — A feedforward neural network with three layers: 144 inputs → 144 hidden neurons → N outputs (one per letter you've trained on). Each neuron computes a weighted sum of its inputs and passes the result through a sigmoid activation function.

**3. Training** — Backpropagation with gradient descent. For each training sample, the network computes its error, propagates that error backward through the layers, and adjusts each weight proportionally. This runs in the browser's event loop using `setTimeout` to keep the UI responsive.

## The series

These three articles cover each stage in detail:

1. [Seeing in Cells: How a Computer Reads Your Handwriting](/articles/2026/04/02/seeing-in-cells/) — how raw pen strokes become a 144-number array
2. [144 Numbers In, One Letter Out](/articles/2026/04/02/144-numbers-in-one-letter-out/) — the network architecture, neuron math, and forward propagation
3. [Backprop in the Browser](/articles/2026/04/02/backprop-in-the-browser/) — gradient descent, backpropagation, and the browser UI synchronization trick

Each article is self-contained but they build on each other. Start from Part 1 if you want the full picture.

## Source code

The full project is on GitHub: [github.com/cleardatalabs/hwrjs](https://github.com/cleardatalabs/hwrjs). Fork it, change the learning rate, add a hidden layer, swap the activation function — the network is small enough that every parameter is accessible and every change is immediately visible in the demo.
