---
title: 'The Hidden Problem with Evaluating LLMs: Why Ontology-Based Benchmarks Matter'
date: 2026-04-04
permalink: /posts/2026/04/ontology-based-llm-benchmarks/
tags:
  - Large Language Models
  - Benchmarking
  - Ontologies
  - Knowledge Graphs
  - Evaluation
  - Reasoning
---

Everyone agrees that Large Language Models should be evaluated rigorously. Dozens of benchmarks exist — MMLU, HellaSwag, BIG-Bench, GSM8K, and many more. Leaderboards are updated weekly. New models claim state-of-the-art performance almost daily.

And yet, something important is missing from most of these evaluations. A subtle but consequential problem that rarely gets discussed: **we are testing whether LLMs can reproduce human-written answers, not whether they can reason correctly.**

This distinction matters more than it might seem — especially in knowledge-intensive domains like biomedicine, clinical care, and drug discovery.

## What Standard Benchmarks Actually Measure

Most popular LLM benchmarks share a common structure: a question is posed, the model generates an answer, and the answer is compared against a gold standard written by a human.

This works reasonably well for factual recall. But it conflates two very different things:

- **Knowledge retrieval** — does the model know the fact?
- **Logical reasoning** — does the model reason correctly from what it knows?

A model that has memorised the right answer will score identically to one that derived it through sound reasoning. And a model that produces a plausible but logically inconsistent answer may still score well if it uses the right words.

In domains where reasoning correctness is critical — medicine, law, science — this is a serious gap.

## The Contamination Problem

There is a second, related issue: **benchmark contamination**. LLMs are trained on enormous text corpora scraped from the internet. Many popular benchmarks — or discussions of their answers — appear in that training data. A model may achieve high scores not because it can reason, but because it has seen the questions before.

This makes benchmark results increasingly difficult to interpret. Is GPT-4 better at medical reasoning, or did it simply encounter more medical exam questions during training? We often cannot tell.

Ontology-based evaluation offers a principled way out of this trap.

## What Ontology-Based Evaluation Offers

Ontologies are formal, machine-readable representations of knowledge in a domain. They define concepts, relationships, and logical constraints using languages like OWL (Web Ontology Language). Well-known examples include SNOMED CT in clinical medicine, Gene Ontology in biology, and ChEBI in chemistry.

Crucially, ontologies encode **logical structure** — not just facts. They express things like: "if A is a subclass of B, and B has property P, then A must also have property P." This makes them ideal for testing whether a model reasons consistently and correctly, rather than just retrieving memorised answers.

An ontology-based benchmark can:

- **Generate novel questions programmatically** from logical axioms — questions that are unlikely to appear verbatim in training data
- **Evaluate reasoning consistency** — checking not just whether an answer is correct, but whether it is consistent with other answers the model gives
- **Test across levels of abstraction** — from simple concept lookup to multi-hop inference across an ontology hierarchy
- **Detect hallucinations precisely** — by checking model outputs against a formal ground truth with clear semantics

## A Practical Example: Medical Reasoning

Consider a clinical ontology that encodes the following:

- `Metformin` is a `Biguanide`
- `Biguanides` are contraindicated in patients with `Renal Impairment`
- `Chronic Kidney Disease` is a subtype of `Renal Impairment`

A sound reasoning system should be able to infer that `Metformin` is contraindicated in patients with `Chronic Kidney Disease` — even if this specific fact was never stated explicitly.

Standard benchmarks would test this with a direct question. An ontology-based benchmark can instead test it as an **entailment**: given what the model knows about Metformin and Biguanides, does it consistently handle all subtypes of renal impairment? Does it give the same answer for `Acute Kidney Injury`? Does it contradict itself when asked the same question rephrased?

This reveals something far more informative than a single accuracy score.

## What We Found

In recent work from our research group, we developed a comprehensive framework for ontology-based evaluation of LLM reasoning capabilities. We systematically tested several state-of-the-art LLMs against biomedical ontologies, assessing not just correctness but **consistency, depth of reasoning, and robustness to rephrasing**.

The findings were instructive. Models that performed strongly on standard benchmarks showed surprising inconsistencies when tested against formal ontological constraints. They would correctly answer a direct question about a concept, then contradict themselves when the same question was posed at a different level of abstraction. They struggled particularly with **negation** and **disjointness** — logical constructs that ontologies express precisely but natural language handles ambiguously.

These are not corner cases. In clinical settings, reasoning about what a drug is *not* indicated for, or that two diagnoses are *mutually exclusive*, is as important as reasoning about what *is* the case.

## Implications for How We Build and Deploy LLMs

These findings have practical implications for anyone building AI systems for knowledge-intensive domains:

1. **Do not rely solely on leaderboard scores** when evaluating models for specialised applications. A model that tops MMLU may still reason poorly about your specific domain.

2. **Invest in domain ontologies** — not just as data assets, but as evaluation tools. If your domain has a well-maintained ontology (and in biomedicine, several excellent ones exist), it is a valuable resource for rigorous model assessment.

3. **Test consistency, not just correctness.** Ask the same underlying question in multiple ways, at multiple levels of abstraction. Inconsistency is often a more reliable signal of poor reasoning than outright wrong answers.

4. **Be cautious about benchmark saturation.** As models improve on existing benchmarks, the benchmarks stop being informative. Ontology-derived benchmarks can be continuously regenerated from updated knowledge bases, staying ahead of contamination.

## Conclusion

The field of LLM evaluation is maturing, but it still has a blind spot: most benchmarks measure what models know, not how well they reason. Ontology-based evaluation frameworks offer a principled, contamination-resistant, semantically grounded alternative — one that is particularly valuable in domains where logical consistency is not optional.

As LLMs are increasingly deployed in healthcare, drug discovery, and clinical decision support, getting evaluation right is not an academic exercise. It is a prerequisite for safe and trustworthy AI.

---

*Remzi Celebi is an Assistant Professor at the Department of Advanced Computing Sciences (DACS), Maastricht University. His research focuses on knowledge graphs, neuro-symbolic AI, and FAIR data for personalized health and drug discovery.*
