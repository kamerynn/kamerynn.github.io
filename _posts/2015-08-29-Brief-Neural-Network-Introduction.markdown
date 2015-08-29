---
layout: post
title:  "Brief Neural Network Introduction"
date:   2015-08-29 16:40
categories: mediator
tags: featured
image: /assets/article_images/2014-11-30-mediator_features/night-track.JPG
---

_Neural networks_ is a term you see often on programming blogs and startups. I pitched an idea to the other Hack Reactor students, touting that the idea can utilize machine learning and neural networks to do some cool stuff. Of course, I knew nothing about either of those things.

I got really lucky. The idea actually turned out to be possible using neural networks, so we dove into research articles and NN library documentation to figure out how to use them best. During that process, my mental image of neural networks changed from an all-powerful robot AI that could do anything, to a more realistic model - a CS representation of how neurons in the brain work in order for a computer to accomplish tasks that are normally hard for computers to do (and sometimes easy for people to do).

# Overview

Neural networks, from the outside, are sort of like a black box: you hand it inputs, and it spits out an output (or outputs). For this example, I'm going to focus on a simple neural network that uses training data in order to operate (the technical term is a _supervised feed-forward network_) There are a few things that make this kind of network special:
- It trains itself based on data that you supply it. For example, if you hand it a certain input and output, it will adjust its inner-workings to try and produce that output when the same input is handed to the network later on.
- This allows the network to _predict_ what the output should be for inputs that aren't defined.