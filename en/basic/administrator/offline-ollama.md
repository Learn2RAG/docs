---
layout: default
title: Offline Ollama & Model Setup
nav_order: 2
permalink: /en/basic/administrator/offline-ollama/
parent: Administrator Documentation
---

# Setting Up Ollama and Models Offline

This guide walks you through deploying Ollama and your chosen Language Model on an air-gapped machine with no internet connection.

## Prerequisites
* An **online PC** (to download the initial files).
* A **USB drive** or network transfer method to move files to the offline target PC.

---

## Step-by-Step Procedure



1. Download the Ollama Linux binary directly:

    ```sh
       curl -L https://ollama.com/download/ollama-linux-amd64.tar.zst -o ollama-linux-amd64.tar.zst
       
    ```

2. Download the model weights:
    Navigate to a model repository like HuggingFace and download the .gguf file for your desired model (e.g., search for gemma-3-27b-it-GGUF). Save this file locally (e.g., gemma-3-27b.gguf).

3. Transfer the Files
      Copy both ollama-linux-amd64.tar.zst and the .gguf file to your portable storage drive.

4. Install Ollama (Offline PC)
   Move the files from your storage drive to the offline machine.
    * Extract the binary system-wide:
      (Note: Ensure your offline Linux distribution has zstd installed. If it does not, unpack and repack the archive as a standard .tar.gz on your online machine before transferring).
        ```
        sudo tar --zstd -xf ollama-linux-amd64.tar.zst -C /usr
      ```
    * Start the Ollama daemon:
      ```
        ollama serve &
      ```
5. Import the Model (Offline PC)
   Create a Modelfile:
   In the exact same directory where you placed your transferred .gguf file, create a text file named "Modelfile". Add a single line pointing to the model file:
   ``` 
      FROM ./[filename].gguf  
      
   ```
   
6. Build and register the model in Ollama:
   ```
   ollama create gemma3-offline -f ./Modelfile
    
   ```


API URL: http://localhost:11434

