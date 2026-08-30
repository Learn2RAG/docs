---
layout: default
title: Offline-Einrichtung von Ollama & Modellen
nav_order: 2
permalink: /de/basic/administrator/offline-ollama/
parent: Administrator-Dokumentation
---

# Offline-Einrichtung von Ollama und Modellen

Diese Anleitung führt Sie durch die Bereitstellung von Ollama und Ihrem gewählten Sprachmodell auf einem Air-Gapped-Rechner (ohne Internetverbindung).

## Voraussetzungen
* Ein **Online-PC** (zum Herunterladen der initialen Dateien).
* Ein **USB-Stick** oder eine Netzwerkübertragungsmethode, um die Dateien auf den Offline-Ziel-PC zu verschieben.

---

## Schritt-für-Schritt-Anleitung

1. Laden Sie die Ollama Linux-Binärdatei direkt herunter:

    ```sh
     curl -L https://ollama.com/download/ollama-linux-amd64.tar.zst -o ollama-linux-amd64.tar.zst
    ```

2. Modellgewichte herunterladen:
   Navigieren Sie zu einem Modell-Repository wie HuggingFace und laden Sie die .gguf-Datei für Ihr gewünschtes Modell herunter (z. B. nach gemma-3-27b-it-GGUF suchen). Speichern Sie diese Datei lokal (z. B. gemma-3-27b.gguf).

3. Dateien übertragen:
   Kopieren Sie sowohl `ollama-linux-amd64.tar.zst` als auch die `.gguf`-Datei auf Ihr tragbares Speichermedium.

4. Ollama installieren (Offline-PC):
   Verschieben Sie die Dateien von Ihrem Speichermedium auf den Offline-Rechner.
    * Entpacken Sie die Binärdatei systemweit:
      *(Hinweis: Stellen Sie sicher, dass auf Ihrer Offline-Linux-Distribution `zstd` installiert ist. Falls nicht, entpacken Sie das Archiv auf Ihrem Online-Rechner und packen es als standardmäßiges `.tar.gz` neu, bevor Sie es übertragen).*
      ```sh
      sudo tar --zstd -xf ollama-linux-amd64.tar.zst -C /usr
      ```
    * Starten Sie den Ollama-Daemon:
      ```sh
      ollama serve &
      ```

5. Modell importieren (Offline-PC):
   Erstellen Sie ein Modelfile:
   Erstellen Sie im exakt selben Verzeichnis, in dem Sie Ihre übertragene `.gguf`-Datei abgelegt haben, eine Textdatei namens `Modelfile`. Fügen Sie eine einzelne Zeile hinzu, die auf die Modelldatei verweist:
   ```text
   FROM ./[Dateiname].gguf
   ```
    Modell in Ollama erstellen und registrieren:
6. ```
    ollama create gemma3-offline -f ./Modelfile
   ```


   API-URL: http://localhost:11434

