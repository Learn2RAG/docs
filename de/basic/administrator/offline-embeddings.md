---
layout: default
title: Offline-Setup für Embedding-Modelle
nav_order: 3
permalink: /de/basic/Administratorhandbuch/offline-embeddings/
parent: Administrator-Dokumentation
---

# Einrichten von Embedding-Modellen im Offline-Betrieb

Diese Anleitung führt Sie durch die Bereitstellung von vorab zwischengespeicherten Hugging Face Embedding-Modellen auf einem isolierten (Air-Gapped) Rechner ohne Internetverbindung.

## Voraussetzungen
* Ein **Online-PC** (zum Herunterladen der anfänglichen Modellarchive).
* Ein **USB-Stick** oder eine Netzwerkübertragungsmethode, um Dateien auf den Offline-Ziel-PC zu verschieben.

---

## Schritt-für-Schritt-Anleitung

1. Modellarchive herunterladen:
   Laden Sie auf Ihrem Online-Rechner die benötigten, vorgefertigten Hugging Face Modell-Cache-Dateien von Hugging Face oder dem öffentlichen DICE-Speicherserver herunter:
   `https://files.dice-research.org/projects/Learn2RAG/datasets/offline_hf_cache/`

2. Dateien übertragen:
   Kopieren Sie die heruntergeladenen Archivdateien (`.tar.gz` oder `.zip`) auf Ihr tragbares Speichermedium und übertragen Sie diese auf den Offline-Ziel-PC.

3. Zielverzeichnis vorbereiten (Offline-PC):
   Stellen Sie sicher, dass das Hugging Face Hub-Cache-Verzeichnis für den Benutzer existiert, der Learn2RAG ausführt:
   ```sh
   mkdir -p ~/.cache/huggingface/hub
   ```
   
4. Modelle entpacken und platzieren:
   Entpacken Sie die Modellarchive direkt nach ~/.cache/huggingface/hub/ (oder /home//.cache/huggingface/hub/).

5. Verzeichnisstruktur überprüfen:
   Bestätigen Sie, dass Ihr Cache-Verzeichnis die erforderlichen Snapshot-Ordner in exakt der von Hugging Face erwarteten Struktur enthält:
```
~/.cache/huggingface/hub/
├─ models--BAAI--bge-m3/
│   └─ snapshots/<hash>/...
├─ models--roberta-large/
│   └─ snapshots/<hash>/...
└─ models--sentence-transformers--all-mpnet-base-v2/
    └─ snapshots/<hash>/...
```