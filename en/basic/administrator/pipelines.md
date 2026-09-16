---
title: Pipelines
permalink: /en/basic/administrator/pipelines.html
parent: Administrator Documentation
---

Each Learn2RAG pipeline is an isolated setup.

## Advanced configuration
### Ports
Each pipeline would need to assign some ports for the required services.
This is done automatically when the pipeline is started, or can be specified manually.

#### User interface and RAG service
This is a port for the web service which includes the chat user interface and OpenAI-compatible API.
It needs to be set manually in most cases beyond a basic local testing setup.

#### Vector store
This is a internal port which is required to set up the database.
