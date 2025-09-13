---
layout: page
title: RAG System
description: Basic Retrieval‑Augmented Generation system built from scratch.
img: assets/img/RAG.png
importance: 10 
category: Fun
github: hugogales/RAG
---

This wasn’t a huge project, but it was a solid learning exercise. I used an embedding model and a chunking strategy to split documents into pages. Each prompt was embedded, then I used cosine similarity to retrieve the most relevant chunks and fed them into a self‑hosted LLM.
I did this to build intuition for RAG design decisions. I found the trade‑offs around chunking (overlap, length, semantic vs. fixed) and retrieval tuning especially interesting.


