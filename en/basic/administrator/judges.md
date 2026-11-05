---
layout: default
title: Judges
nav_order: 10
permalink: /de/basic/administrator/judges.html
parent: Administrator Documentation
---

## Judges

Learn2RAG is integrated with two judges based on [RAGAS](https://docs.ragas.io/en/stable/): the Context Relevance Judge and the Answer Relevance Judge.
These judges help improve the reliability of the pipeline by identifying irrelevant contexts or answers and triggering corrective actions when their relevance scores fall below a configurable threshold. 

### Context Relevance Judge

The Context Relevance Judge determines whether the retrieved contexts contain information relevant to the user's question. It operates after the retrieval and re-ranking stages, before the contexts are passed to the Large Language Model (LLM) for answer generation. This judge uses the RAGAS Context Relevance metric, which measures the relevance of the retrieved contexts using LLM-based evaluation.  
  
The judge assigns a relevance score and compares it against a threshold. If the score meets the threshold, the retrieved contexts are passed to the LLM for answer generation. Otherwise, the pipeline rewrites the query and performs the retrieval again to obtain more relevant contexts. This retry is limited to one attempt to prevent repeated retrieval operations.

### Answer Relevance Judge

The Answer Relevance Judge determines whether the generated answer adequately addresses the user's question. It operates after the LLM has generated a response and before the answer is returned to the user. This judge uses the RAGAS Answer Relevancy metric, which evaluates the semantic alignment between the generated answer
and the original question.  
  
The judge assigns a relevance score and compares it against a threshold. If the score meets the threshold, the generated answer is returned to the user. Otherwise, the pipeline attempts to generate a new answer using the retrieved contexts. This retry is also limited to one attempt to avoid repeated answer generation. 

### Configuration

Both judges can be enabled or disabled independently through the pipeline configuration. The judges also share a single configurable threshold to determine when a retry is triggered.  

By default, both judges are disabled and can be enabled when required.