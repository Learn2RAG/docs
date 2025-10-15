# Administrator documentation
## Requirements
### Linux
- 64-bit (kernel 3.2+, glibc 2.17+)
- You might need to install the following libraries from your distribution's package manager: `libgl1 libmagic1`. On a Debian or Ubuntu system, you can do that using `sudo apt install libgl1 libmagic1`.

### Windows
- 64-bit (Windows 10+, Windows Server 2016+)

## Obtaining, installation and starting
Download the release for your platform at <https://learn2rag.de/download>.
Extract the archive.
Run the file named `start`.
On the first run, Python environment and dependencies would be prepared, so it can take some time.

## Configuration
### First run wizard
On a first run before you created any configurations, a first run wizard is displayed which can be used to create a minimally working configuration.
You can follow the steps to set up a basic example configuration.

### Language models
#### Downloadable language models
Learn2RAG can download and deploy a language model.
That is done with Ollama which is automatically started.
An overview of available models: <https://ollama.com/library>.

##### Suggested language models
A short list of suggested language models to download is provided for a quick start.

#### External language models
An external (local or remote) language model can be used if it's available with OpenAI or Ollama compatible API.
You would need an API URL and (if required) an access token.

##### OpenAI's ChatGPT
API type
: ChatOpenAI

API URL
: (leave empty)

Access token
: `<your token>`

Language model
: `gpt-4o` or other

### Data sources
In this section the data sources are only configured.
They are actually scanned or retrieved on a later stage, after a pipeline is configured and the import task is run.

#### Files
Add local (on the same PC or server where Learn2RAG is running) directories.
For example: `/home/user/Documents`, `C:\Users\User\Documents`.

#### Web pages
Add URLs of web pages.
For example: `https://en.wikipedia.org/wiki/Berlin`.

### Pipelines
#### Minimal configuration
To create a pipeline, you need to specify the storage directory where the system would save all related data, and choose which configured language models and data sources should be used.

#### Optional configuration
##### Ports
You can specify which ports should pipeline components use.
If skipped, the system would try to find an available port automatically.

##### Importing data
You can set or unset an option to run the data import as soon as you configure the pipeline.

### Interface language
Learn2RAG includes English and German interface localization.
The localization is chosen according to your web browser's settings.
Refer to your web browser's documentation for the details.

## Usage
After at least one language model, data source and pipeline are configured, you can start tasks related to the pipeline.

### Importing data
Import task would process all selected data sources.
After starting, you would need to wait until it is done.

### Using the system
Pipeline task would start the necessary components.
After starting, use "Open" button to open the user interface.

## Updating
Run the file named `uninstall` before or after extracting a new version of the system.

## Uninstallation
Run the file named `uninstall`.
That would remove automatically created application files, but leave your configuration data and downloaded models in place.

## Data storage locations
### Linux
`$XDG_DATA_HOME/pyapp/` (`~/.local/share/pyapp/`)
: Application data

`$XDG_DATA_HOME/Learn2RAG/` (`~/.local/share/Learn2RAG/`)
: User data

### Windows
`%LOCALAPPDATA%\pyapp\data\`
: Application data

`%LOCALAPPDATA%\Learn2RAG\`
: User data

## Advanced configuration
You can create `config.yml` file next to the `start` file.

An example with all supported options:
```yml
flask:
  # Application data path
  instance_path: '/data/learn2rag'
SUGGESTED_MODELS:
  local-chat:
    label: Local LLM configuration
    description: Put more information there.
    config:
      api: ChatOpenAI
      url: https://example.com/api
      model: gemma-3-27b-it
      token: xxx
```
