---
title: Data source with user authorization
permalink: /en/basic/administrator/userauth.html
---

User authorization is used to restrict which users are allowed to access which documents.
The import process still needs to be configured in a way that it can access all documents.

## OAuth
### Supported data sources
- Drupal

### Configuration
#### Determine Learn2RAG chat URL
OAuth provider needs to know the exact URL of our application.
Before starting any configuration, you need to know a full URL for the pipeline from the perspective of users, including the port (which you can choose according to your needs).

Example: if users can access Learn2RAG using `learn2rag.example.com` on port `9050` with TLS, the resulting URL would be `https://learn2rag.example.com:9050/`

#### Create OAuth consumer in your data source
- client ID: your choice
- client secret: your choice
- redirect URL: application URL combined with `auth/oauth/callback`, for example `https://learn2rag.example.com:9050/auth/oauth/callback`
- grant types: `authorization_code` and `refresh_token`
- scopes: for example, `authenticated` (adjusted to your setup)

#### Configure the data source in Learn2RAG
- User authorization: `OAuth`
- client ID: must be the same as in previous step
- client secret: must be the samep as in previous step
- authorize URL: the corresponding URL from your application
- access token URL: the corresponding URL from your application

For example, if your Drupal instance is available at `https://drupal.example.com/`:
- authorize URL: `https://drupal.example.com/oauth/authorize`
- access token URL: `https://drupal.example.com/oauth/token`

URLs can be left empty to use the default ones relative to the base URL of the data source.

#### Configure the pipeline in Learn2RAG
When creating a pipeline, use "more options" and put your chosen port (for example, `9050`) in "Ports - user interface".

After starting the pipeline, in the user interface there should be a button to initiate user log in with OAuth.
