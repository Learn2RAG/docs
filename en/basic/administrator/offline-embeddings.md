---
layout: default
title: Offline Embedding Models Setup
nav_order: 3
permalink: /en/basic/administrator/offline-embeddings/
parent: Administrator Documentation
---

# Setting Up Embedding Models Offline

This guide walks you through deploying pre-cached Hugging Face embedding models on an air-gapped machine with no internet connection.

## Prerequisites
* An **online PC** (to download the initial model archives).
* A **USB drive** or network transfer method to move files to the offline target PC.

---

## Step-by-Step Procedure

1. Download the model archives:
   On your online machine, download the required pre-packaged Hugging Face model cache files from Hugging Face or  the public DICE storage server:
   `https://files.dice-research.org/projects/Learn2RAG/datasets/offline_hf_cache/`

2. Transfer the Files:
   Copy the downloaded archive files (`.tar.gz` or `.zip`) to your portable storage drive and move them to the offline target PC.

3. Prepare the Target Directory (Offline PC):
   Ensure the Hugging Face hub cache directory exists for the user running Learn2RAG:
   ```sh
   mkdir -p ~/.cache/huggingface/hub
   ```
   extract and Place the Models:
   Unpack the model archives directly into ~/.cache/huggingface/hub/ (or /home/<user>/.cache/huggingface/hub/).
   Verify Directory Structure:
   Confirm that your cache directory contains the required snapshot folders in the exact structure expected by Hugging Face:
   ```
   ~/.cache/huggingface/hub/
   ├─ models--BAAI--bge-m3/ 
   │   └─ snapshots/<hash>/...
   ├─ models--roberta-large/
   │   └─ snapshots/<hash>/...
   └─ models--sentence-transformers--all-mpnet-base-v2/
       └─ snapshots/<hash>/...
   ```

