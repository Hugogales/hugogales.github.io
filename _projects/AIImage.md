---
layout: page
title: AI image detector
description: Made and tested various models to detect AI from real images.
img: assets/img/AIImage.jpg
importance: 2
category: School
github: 
---

## Summary

Yes this description is AI generated from my final report for this project. Did this work with two of my friends for a class final project.

- **What you set out to do**
  - Big question: “Can we tell if a picture is AI‑made or real using quick stats like brightness, contrast, saturation, etc.—and how does that stack up against a CNN?” Spoiler: the CNN is the gym bro who actually lifts.

- **Data at a glance**
  - Two datasets:
    - **Dataset 1**: ~12k low‑res images, 50/50 real vs. fake—great for “messy real‑world” testing.
    - **Dataset 2**: ~900 higher‑quality art images, ~54/46 split—good for subtle style cues.

- **What We measured**
  - Brightness, saturation, contrast, number of unique pixels, and RGB color ranges.
  - Sanity‑checked with t‑tests and correlations. The density plots show the classes do nudge apart—just not cleanly enough to win the whole game.

- **Model adventures**
  - Tried PCA to compress the features. Verdict: meh—no real boost, so dropped.
  - Logistic Regression / Random Forest on the hand‑crafted features landed around ~0.64 for accuracy/precision/recall/F1. Feature importance crowned brightness/contrast/saturation as the top bouncers.
  - Then the CNN strolled in, looked at raw pixels, and posted ~0.97 across the board. Yowza.
  - Conclusion: differences exist and are useful, but CNNs capture the nuance way better. Future idea: try a GAN for continual learning.

---

## Why this is exciting for “big data” even without looking at images

Think of the simple stats as a no‑peek pre‑screen—a fast, cheap bouncer before the VIP lounge:

- **Triage at scale**: Run brightness/contrast/saturation/unique‑pixel counts in milliseconds to flag likely AI images across millions of files.
- **Save compute**: Only send the “maybe” pile to your expensive CNN; pass the obvious ones or toss them.
- **Privacy‑friendlier**: You’re not “seeing” the images—just their aggregates—so the first pass can happen where data lives (edge / on‑prem), reducing transfers.
- **Ops hygiene**: Use thresholds (e.g., odd saturation ranges) to auto‑quarantine suspicious content and keep downstream systems cleaner.
- **Real‑time ready**: These features can run inline in ingestion pipelines or queues as a first‑stage filter.

Mental model: brightness/contrast = the door staff (“ID please”); CNN = the back‑room expert who interviews edge cases. Together, you get speed + accuracy without melting your GPUs.