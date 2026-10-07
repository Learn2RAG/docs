---
layout: default
title: Benutzerautorisierung
nav_order: 4
permalink: /de/basic/developer/userauth/
parent: Entwicklerdokumentation
---
# Neue Möglichkeiten zur Autorisierung hinzufügen
## Zu ändernde Dateien
- `learn2rag/userui/auth/SOMETHING.py` - Implementierung des Benutzer-Login-Flows hinzufügen
- `learn2rag/userui/auth/__init__.py::build_router` - `auth_routers` - die Implementierung dort einbinden, damit sie in der Benutzer-UI angezeigt wird
- `learn2rag/pipeline/authorization_SOMETHING.py` -- Implementierung der Online-Filterprüfung hinzufügen
- `learn2rag/pipeline/authorization.py::_create_authorization_filter` - Initialisierung der Filterprüfung hinzufügen
- `learn2rag/ui/templates/sources_add_SOMETHING.py` - Felder zum Konfigurieren der Datenquelle hinzufügen