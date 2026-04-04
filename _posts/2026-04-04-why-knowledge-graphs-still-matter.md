---
title: 'Why Knowledge Graphs Still Matter in the Age of LLMs'
date: 2026-04-04
permalink: /posts/2026/04/why-knowledge-graphs-still-matter/
tags:
  - Knowledge Graphs
  - Large Language Models
  - Neuro-symbolic AI
  - Explainability
  - FAIR Data
---

Large Language Models have taken the world by storm. GPT-4, Llama, Mistral — they can write code, summarise papers, answer complex questions, and even pass medical licensing exams. It is tempting to ask: if LLMs can do all of this, do we still need knowledge graphs?

The short answer is: absolutely yes. And in this post I want to explain why — not as a defence of old technology, but as an argument for a richer, more robust approach to AI.

## What LLMs Are Great At

Let us start by being honest about what LLMs do well. They are extraordinary at:

- **Language understanding and generation** — translating, summarising, paraphrasing, explaining
- **Pattern recognition across vast text corpora** — capturing statistical regularities in human knowledge
- **Few-shot reasoning** — solving new problems from just a few examples
- **Information extraction** — pulling structured facts from unstructured text

These are genuinely impressive capabilities, and they have real value in research, healthcare, and industry. I use LLMs in my own research and supervise students who build on them.

But LLMs also have well-documented, fundamental limitations — and this is exactly where knowledge graphs step in.

## The Core Problems with LLMs Alone

### 1. Hallucination

LLMs generate plausible-sounding text. They do not retrieve facts — they predict tokens. This means they can confidently state things that are false. In domains like drug discovery or clinical decision support, a confident hallucination is not a minor inconvenience — it can be dangerous.

Knowledge graphs, by contrast, are **grounded in verified, structured facts**. Every triple (`Drug A` — `interacts with` — `Drug B`) has a provenance: where it came from, who asserted it, when. You cannot hallucinate a triple in a knowledge graph.

### 2. Lack of Explainability

When an LLM predicts that two drugs interact, it cannot tell you *why*. There is no reasoning trace, no chain of evidence — just a probability distribution over tokens.

Knowledge graph-based reasoning is **inherently explainable**. A path through the graph — `Drug A` shares a target with `Drug B`, which is metabolised by `CYP3A4`, which is inhibited by `Drug C` — is a human-interpretable explanation. This matters enormously in regulated domains like healthcare, where clinicians and regulators need to understand and trust AI decisions.

### 3. Staleness and Closed-World Assumptions

LLMs are trained on a static snapshot of the world. They do not know about a drug approved last month or a gene function characterised last week. Updating them requires expensive retraining.

Knowledge graphs can be **continuously updated** with new facts as they are established, without retraining. This is particularly valuable in fast-moving fields like genomics or pharmacology.

### 4. No Native Support for FAIR Data

The [FAIR principles](https://www.go-fair.org/fair-principles/) — Findable, Accessible, Interoperable, Reusable — are foundational to modern scientific data management. Knowledge graphs, built on standards like RDF, OWL, and SPARQL, are the natural substrate for FAIR data. They make data **machine-readable and interoperable** across institutions and systems by design.

LLMs treat data as raw text. They provide no formal semantics, no shared vocabularies, no interoperability guarantees.

## Where Knowledge Graphs and LLMs Complement Each Other

The most exciting development in recent years is not "LLMs vs. knowledge graphs" — it is **LLMs + knowledge graphs**. This neuro-symbolic combination plays to the strengths of both:

- **LLMs for construction**: extracting entities and relations from unstructured text to populate knowledge graphs automatically
- **Knowledge graphs for grounding**: providing verified facts to reduce LLM hallucination (Retrieval-Augmented Generation, or RAG)
- **Knowledge graphs for evaluation**: using ontologies and formal semantics to benchmark LLM reasoning — an approach we explored directly in recent thesis work in our group
- **LLMs for querying**: allowing users to ask questions in natural language, which are then translated into structured SPARQL queries over a knowledge graph

In our own research — on drug-drug interaction prediction, food knowledge graphs, and the [AIDAVA project](https://aidava.eu) for clinical data integration — we consistently find that combining structured knowledge with neural approaches outperforms either alone.

## Conclusion

LLMs are powerful, and they are here to stay. But they are not a replacement for structured, semantically rich, FAIR-compliant knowledge representations. Knowledge graphs provide what LLMs fundamentally lack: **verified facts, explainable reasoning, interoperability, and continuous updatability**.

The future of AI in knowledge-intensive domains like healthcare and drug discovery is not a choice between symbolic and neural methods. It is the thoughtful combination of both — and knowledge graphs are the foundation that makes that combination possible.

---

*Remzi Celebi is an Assistant Professor at the Department of Advanced Computing Sciences (DACS), Maastricht University. His research focuses on knowledge graphs, neuro-symbolic AI, and FAIR data for personalized health and drug discovery.*
