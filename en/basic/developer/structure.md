# Project structure
## build-python
A script to build all Python modules.
## configurator
A start script for the configurator.
## Distfiles
A list of files to be included in the package.
## install
A script to download and install dependencies of all components.
## learn2rag
Top-level configurator Python package.
### learn2rag/compose
Classes and functions handling subprocess management.
### learn2rag/data
Classes and functions handling data storage.
### learn2rag/ui
Main configurator Flask web application and the relevant files (templates, translations).
## open-webui-pipelines
Open WebUI pipeline which connects our pipeline to Open WebUI.
## package-*
Scripts which build a package (installer).
## pyapp
Subrepository with a third-party tool to build packages.
## qdrant
Qdrant configuration files.
## services
### services/basic-pipeline
First-party component.
### services/importer
First-party component.
### services/open-webui
Third-party component.
### services/open-webui-pipelines
Third-party component.
### services/start-*
Launcher scripts for other components which are replaced by binaries in the packaged version.
## start*
Start scripts for development and packaged versions.
