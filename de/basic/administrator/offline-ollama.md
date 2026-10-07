---
layout: default
title: Offline-Einrichtung von Ollama & Modellen
nav_order: 2
permalink: /de/basic/administrator/offline-ollama/
parent: Administratorhandbuch
---

# Ollama und Modelle offline einrichten

Diese Anleitung führt Sie durch die Einrichtung von Ollama und Ihrem ausgewählten Sprachmodell auf einer isolierten (air-gapped) Maschine ohne Internetverbindung.

## Voraussetzungen
* Ein **Online-PC** (zum Herunterladen der anfänglichen Dateien).
* Ein **USB-Laufwerk** oder eine Methode zur Netzwerkübertragung, um die Dateien auf den Offline-Ziel-PC zu übertragen.

---

## Schritt-für-Schritt-Anleitung



1. Laden Sie die Ollama-Linux-Binärdatei direkt herunter:

    ```sh
       curl -L https://ollama.com/download/ollama-linux-amd64.tar.zst -o ollama-linux-amd64.tar.zst
       
    ```

2. Laden Sie die Modellgewichte herunter:
    Navigieren Sie zu einem Modell-Repository wie HuggingFace und laden Sie die .gguf-Datei für Ihr gewünschtes Modell herunter (z. B. Suchen Sie nach gemma-3-27b-it-GGUF). Speichern Sie diese Datei lokal (z. B. gemma-3-27b.gguf).

3. Dateien übertragen
      Kopieren Sie sowohl ollama-linux-amd64.tar.zst als auch die .gguf-Datei auf Ihr tragbares Speichermedium.

4. Ollama installieren (Offline-PC)
   Verschieben Sie die Dateien von Ihrem Speichermedium auf die Offline-Maschine.
    * Entpacken Sie die Binärdatei systemweit:
      (Hinweis: Stellen Sie sicher, dass in Ihrer Offline-Linux-Distribution zstd installiert ist. Wenn nicht, entpacken Sie das Archiv auf Ihrem Online-Rechner und packen Sie es als Standard-.tar.gz-Datei neu zusammen, bevor Sie es übertragen).
        ```
        sudo tar --zstd -xf ollama-linux-amd64.tar.zst -C /usr
      ```
    * Starten Sie den Ollama-Daemon:
      ```
        ollama serve &
      ```
5. Modell importieren (Offline-PC)
   Erstellen Sie eine Modelfile:
   Im exakt gleichen Verzeichnis, in dem Sie die übertragene .gguf-Datei abgelegt haben, erstellen Sie eine Textdatei mit dem Namen "Modelfile". Fügen Sie eine einzelne Zeile hinzu, die auf die Modelldatei verweist:
   ``` 
      FROM ./[filename].gguf  
      
   ```
   
6. Modell erstellen und in Ollama registrieren:
   ```
   ollama create gemma3-offline -f ./Modelfile
    
   ```


API-URL: http://localhost:11434