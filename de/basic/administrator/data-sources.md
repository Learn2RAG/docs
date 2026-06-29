---
title: Datenquellen
permalink: /de/basic/administrator/data-sources.html
---

## Dateisystem

Fügen Sie lokale Verzeichnisse (auf demselben PC oder Server, auf dem Learn2RAG ausgeführt wird) hinzu.
Zum Beispiel: `/home/user/Documents`, oder `C:\Users\User\Documents`.

![configurator file source](/static/images/config-add-file-source.png)

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

> Für einige Dateitypen würde die Bibliothek Pandoc benötigt - wenn diese nicht auf dem System installiert ist, wird eine interaktive Installation angestoßen. Für eine nutzerspezifische Installation wird empfohlen, die Bibliothek vorab zu installieren.
 
## Webseiten

Sie können auch Webseiten als Datenquellen hinzufügen. Zum Beispiel: `https://en.wikipedia.org/wiki/Berlin`. Das Auslesen ist auf die HTML-Inhalte begrenzt, dynamisch generierter Seiteninhalt (z.B. Client-seitiges Javascript) wird nicht ausgewertet.

![configurator file source](/static/images/config-add-web-source.png)

## Microsoft
Sie können Daten aus einer Sharepoint Sammlung hinzufügen.

### Unterstützte Dateitypen
* **`.pptx`**
* **`.xlsx / .xls`**
* **`.pdf`**
* **`.txt`**
* **`.csv`**
* **`.html`**
* **`.md`**

## Drupal
Sie können Daten aus Ihrer Drupal Webseite hinzufügen.

### Unterstützter Inhalt
* alle Content - Typen konfigurierbar wie z.B. ["article", "page", "blog", ...]
* alle Text - Typen konfigurierbar wie z.B. ["title", "field_body", "body"], 

