---
layout: default
nav_order: 1
title: Administratorhandbuch
permalink: /de/basic/Administratorhandbuch
parent: Deutsch
---

## Videoübersicht
<video src="https://files.dice-research.org/projects/Learn2RAG/docs/de/basic/learn2rag-install-de.mp4" controls></video>

## Anforderungen

### Hardware
#### Platzbedarf
##### Linux
Downloadgröße
: 7 GB

Größe nach dem Entpacken
: 10 GB

Zusätzlicher Speicherbedarf für die Installation
: 10 GB

##### Windows
Downloadgröße
: 2,5 GB

Größe nach dem Entpacken
: 4 GB

Zusätzlicher Speicherbedarf für die Installation
: 4 GB

##### Zusätzlicher Speicherbedarf
Embedding-Modell
: 4,5 GB

LLM (Google Gemma 3 27b)
: 17 GB

Speicher für Datenbanken und temporäre Dateien
: entsprechend der Größe Ihrer Daten

### Linux
- 64-Bit (Kernel 3.2+, glibc 2.17+)
- Möglicherweise müssen Sie die folgenden Bibliotheken über den Paketmanager Ihrer Distribution installieren: `libgl1 libmagic1`. Auf einem Debian- oder Ubuntu-System können Sie dies mit `sudo apt install libgl1 libmagic1` tun.

### Windows
- 64-bit (Windows 10+, Windows Server 2016+)
- Möglicherweise müssen Sie [Microsoft Visual C++ Redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist) installieren.

**Fehlerbehebung: Pfadlänge zu lang**
Wenn der Fehler `Could not install packages due to an OSError: [WinError 206] Der Dateiname oder die Erweiterung ist zu lang` auftritt, müssen Sie die Unterstützung für lange Dateipfade in Windows aktivieren:

1. Drücken Sie `Win + R`, geben Sie `regedit` ein und drücken Sie **Enter**.
2. Navigieren Sie zu `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem`.
3. Suchen Sie den Wert `LongPathsEnabled` und machen Sie einen Doppelklick darauf. *(Falls nicht vorhanden: Rechtsklick in einen leeren Bereich, **Neu > DWORD-Wert (32-Bit)** wählen und `LongPathsEnabled` nennen)*.
4. Setzen Sie den **Wert** auf `1` und klicken Sie auf **OK**.

## Installation und Start
1. Laden Sie die Version für Ihre Plattform von <https://learn2rag.de/downloads> herunter.
2. Extrahieren Sie das Archiv. Sie müssen dieses Verzeichnis aufbewahren, um Learn2RAG auszuführen.
   ```sh
   unzip learn2rag-linux.zip
   cd learn2rag-linux