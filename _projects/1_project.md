---
layout: page
title: Undergraduate Research
description: Applied research project; methods, contributions, and outcomes.
img: assets/img/undergraduate-research.jpg
importance: 1
category: work
github: 
related_publications: true
---

## Summary

This project tackles a central problem in cooperative multi‑agent reinforcement learning: enabling a team of learning agents to truly collaborate at scale.

- Centralized execution: full context for joint actions, but the joint‑action space explodes as team size grows.
- Decentralized execution: avoids the explosion, but agents must decide what/when/with‑whom to share, making coordination and learning harder.

We introduce Team‑Attention‑Actor‑Critic (TAAC) to retain centralized execution benefits without joint‑action paralysis. Collaboration is explicit: the actor consults teammates’ internal representations via attention, and a light regularizer nudges agents toward complementary roles. Unlike attention‑based critics used only during training (e.g., MAAC in CTDE), TAAC performs selective, attention‑based exchange at decision time.

### Method (TAAC)
- Encode each agent’s observation into an embedding.
- Use multi‑headed attention to let agents query teammates and form a team‑aware embedding.
- Policy head outputs an action distribution from that embedding.
- Critic mirrors the flow, conditions on actions, and also keeps a pre‑attention embedding to ease value estimation.
- Training to promote collaboration:
  - Multi‑agent baseline for stable policy gradients and credit assignment.
  - Light “conformity” loss discouraging identical representations, encouraging diverse yet compatible roles.

### Evaluation
- Domain: simulated 3‑v‑3 soccer where teamwork is essential.
- Observations: relative positions, ball kinematics, goals, and boundaries.
- Actions: small set of movement and kick options.
- Rewards: shaping toward ball, team progress to opponent goal, scoring bonus, spacing incentive.
- Curriculum: static → random → league play vs past agents.
- Baselines: PPO (decentralized) and MAAC (attention‑critic with decentralized execution).

### Results
- TAAC achieves the strongest league performance and clearer collaborative behavior (connectivity, purposeful possession exchanges resembling passing).
- PPO is competitive but often settles into spread shapes with clustered attackers (lower connectivity).
- MAAC underperforms here, likely due to sensitivity and limited training.

### Next steps
- Retune and train MAAC longer; run ablations (actor‑attention, critic‑attention, conformity loss); test in additional cooperative domains and under partial observability or bandwidth limits.

Below is a video of TAAC going against PPO in the football environment.

{% include video.liquid path="assets/video/football.mp4" class="img-fluid rounded z-depth-1" controls=true %}

I am currently working on extending these results to other environments. Below is a video of how it is going so far. In this environment the goal is for the boxes to learn to stack on top of each other such that they can reach the highest point possible (i.e., build the tallest tower).

{% include video.liquid path="assets/video/boxjump.mp4" class="img-fluid rounded z-depth-1" controls=true %}




