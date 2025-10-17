# Internationalization
## Overview
We use [gettext](https://www.gnu.org/software/gettext/) and the corresponding Python libraries to support multiple languages for interface texts.
## Workflow
### Editing the English texts
English texts are a part of the source code.
You can use tools like `grep` to find the text you need to edit in the source.
### Editing the German texts
- Run `./update-translations`.
- Edit `learn2rag/ui/translations/de/LC_MESSAGES/messages.po`. There are many user-friendly editors for `.po` files, for example [Poedit](https://poedit.net). It can be also be edited with any text editor however you would need to be aware of the metadata format.
- Run `./update-translations` again.
- Commit changes to `.po` and `.pot` files to the git repository.
