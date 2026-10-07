---
title: Benutzerautorisierung
permalink: /de/basic/administrator/userauth.html
parent: Administratorhandbuch
layout: default
nav_order: 15
---

Benutzerautorisierung wird verwendet, um zu begrenzen, welche Benutzer auf welche Dokumente zugreifen dürfen.
Der Importprozess muss weiterhin so konfiguriert sein, dass er auf alle Dokumente zugreifen kann.

## OAuth
### Unterstützte Datenquellen
- Drupal

### Konfiguration
#### Bestimmen der Learn2RAG-Chat-URL
Der OAuth-Anbieter muss die genaue URL unserer Anwendung kennen.
Bevor Sie mit der Konfiguration beginnen, müssen Sie eine vollständige URL für die Pipeline aus der Perspektive der Benutzer kennen, einschließlich des Ports (den Sie nach Bedarf wählen können).

Beispiel: Wenn Benutzer Learn2RAG über `learn2rag.example.com` am Port `9050` mit TLS aufrufen können, lautet die resultierende URL `https://learn2rag.example.com:9050/`

#### OAuth-Consumer in Ihrer Datenquelle erstellen
- Client-ID: Ihre Wahl
- Client-Secret: Ihre Wahl
- Weiterleitung-URL: Anwendungs-URL kombiniert mit `auth/oauth/callback`, beispielsweise `https://learn2rag.example.com:9050/auth/oauth/callback`
- Grant-Typen: `authorization_code` und `refresh_token`
- Scopes: beispielsweise `authenticated` (angepasst an Ihr Setup)

#### Datenquelle in Learn2RAG konfigurieren
- Benutzerautorisierung: `OAuth`
- Client-ID: muss mit dem Wert aus dem vorherigen Schritt übereinstimmen
- Client-Secret: muss mit dem Wert aus dem vorherigen Schritt übereinstimmen
- Autorisierungs-URL: die zugehörige URL aus Ihrer Anwendung
- Access-Token-URL: die zugehörige URL aus Ihrer Anwendung

Beispielsweise, wenn Ihre Drupal-Instanz unter `https://drupal.example.com/` verfügbar ist:
- Autorisierungs-URL: `https://drupal.example.com/oauth/authorize`
- Access-Token-URL: `https://drupal.example.com/oauth/token`

Die URLs können leer gelassen werden, um die Standard-URLs relativ zur Basis-URL der Datenquelle zu verwenden.

#### Pipeline in Learn2RAG konfigurieren
Wenn Sie eine Pipeline erstellen, verwenden Sie "Weitere Optionen" und geben Sie Ihren gewählten Port (beispielsweise `9050`) unter "Ports - Benutzeroberfläche" ein.

Nach dem Starten der Pipeline sollte es in der Benutzeroberfläche eine Schaltfläche geben, mit der die Benutzeranmeldung über OAuth gestartet wird.