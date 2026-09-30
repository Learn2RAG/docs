

---
title: Datenquellen
permalink: /de/basic/administrator/data-sources.html
parent: Administratorhandbuch
---

## Dateisystem
Fügen Sie lokale Verzeichnisse (auf demselben PC oder Server, auf dem Learn2RAG läuft) hinzu.
Zum Beispiel: `/home/user/Documents`, `C:\Users\User\Documents`.

### Unterstützte Dateitypen
* **`.docx`**
* **`.pptx`**
* **`.xlsx`**
* **`.pdf`**
* **`.txt`**
* **`.csv`**
* **`.html`**
* **`.md`**
* **`.rtf`**
* **`.odt`**
* **`.epub`**

> Pandoc wird für einige Dateitypen benötigt. Falls es nicht vorhanden ist, wird der Benutzer informiert und das System versucht, es interaktiv zu installieren. Wenn Sie die Installationsparameter, wie den Installationsort, auswählen möchten, installieren Sie Pandoc bitte vorab.

## Webseiten
Fügen Sie URLs von Webseiten hinzu.
Zum Beispiel: `https://en.wikipedia.org/wiki/Berlin`. Client-seitig durch JavaScript erzeugte Inhalte werden nicht ausgeführt oder ausgewertet.

## Microsoft
Sie können eine SharePoint-Sammlung als Dokumentenquelle hinzufügen.

### Unterstützte Dateitypen
* **`.pptx`**
* **`.xlsx / .xls`**
* **`.pdf`**
* **`.txt`**
* **`.csv`**
* **`.html`**
* **`.md`**

## Drupal
Sie können Ihre Drupal-Website als Datenquelle hinzufügen.

### Unterstützter Inhalt
* Konfigurieren Sie beliebige Inhaltstypen wie ["article", "page", "blog", ...]
* Konfigurieren Sie beliebige Textfelder wie ["title", "field_body", "body"],