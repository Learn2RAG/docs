---
layout: default
title: User authorization
nav_order: 4
permalink: /en/basic/developer/userauth/
parent: Developer Documentation
---
# Adding new ways for authorization
## Files to change
- `learn2rag/userui/auth/SOMETHING.py` - add implementation of user login flow
- `learn2rag/userui/auth/__init__.py::build_router` - `auth_routers` - include the implementation there for it to show up in user UI
- `learn2rag/pipeline/authorization_SOMETHING.py` -- add implementation of online filter check
- `learn2rag/pipeline/authorization.py::_create_authorization_filter` - add initialization of the filter check
- `learn2rag/ui/templates/sources_add_SOMETHING.py` - add fields for configuring data source
