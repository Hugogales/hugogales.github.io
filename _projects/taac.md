---
layout: page
title: Undergraduate Research
description: Applied research project; methods, contributions, and outcomes.
img: assets/img/undergraduate-research.jpg
importance: 1
category: Spotlight
github: Hugogales/Undergraduate_Research
related_publications: true
---

## Summary

This project introduces a novel algorithm, Team‑Attention‑Actor‑Critic (TAAC), designed to improve collaboration between agents. TAAC uses multi‑headed attention across agents to enable unrestricted inter‑agent communication. Rather than imposing hard communication limits, TAAC lets the policy learn whom to communicate with and when. Many prior algorithms for collaboration and coordination impose strict constraints; TAAC relaxes several of these.

We chose a Centralized‑Training‑and‑Centralized‑Execution (CTCE) setup to enable explicit collaboration via direct communication, in contrast to Centralized‑Training‑and‑Decentralized‑Execution (CTDE) and Decentralized‑Training‑and‑Decentralized‑Execution (DTDE), which model collaboration implicitly.

We additionally introduced a new idea called conformity loss which is works through the cosine similarity of agent embedding post attention, to promote collaboration. It works on the assumption that collaboration requires different thoughts and agents working in on seperate yet complimentary tasks. While conformity loss may clearly be more hurtfull than helpfull in enviroments where the assumption does not hold, it can be tuned by caping and scaling the loss to match the type of coordination in the enviroment.

We have tested TAAC and compared to different algorithms from a CTDE (MAAC) and a DTDE (PPO) Scheme from different algorithms in Football enviroment where coordination and collaboration are highly important. Below is video of a game of TAAC demonstrating its peforamance.

{% include video.liquid path="assets/video/football.mp4" class="img-fluid rounded z-depth-1" controls=true %}

This work helped me win the ROSIE Competition and attend ICMLA to present and publish. Huge thanks to Jeremy Kedziora, Ph.D.—an incredible mentor who guided this research. Couldn’t have done it without him.

### Algorithm (TAAC)
- Encode each agent’s observation into an embedding using an MLP.
- Use multi‑headed attention to let agents query teammates and form a team‑aware embedding.
- Policy head outputs an action distribution from that embedding.
- Critic mirrors the flow, conditions on actions, and also keeps a pre‑attention embedding to ease value estimation.
- Training to promote collaboration:
  - Multi-agent Counterfactual baseline for stable policy gradients and credit assignment.
  - Novel Conformity loss discouraging identical representations, encouraging diverse yet compatible roles.

Below is an image of the algorithm:

{% include figure.liquid path="assets/img/TAAC_algorithm.png" class="img-fluid rounded z-depth-1" alt="TAAC algorithm diagram" %}

### Evaluation
- Domain: simulated 3‑v‑3 soccer where teamwork is essential.
- Observations: relative positions, ball kinematics, goals, and boundaries.
- Actions: small set of movement and kick options.
- Rewards: shaping toward ball, team progress to opponent goal, scoring bonus, spacing incentive.
- Curriculum Learning format: static → random → league play vs past agents.
- Baselines: PPO (decentralized) and MAAC (attention‑critic with decentralized execution).

### Results
- TAAC achieves the strongest league performance and clearer collaborative behavior (connectivity, purposeful possession exchanges resembling passing).
- PPO is competitive but often settles into spread shapes with clustered attackers (lower connectivity).
- MAAC underperforms here, likely due to not finding the optimal hyperparams a clear weakness in our research.

### Next steps
I’m actively expanding this work to build a more convincing body of evidence for TAAC’s effectiveness. I’m training across new environments—here’s a sneak peek:

{% include video.liquid path="assets/video/boxjump.mp4" class="img-fluid rounded z-depth-1" controls=true %}

Planned next steps: evaluate across more environments, test scalability to many agents, and study conformity‑loss settings. The goal is to really understand how TAAC performs and where it stands versus other methods. I aim to submit this as a journal article once complete.

Please reach out with any questions, ideas or feedback (if I am being an idiot).
Read more about my work here: [TAAC paper on arXiv](https://arxiv.org/abs/2507.22782)
{: .mt-2 }
<a class="btn btn-sm z-depth-0" href="https://arxiv.org/abs/2507.22782" role="button">arXiv</a>

