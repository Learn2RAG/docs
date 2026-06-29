---
title: Data Sources
permalink: /en/basic/administrator/data-sources.html
---

## File System
Add local (on the same PC or server where Learn2RAG is running) directories.
For example: `/home/user/Documents`, `C:\Users\User\Documents`.

### Supported File Types
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

> Pandoc is required for some file types - if not present user is informed and system will try to install interactivly. If you want to chooe the installation parameters such as installation location, please install beforehand.

## Web Pages
Add URLs of web pages.
For example: `https://en.wikipedia.org/wiki/Berlin`. Client-side Javascript generated content is not executed or parsed.

## Microsoft
You can add a Sharepoint-Collecation as document source

### Supported File Types
* **`.pptx`**
* **`.xlsx / .xls`**
* **`.pdf`**
* **`.txt`**
* **`.csv`**
* **`.html`**
* **`.md`**

## Drupal
You can add your Drupal site as data source.

### Supported Content
* configure any content type such as ["article", "page", "blog", ...]
* configure any text field such as ["title", "field_body", "body"], 

