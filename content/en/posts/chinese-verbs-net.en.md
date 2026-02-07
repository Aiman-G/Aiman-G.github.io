---
title: "Chinese Verb Network Explorer: Learn Mandarin Verbs as a System (Not a List)"
date: 2026-02-06
description: "An interactive Streamlit app that visualizes how two-character Chinese verbs connect through characters, tones, and semantics—using network science + phonology-aware tooling."
categories: ["tech"]

draft: false
tags: ["mandarin", "nlp", "network-science", "streamlit", "linguistics", "data-visualization"]
---


Chinese is a very interesting language in which most words are two characters long, and characters work like Lego blocks. A character can be used in many words. For me, memorizing verbs from a list is boring.
 Chinese has a structure that can be represented in an aesthetically pleasing way: networks.



For this reason, I built a Streamlit app that helps you explore **common two-character Mandarin verbs** through:
- **Character networks** (which characters combine with which),
- **Semantic maps** (UMAP projections of verb embeddings),
- **Tone-pattern analysis** (tone flows, tone networks, minimal contrasts),
- and **teaching tools** (coverage optimization + deck/curriculum builders).

 **Try the app here:** (https://explore-chinese.streamlit.app/)


---

## Why a verb network?

Two-character verbs are a huge part of everyday Mandarin. But learners often meet them as disconnected items (“记住 1000 个词”), which hides a useful fact:

> Many verbs share **reusable characters** and form **clusters** (“word families”).  
> If you learn the right hubs first, you unlock more vocabulary with less effort.

This app makes those hidden structures visible and interactive.

---

## Data & conventions (what’s inside)

The app uses a dataset of **1,140 Chinese Mandarin verbs**, with **953 two-character verbs** (the remainder are single-character). Pronunciations are prepared for learning by applying **third-tone sandhi**, and tone pairs use a simple convention:

- **Neutral tone is encoded as 5**, so tone patterns look like `3-4`, `2-5`, etc.  
- Tone sandhi is already applied in the pinyin used by the app (so the displayed pronunciations are closer to what you’d say in connected speech).

(These conventions are reflected directly in the app UI and filtering.)

---

## A quick tour (what you can do in 3 minutes)

### 1) Character Hub: “Which characters unlock the most verbs?”
**Page:** Character Network (汉字网络)

This is a directed graph where:
- **Nodes** = individual characters  
- **Edges** = a two-character verb formation `A → B` (meaning the verb is “AB”)

Inside the page you can:
- Filter by **verb class/category** (bilingual labels),
- Inspect a character’s role as a **starter** (out-degree) vs **ender** (in-degree),
- Use **Learning Pathways**:
  - **Degree centrality** → “super-connectors”
  - **Betweenness centrality** → “bridges” between clusters
- Explore **Word Families** discovered via community detection (clusters of tightly connected characters)

**How to use it (learner):** pick one high-centrality character and study 10–20 verbs containing it.  
**How to use it (teacher):** pick a community (“family”) and teach it as a themed unit.

---

### 2) Explore Two-Character Verbs: semantics + tone flow
**Page:** Explore Common Verbs (探索双字动词)

This page has two complementary lenses:

#### 🗺️ Semantic Map (UMAP)
An interactive scatter plot where each dot is a verb.
- Axes are `umap_x / umap_y` (a 2D projection).
- Nearby verbs tend to be **more similar in meaning** (under the embedding space used to compute the projection).
- Color = verb category.

You can also **highlight a specific verb** and read its details (pinyin, English gloss, tone pattern, and a category-conditioned transition probability shown in the UI).

#### 🌊 Tonal Flow (Sankey)
A Sankey diagram shows how often tone `X` on the first character flows into tone `Y` on the second character, based on counts within your current filters.

**How to use it:** if a tone pair is hard for you (e.g., `3-3`), filter to it and turn it into a focused practice set.

---

### 3) Tone Patterns: phonology-first exploration
**Page:** Tone Patterns (声调探索)

This section is for tone-aware learning and teaching. It includes:
- An interactive **tone network** (edges colored by tone pairs and weighted by frequency),
- **Tone pathways**: generate a character chain biased toward a target tone pair,
- **Tone in families**: tone distributions inside network communities,
- **Minimal tone-contrast sets**: verbs sharing the same base pinyin (digits removed) but differing in tone patterns—useful for perception/production drills,
- **Character tone profiles**: which tones a character tends to take depending on position,
- A **curriculum builder**: sample a tone-pair-focused deck, optionally weighted by network degree.

**How to use it:** pick 1–2 tone pairs for a week and generate a deck you can rehearse daily.

---

### 4) Verb Action Coach: tools for lesson design + deliberate practice
**Page:** Verb Action Coach (动词教学助理)

This is a “teacher/coach mode” with:
- Category distribution + phonetic breakdown (initials/finals),
- A **5×5 tone heatmap** (source tone → destination tone),
- A **Coverage Optimizer**:
  - Given a budget `k`, the app greedily selects characters that cover the maximum number of verbs (a classic greedy approximation to set cover).
  - Output includes coverage % plus a downloadable table of covered verbs.
- A **Deck Builder**:
  - Filter by tone pairs and by phonetic components (initial/final, first/second character),
  - Sample a study list (weighted by how frequently AB occurs in the dataset),
  - Download as CSV.
- A **Pitfalls** tab:
  - highlights characters with high tone variability (polyphony proxy),
  - and lists `3-3` tone-pattern verbs (useful for tone sandhi practice).

**How to use it (teacher):** set `k=20` and build a “high-yield character” mini-course.  
**How to use it (learner):** build a 40-card deck for one tone pair + one final (e.g., to target a pronunciation weakness).

---

## Under the hood (compact technical notes)

### Network representation
Two-character verbs are modeled as a directed graph `char1 → char2`. This makes it natural to compute:
- **Degree** (how many combinations a character participates in),
- **Betweenness** (bridge characters),
- **Communities** (clusters / “word families”).

### UMAP semantic map
The semantic map uses **UMAP**, a nonlinear dimensionality reduction method applied to verb embeddings, producing the `umap_x, umap_y` coordinates shown in the app.

### Coverage optimizer (greedy set cover intuition)
To maximize “verbs unlocked” under a character budget:
1. Start with all verb-edges uncovered.
2. Repeatedly pick the character that covers the most uncovered edges.
3. Stop when you hit `k` or everything is covered.

This is simple, fast, and surprisingly effective for building beginner-to-intermediate curricula.

---

## Caveats (important, especially for researchers)

- The semantic map is **exploratory**: 2D projections can distort distances, and embedding similarity is not the same as “ground-truth semantics.”
- Network structure depends on the dataset’s scope (frequency, selection criteria, labeling).

---

## How I’d love people to use this

If you’re a learner:
1) Start in **Character Hub** → pick 1 hub character  
2) Move to **Explore Verbs** → highlight 10 verbs containing it  
3) End in **Deck Builder** → export a focused practice list

If you’re a teacher:
1) Use **Word Families** → pick a cluster  
2) Use **Tone Heatmap** → select 1–2 common tone pairs  
3) Export a deck + build a lesson around it

---

## References
- Deng et al., *A Chinese verb semantic feature dataset (CVFD)*, **Behavior Research Methods** (Springer). DOI: 10.3758/s13428-022-02047-4.
- McInnes, Healy, Melville, *UMAP: Uniform Manifold Approximation and Projection for Dimension Reduction* (2018).

---

If you try the app and have feedback (bugs, feature ideas, collaboration), I’d genuinely love to hear it.
