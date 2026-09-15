---
layout: default
title: Optimization
nav_order: 10
permalink: /de/basic/administrator/optimization.html
parent: Administrator Documentation
---

## Optimization

Learn2RAG provides an optimization process to automatically find a more suitable configuration for the RAG pipeline.

### Training data

The optimization requires a training file containing your questions and the corresponding expected answers.
The file should be in csv format, with first row containing column header.
Expected columns: `question`, `answer`.
We provide [an example of the training file](/static/sample_data/training_data_sample.csv).

### How it works

The optimization process uses [SMAC](https://github.com/automl/smac3) to search through the available configurations. For each selected configuration, Learn2RAG runs the pipeline on your training data and evaluates the generated answers.
Based on these results, SMAC continues searching for better configurations. After the optimization completes, the best configuration found is saved and subsequently used by the RAG pipeline.
