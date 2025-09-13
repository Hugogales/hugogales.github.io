---
layout: page
title: Snake Q‑Learning
description: Trained an agent to play Snake using Q‑learning.
img: assets/img/snake.jpg
importance: 5
category: Spotlight
github: hugogales/Snake-Q-Learning
---

## Summary

To get started with reinforcement learning I wanted to get Q-learning to learn how to play snake.
After finding an enviroment for this we used a simple qtable focusing on the observations of:

- **Observations:**
  - Is there danger (wall or body) **ahead**, **to the left**, or **to the right** of the snake's current direction?
  - Is the apple **ahead**, **to the left**, or **to the right** relative to the snake's current direction?

- **Actions:**
  - Move **up**
  - Move **down**
  - Move **left**
  - Move **right**


To improve the algorithm I mostly attempted playing with hyperparameters simply the state-action space (by making the observation and action relative to snakes direction). It managed to get a high-score of 140 which I think it pretty good. However it failed to learn late game strategies to tidy up its tail, it only learnt how to go to apples and avoid walls and its tail. Try a deep-learning aproach with more information in the state would likely allow for more complex strategies. (or I could just do a hamilton cycle and just win)

Below is a video of it working:

{% include video.liquid path="assets/video/Snake-q-learning.mp4" title="Snake Q-Learning Agent Demo" width="560" height="315" %}
