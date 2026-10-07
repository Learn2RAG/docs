

---
layout: default
title: Optimization
nav_order: 10
permalink: /de/basic/administrator/optimization.html
parent: Administratorhandbuch
---

## Optimierung

Learn2RAG stellt einen Optimierungsprozess bereit, der automatisch eine geeignetere Konfiguration für die RAG-Pipeline ermittelt.

### Trainingsdaten

Die Optimierung erfordert eine Trainingsdatei, die Ihre Fragen und die zugehörigen erwarteten Antworten enthält.
Die Datei sollte im CSV-Format vorliegen, wobei die erste Zeile die Spaltenüberschriften enthält.
Erwartete Spalten: `question`, `answer`.
Wir stellen [ein Beispiel der Trainingsdatei](/static/sample_data/training_data_sample.csv) bereit.

### Funktionsweise

Der Optimierungsprozess nutzt [SMAC](https://github.com/automl/smac3), um die verfügbaren Konfigurationen durchzusuchen. Für jede ausgewählte Konfiguration führt Learn2RAG die Pipeline auf Ihren Trainingsdaten aus und bewertet die generierten Antworten.
Auf Grundlage dieser Ergebnisse setzt SMAC die Suche nach besseren Konfigurationen fort. Nach Abschluss der Optimierung wird die beste gefundene Konfiguration gespeichert und anschließend von der RAG-Pipeline verwendet.