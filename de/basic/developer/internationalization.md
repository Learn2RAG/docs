

---
layout: default
title: Internationalization
nav_order: 4
permalink: /en/basic/developer/internationalization/
parent: Entwicklerdokumentation
---
# Internationalisierung
## Überblick
Wir verwenden [gettext](https://www.gnu.org/software/gettext/) und die entsprechenden Python-Bibliotheken, um mehrere Sprachen für Schnittstellentexte zu unterstützen.
## Workflow
### Bearbeiten der englischen Texte
Englische Texte sind ein Teil des Quellcodes.
Sie können Werkzeuge wie `grep` verwenden, um den Text zu finden, den Sie im Quellcode bearbeiten müssen.
### Bearbeiten der deutschen Texte
- Führen Sie `./update-translations` aus.
- Bearbeiten Sie `learn2rag/ui/translations/de/LC_MESSAGES/messages.po`. Es gibt viele benutzerfreundliche Editoren für `.po`-Dateien, zum Beispiel [Poedit](https://poedit.net). Sie können es auch mit einem beliebigen Texteditor bearbeiten, müssen dabei jedoch das Metadatenformat beachten.
- Führen Sie `./update-translations` erneut aus.
- Übergeben Sie die Änderungen an den `.po`- und `.pot`-Dateien in das Git-Repository.