---
layout: post
title:  "Brief Neural Network Introduction"
date:   2015-08-29 16:40
categories: mediator
tags: neural networks
image: /assets/article_images/2014-11-30-mediator_features/night-track.JPG
---

_Neural networks_ is a term you see often on programming blogs and startups. I pitched an idea to the other Hack Reactor students, touting that the idea can utilize machine learning and neural networks to do some cool stuff. Of course, I knew nothing about either of those things.

I got really lucky. The idea actually turned out to be possible using neural networks, so we dove into research articles and NN library documentation to figure out how to use them best. During that process, my mental image of neural networks changed from an all-powerful robot AI that could do anything, to a more realistic model - a CS representation of how neurons in the brain work in order for a computer to accomplish tasks that are normally hard for computers to do (and sometimes easy for people to do).

# Overview

Neural networks, from the outside, are sort of like a black box: you hand it inputs, and it spits out an output (or outputs). For this example, I'm going to focus on a simple neural network that uses training data in order to operate (the technical term is a _supervised feed-forward network_).

There are a few things that make this kind of network special:

* It trains itself based on data that you supply it.
* This allows the network to _predict_ what the output should be for inputs that aren't defined.

The _training_ process simply involves adjusting weights inside of the neural network. These weights help process the inputs to match close to what the expected output should be. There's a lot of different ways to do this, but a very simple way is to use _gradient descent_, which the NN library of your choice will likely implement for you.

This alone is friggin awesome. We can hand it inputs that we haven't explicitly defined and it will use the training data we've supplied it to predict what the output should be. Compare this to a hash table. If you try to retrieve a value for a key that is undefined, you're out of luck.

Neural networks have a wide range of use cases and implementations, much broader than this post illustrates. A few resources to check out if you're curious:

http://karpathy.github.io/neuralnets/
http://www.heatonresearch.com/content/non-mathematical-introduction-using-neural-networks
http://neuralnetworksanddeeplearning.com/