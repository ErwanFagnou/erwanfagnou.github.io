---
title: "Personal Research on Deep Neural Network Optimization"
excerpt: "Creation of novel optimization algorithms for optimizing deep neural networks."
collection: projects
teaser: "/images/projects/mlp_optimizers/results_lowres.png"
teaser_type: "image"
teaser_video_hover: false
dates: "Sept. 2021 - Ongoing"
sorting_key: 992109
---

## Context

I had worked on algorithms for the optimization of single layer neural networks in a previous project (see [here](/projects/nonlinear-least-squares/)). In this project, I wanted to apply what I had learned to deep neural networks.

## My algorithms

As this is still an ongoing project that I find promising, I prefer not to disclose the details of my algorithm. However, I can say that, like my previous project, I am inspired by the least squares to update the parameters of the neural network.

As my method was originally found intuitively, I am currently trying to prove its theoretical properties. What is surprising is that although it is a first-order method, it is able to minimize the loss much faster than the standard stochastic gradient descent, even when I force it to have the same step size as the SGD! As gradient descent is optimal when considering the first order approximation of the loss, this suggests that my method somewhat considers a higher order approximation of the loss.

I found some interesting similarities with Newton's method, but my method is much more efficient as it is a first-order method (Newton's method is a second-order method, so it requires computing the Hessian matrix).

I have currently tested my method on a few tasks. I used a neural network with 2 hidden layers, that I trained on MNIST and CIFAR10, with great results:

{% include project_image.html
path="/images/projects/mlp_optimizers/results.png"
caption="Neural network trained on CIFAR10 with my method (GLS) and Adam. The learning rates chosen are variations around the optimal values. The y-axis is in log scale."
%}

Although my method takes more time per epoch (4.3s, against 2.6s for Adam), it is able to reach a loss that would take Adam much more epochs to each.

I also trained an autoencoder on CIFAR10, to challenge my optimizer. I am currently investigating some issues: it seems that it performs poorly when the output dimension of a layer is larger than the input dimension.
