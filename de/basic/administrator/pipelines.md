---
title: Pipelines
permalink: /de/basic/administrator/pipelines.html
parent: Administratorhandbuch
layout: default
nav_order: 5
---

Jede Learn2RAG-Pipeline ist ein isoliertes Setup.

## Erweiterte Konfiguration
### Ports
Jede Pipeline muss einige Ports für die erforderlichen Dienste zuweisen.
Dies erfolgt automatisch beim Starten der Pipeline oder kann manuell festgelegt werden.

#### Benutzeroberfläche und RAG-Dienst
Dies ist ein Port für den Webdienst, der die Chat-Benutzeroberfläche und die OpenAI-kompatible API umfasst.
In den meisten Fällen jenseits eines grundlegenden lokalen Testsetups muss er manuell festgelegt werden.

#### Vektorspeicher
Dies ist ein interner Port, der für die Einrichtung der Datenbank erforderlich ist.