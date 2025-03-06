---
layout: post
title: Bias is Good (Inductively Speaking): Decoding the "Why"
date: 2025-03-06
categories: ["ml", "machine-learning", "ai", "inductive-bias"]
---

## Understanding Inductive Bias: The "Why" Behind the "How" in Machine Learning

This write-up stems from a conversation I had last week with my colleague. It made me think how people get the “how” (how things work, how to do something), but often don’t think about the “why” (the reasoning behind the choices that shaped those methods in the first place). 

### Inductive Bias

Inductive bias refers to the assumptions a machine learning algorithm makes about the relationship between inputs and outputs. These assumptions are necessary for learning, as they guide the model in predicting outputs for new data.

Inductive bias is what allows machine learning to work and makes the modeling easy. In simple terms, it restricts the hypothesis space - the set of all possible functions a model could learn from, to a smaller, more manageable subset. Without this restriction, a model would have infinitely many possible functions to choose from, making learning impossible.

For example, in linear regression, you could fit infinitely many curves to a finite set of points. But if you assume the function is linear, you drastically reduce the number of possibilities.

Let's look at a couple of classic examples: 

### 1. Why CNNs Work So Well for Images

It’s all about the structure of images, that neighboring pixels are highly correlated, meaning local features (edges, textures, shapes) are more relevant than distant ones. 

*Key Assumptions:*

*   **Local Connectivity:** CNNs assume that nearby pixels matter more than distant ones. That’s why convolutional filters (like 3x3 or 5x5) scan the image locally, picking up patterns like edges or corners.

*   **Translation Invariance:**  The same features (like edges or corners) can appear anywhere in the image, meaning, in image classification, a CNN assumes that detecting a "cat" in the top-left corner is just as meaningful as detecting it in the center. This is achieved through conv filters and weight sharing, allowing the network to detect the same feature across different locations.

### 2. RNNs in Sequence Processing

Why does RNNs work when dealing with sequences (things like text and time-series data)? Their strength lies in understanding temporal dependencies. In other words, they assume that the order of things matters. The word “not” appearing before “good” changes the meaning of a sentence.

Think about language. The core idea is that language isn't random. We don't just string words together arbitrarily. Grammar, syntax, context, and meaning all play a role in dictating what words are likely (or even possible) to follow a given sequence of words.

**Basically, The words you've already read drastically limit the possible words that can come next.**

*Key Assumptions:*

*   **Temporal Dependency:** RNNs assume that past information impacts future predictions. In the sentence “The cat sat on the…”, the next word is likely “mat”, not “airplane”, because of the previous words.

*   **Order Sensitivity:**     Unlike a bag of words approach, where word order doesn’t matter, RNNs process data sequentially. That’s why “I love apples” and “Apples love I” don’t mean the same thing.


### Why *Not* Use RNNs for Images?

Theoretically, you *could*. Like I explained, there's a reason why they aren't the first choice. The inductive bias of RNNs simply doesn't line up well with the structure of images. 

*   **Images Are Spatial, Not Sequential:** RNNs process one step at a time, while images have a 2D structure. There’s no natural “order” to pixels like there is with words in a sentence.

*   **Too Many Pixels, Too Many Steps:** A simple 224×224 grayscale image has over 50,000 pixel values. Processing all of that sequentially (Long-Range Dependencies)? Painfully slow and inefficient.

### When *Can* You Use RNNs for Images?

It's not a complete no! RNNs can be useful for specific image-related tasks combined with CNNs, where sequential processing makes sense.

For example, 

*   **Image Captioning:** Instead of processing raw pixels, an RNN can take CNN-extracted features and generate descriptive text.

*   **Video Processing:** Since videos are just sequences of images, RNNs can analyze data over time.

### The Takeaway

At the end of the day, choosing the right model for the right problem is all about understanding its inductive bias and how well it aligns with your data.

It is more than just throwing data at it and hoping for the best (although [this talk](https://www.youtube.com/watch?v=orDKvo8h71o) tells otherwise​​ 🧐)

### References:

*   [Inductiveb Bias Wiki](https://en.wikipedia.org/wiki/Inductive_bias)
*   [A Reddit Thread](https://www.reddit.com/r/MLQuestions/comments/egof3l/explanation_of_inductive_bias/)
