---
title: "Is Knowledge Retrieved, or Accumulated?"
subtitle: "The Limits of RAG Exposed by Karpathy's 'LLM Wiki' — and What Lies Beyond"
author: "Dennis Kim"
affiliation: "CEO, Betalabs Inc. · Publisher, Web3Paper"
date: 2026-04-20
tags: [AI, LLM, RAG, Knowledge Management, Karpathy, Web3Paper]
lang: en
---

# 【 TECH COLUMN 】

# Is Knowledge Retrieved, or Accumulated?
## The Limits of RAG Exposed by Karpathy's 'LLM Wiki' — and What Lies Beyond

**Dennis Kim**

---

> *"We need to move LLMs beyond mere retrieval, toward reading, understanding, and organizing knowledge on their own."*
> — Andrej Karpathy

In late 2025, a single remark from Andrej Karpathy — founding member of OpenAI and former Director of AI at Tesla — sent a ripple through the AI engineering community. He likened the Retrieval-Augmented Generation (RAG) architecture that most AI applications now depend on to *"handing a fresh note to an amnesiac every time they need to remember something,"* and proposed an alternative he called the **LLM Wiki**. Rather than consuming knowledge by searching for it again and again, the idea is to read it once, structure it, *compile* it, and accumulate it.

What sounds like a simple proposal is, in fact, a fundamental challenge to the information-processing paradigm the AI industry has taken for granted over the past two years. To understand why it resonated so strongly — and why it has simultaneously drawn sharp criticism — we must first look at the structural limits on which today's standard, RAG, is built.

## I. RAG's "Amnesia" — Why Knowledge Is Once Again the Problem

RAG was an elegant compromise. An LLM's context window is finite, and fine-tuning the model for every use case is too costly and too slow. So we stored information in external knowledge bases and, at query time, fetched the relevant chunks and stuffed them into the prompt. Vector embeddings, hybrid search, rerankers — for three years, the AI infrastructure industry poured vast resources into refining this pipeline.

But Karpathy's diagnosis cuts deep. This approach resembles *matching* rather than *understanding*. With every query, the model receives information fragments it is seeing for the first time, and assembles an answer on the fly. Nothing is learned between yesterday's answer and today's. A contradiction noticed in one turn is not recorded for the next. Even on the 1,000th retrieval of the same document, the model must re-read it with the same effort as on the 999th. No human relates to knowledge this way.

This is precisely where the concept of **"compilation of knowledge"** enters. Rather than interpreting source code every time, we compile it once — and subsequent execution becomes fast, consistent, and optimized. The LLM Wiki mirrors this logic. Instead of retrieving raw documents piecemeal for every query, an LLM agent reads them, summarizes them, cross-links them, flags contradictions, and stores the result in a human-readable form such as Markdown. When a question then arrives, the model can focus its reasoning on this *curated* knowledge rather than on raw fragments.

## II. What Is Genuinely New Here

### 1) The Compounding Effect of Knowledge

What most clearly separates the LLM Wiki from RAG is how each treats *time*. A RAG knowledge base grows linearly: 1,000 documents means 1,000 independent fragments. An LLM Wiki, by contrast, links each new piece of information to existing pages, flags contradictions as they arise, and consolidates duplicates. A living encyclopedia that updates itself every time a new book is read — that is the picture Karpathy paints.

The gap widens exponentially over time. As the knowledge base grows, RAG is increasingly plagued by noise; an LLM Wiki, in theory, becomes increasingly refined. This is what is meant by the **compounding effect**.

### 2) A Redistribution of Human Cognitive Load

Interestingly, the core value Karpathy emphasizes is not *performance* but *division of labor*. The essence of the idea, he argues, is that the LLM handles the tedious **bookkeeping** on behalf of the human. Deciding where to source information, what to explore, what questions to ask — these higher-order judgments remain with the human. The repetitive, low-level work — summarizing, cross-referencing, naming files, organizing categories — is offloaded to the agent.

This distinction marks a significant pivot in the "tool theory" of the generative-AI era. What we ought to expect from an LLM is not *that it does our thinking for us*, but rather *that it keeps the infrastructure for thinking in good order*.

### 3) Restoring Transparency and Ownership

A vector database is, by nature, a black box. Very few engineers can intuitively audit what is stored in a 3,072-dimensional embedding space, or why one fragment is retrieved while another is missed. An LLM Wiki, by contrast, is nothing more than a collection of Markdown text files. The user can open them at any time, correct errors, and reorganize structure. Direct integration with established note-taking ecosystems such as Obsidian is significant in the same vein. This is not merely a matter of convenience — it is a question of returning *control over knowledge* from the AI system back to the human.

## III. The Shadow — Four Reefs Hidden Behind the Innovation

### 1) The Accumulation and Amplification of Error — The Most Fatal Achilles' Heel

The greatest risk of the LLM Wiki concept is that the model's own imperfections are *structurally amplified*. RAG refers back to the source on every query; if a hallucination occurs, there is a chance to correct it on the next turn. The LLM Wiki is different. If, during initial compilation, the model misses a subtle nuance, leans on a particular bias, or wrongly resolves a contradiction between two documents, that error is inscribed into the wiki as *fact*.

The problem does not end there. As subsequent documents are added and begin to cross-reference the contaminated page, the error no longer stays in one place — it propagates across the entire network. A *self-reinforcing falsity*. This is a pattern seen even in human-edited systems like Wikipedia, but in an LLM-driven system, it can snowball without a verifier. It is essentially the same class of risk as the "cross-generational model collapse" recently reported by Anthropic and several other research labs.

### 2) The Wall of Scalability

The LLM Wiki approach is ideal for small, focused knowledge bases. Once the document count climbs into the thousands, however, the economics begin to collapse. Each new document requires the agent to read the whole wiki, find related pages, and verify consistency. Real-world benchmarks indicate that **accuracy remains solid below 500 notes but degrades sharply past 1,000**. Human Wikipedia editors can manage seven million articles precisely because each handles an extremely narrow domain. LLM agents do not yet have this kind of division of labor.

### 3) Token Economics — "Technology That Warms the Planet"

Compilation is not free. Every time new material is added, the full wiki must be read, analyzed, and updated — consuming enormous quantities of tokens. As the wiki grows, the cost per update rises not linearly but *super-linearly*. For a large organization adopting this approach, API-call costs alone can easily run into tens of thousands of dollars per month. A reminder that RAG was never merely a *technical* compromise — it was an economic one as well.

### 4) The Bias of LLM-Designed Knowledge Structures

A subtler problem is that the very *skeleton* of the knowledge is authored by the LLM. What to name a page, which concept to nest under which, what to cross-reference — every one of these decisions reflects the worldview embedded in the model's training data. A Korean-history wiki structured by a model trained primarily on English-language sources will be carved up in ways a Korean editor would never have produced. Outsourcing not only the *content* of knowledge but its *map* — the implications run deeper than they first appear.

## IV. The Counter-Argument — Isn't "On-Demand RAG" Enough?

The most compelling critique from skeptics is *over-engineering*. They ask: must everything really be compiled in advance? Isn't it enough to let a well-designed RAG pipeline fetch the source material at query time? Now that the latest LLMs have crossed the one-million-token context window, hasn't the traditional need to "pre-organize knowledge" itself grown weaker?

This objection deserves to be taken seriously. Karpathy himself has never claimed the LLM Wiki is a universal answer. What he has surfaced, more precisely, is the fact that *knowledge management* and *information retrieval* were always different problems. RAG is optimized for the latter. But for researchers, authors, lawyers, and medical professionals who work with the same body of knowledge for years, the former — *accumulating knowledge* — remains an essential requirement.

## V. Paths Forward — The Middle Ground of "Semi-Automated Curation"

Practical directions for realizing the LLM Wiki's potential while containing its risks are already emerging on several fronts.

### ① Human-in-the-Loop

Require human approval before the agent makes significant changes to the wiki. This is the most reliable brake against error amplification. It trades full automation for *trustworthiness* — and is the compromise most real-world deployments eventually settle on.

### ② Hybrid Architecture

Treat the wiki and RAG not as exclusive alternatives but as complementary layers. Compile stable, established knowledge into the wiki; for domains where freshness matters or facts must be verified, fall back on RAG to re-reference the original source. This dual structure mirrors the human cognitive architecture of "slow brain" and "fast brain."

### ③ Forgetting by Design

Abandon the ambition to preserve all knowledge forever. Human memory strengthens, weakens, consolidates, and forgets. Without this cycle, the inertia of stale information blocks new insight. Mechanisms that naturally decay low-access pages or push them into archives are essential for a *living* knowledge system.

### ④ Provenance Tracking and Version Control

Git-based version control and metadata annotation are not optional. Every claim in the wiki must be traceable back to the specific passage in the source document from which it derives, and every change must be auditable. Without this, the LLM Wiki degenerates into an unsupervised black box.

## VI. Coda — From Retrieved Knowledge to Accumulated Knowledge

Karpathy's LLM Wiki proposal is not a finished architecture. It is a question. For the past few years, we have pushed AI in the direction of *searching more and generating more*. The result has been astonishing performance — but also a knowledge landscape that is increasingly fragmented and disposable. Can we really call a system that starts from scratch in every conversation *intelligent*?

**The LLM Wiki is one response to that question.** It is an attempt to give AI back its capacity to *remember* — and, at the same time, to return to humans their *ownership* over knowledge. It is, to be sure, unlikely to be ported into large-scale commercial systems in its current form. The three reefs — error accumulation, cost, and bias — are real risks.

Yet over the next one to two years, this idea will most likely propagate not as a *fully automated wiki* but as a *semi-automated knowledge-curation tool*. Personal second brains, enterprise internal knowledge hubs, shared knowledge bases for research groups — the LLM Wiki approach will first take root in small, high-value, verifiable domains.

What is clear is this: **the point is not that RAG was wrong, but that RAG alone is not enough.** And that knowledge, in its truest sense, was never something merely *retrieved*, but a living process of accumulation, reorganization, and sometimes forgetting — that is what Karpathy has reminded us of.

---

**Dennis Kim**
CEO, Betalabs Inc. · Publisher, Web3Paper
✉️ gameworker@gmail.com · 🐙 github.com/gameworkerkim
