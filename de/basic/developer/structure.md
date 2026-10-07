---
layout: default
title: Projektstruktur
nav_order: 5
permalink: /de/basic/developer/structure/
parent: Entwicklerdokumentation
---

# Projektstruktur
## build-python
Ein Skript zum Bauen aller Python-Module.
## configurator
Ein Startskript für den Konfigurator.
## Distfiles
Eine Liste der Dateien, die im Paket enthalten sind.
## install
Ein Skript zum Herunterladen und Installieren der Abhängigkeiten aller Komponenten.
## learn2rag
Python-Paket für den Top-Level-Konfigurator.
### learn2rag/compose
Klassen und Funktionen zur Verwaltung von Unterprozessen.
### learn2rag/data
Klassen und Funktionen zur Verwaltung der Datenspeicherung.
### learn2rag/ui
Flask-Webanwendung des Hauptkonfigurators und die relevanten Dateien (Vorlagen, Übersetzungen).
## open-webui-pipelines
Open WebUI-Pipeline, die unsere Pipeline mit Open WebUI verbindet.
## package-*
Skripte zum Erstellen eines Pakets (Installationsprogramm).
## pyapp
Subrepositorium mit einem Drittanbieter-Tool zum Erstellen von Paketen.
## qdrant
Konfigurationsdateien für Qdrant.
## services
### services/basic-pipeline
Erstparty-Komponente.
### services/importer
Erstparty-Komponente.
### services/open-webui
Drittanbieter-Komponente.
### services/open-webui-pipelines
Drittanbieter-Komponente.
### services/start-*
Startskripte für andere Komponenten, die in der Paketversion durch Binärdateien ersetzt werden.
## start*
Startskripte für Entwicklungs- und Paketversionen.