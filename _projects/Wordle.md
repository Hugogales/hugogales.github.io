---
layout: page
title: Wordle App
description: Replicated Wordle and made a sick AI.
img: assets/img/wordle-app.png
importance: 3
category: Fun
github: Hugogales/Wordle_App
---

As part of a class project, I was tasked with making a Wordle game. I went a bit above and beyond and built an AI to solve Wordle as efficiently as possible, inspired by a video from the legend 3Blue1Brown:

{% include video.liquid path="https://www.youtube.com/watch?v=v68zYyaEmEA&vl=en" title="3Blue1Brown Wordle strategy" width="560" height="315" %}

The AI uses information theory to pick the word that, on average, yields the most information (measured in bits). It achieves about 3.8 guesses on average. A future improvement is biasing guesses toward words more likely to be actual solutions, as described in the 3Blue1Brown video.

I also added different game modes such as Evil Wordle, where the word changes after every guess (it’s still solvable!).

I packaged it as an app, added multi‑language support so my Spanish family could play, and included stats.

Below are some pictures of my app:

<img src="/assets/img/wordle1.png" alt="Wordle App Screenshot 1" width="350" style="margin:10px;">
<img src="/assets/img/wordle2.png" alt="Wordle App Screenshot 2" width="350" style="margin:10px;">
<img src="/assets/img/wordle3.png" alt="Wordle App Screenshot 3" width="350" style="margin:10px;">
