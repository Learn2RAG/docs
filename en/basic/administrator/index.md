---
layout: default
title: Administrator Documentation
nav_order: 1
permalink: /en/basic/administrator/
parent: English
has_children: true
---

## Requirements
### Hardware
#### Disk space
##### Linux
Download size
: 7 GB

Unarchived size
: 10 GB

Additional space for installation
: 10 GB

##### Windows
Download size
: 2.5 GB

Unarchived size
: 4 GB

Additional space for installation
: 4 GB

##### Additional space
Embedding model
: 4.5 GB

LLM (Google Gemma 3 27b)
: 17 GB

Storage for databases and temporary files
: according to the size of your data

### Linux
- 64-bit (kernel 3.2+, glibc 2.17+)
- You might need to install the following libraries from your distribution's package manager: `libgl1 libmagic1`. On a Debian or Ubuntu system, you can do that using `sudo apt install libgl1 libmagic1`.

### Windows
- 64-bit (Windows 10+, Windows Server 2016+)
- You might need to install https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist
  
**Troubleshooting: Path Length Error**
  If you encounter `Could not install packages due to an OSError: [WinError 206] The filename or extension is too long` (or `Der Dateiname oder die Erweiterung ist zu lang`), you need to enable long path support in Windows:

1. Press `Win + R`, type `regedit`, and press **Enter**.
2. Navigate to `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem`.
3. Find the `LongPathsEnabled` value and double-click it. *(If it doesn't exist: right-click an empty space, select **New > DWORD (32-bit) Value**, and name it `LongPathsEnabled`)*.
4. Change the **Value data** to `1` and click **OK**.

## Obtaining, installation and starting
Download the release for your platform at <https://learn2rag.de/downloads>.
Extract the archive.
You will need to keep this directory to run Learn2RAG.
```sh
unzip learn2rag-linux.zip
cd learn2rag-linux
```

Run the file named `start` either with a right mouse click and "Execute" or in a terminal.
```sh
./start
```

On the first run, Python environment and dependencies would be prepared, so it can take some time.
Expected first start time:
| Powerful server | 10 min |

## Configuration
### First run wizard
On a first run before you created any configurations, a first run wizard is displayed which can be used to create a minimally working configuration.
You can follow the steps to set up a basic example configuration.

### Language models
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

#### Downloadable language models
Learn2RAG can download and deploy a language model.
That is done with Ollama which is automatically started.
An overview of available models: <https://ollama.com/library>.

##### Air-gapped / Offline Environments
If your deployment machine has no internet access, you cannot download models via the built-in wizard. You must manually transfer Ollama and the model files. See the [Offline Ollama Setup Guide](offline-ollama.md) for step-by-step instructions.

##### Suggested language models
A short list of suggested language models to download is provided for a quick start.

### Data sources
In this section the data sources are only configured.
They are actually scanned or retrieved on a later stage, after a pipeline is configured and the import task is run.

| Data source | Supported | User Rights Supported |
|-------------|:---------:|:---------------------:|
| File system |    Yes    |           No          |
| Webpages    |    Yes    |           No          |
| Microsoft   |    Yes    |           No          |
| Drupal      |    Yes    |          Yes          |

More details about the supported data sources can be found [here](data-sources.md)

### Pipelines
#### Minimal configuration
To create a pipeline, you need to specify the storage directory where the system would save all related data, and choose which configured language models and data sources should be used.

> **Note:** By default, the pipeline storage path is located in the user data directory of the user running Learn2RAG (see [Data storage locations](#Data-storage-locations)). However, any accessible path on your system can be used.

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

> **Note:** Importing a large volume of data can take a significant amount of time.

### Using the system
Pipeline task would start the necessary components.
After starting, use "Open" button to open the user interface.

## Updating
Run the file named `uninstall` before or after extracting a new version of the system.

## Uninstallation
To uninstall Learn2RAG, you can either run the main uninstall script or target specific components using the dedicated scripts.

### Interactive Uninstall

Run the file named uninstall (Linux) or uninstall.bat (Windows).
This removes all application runtimes and dependencies, then prompts whether you also want to delete your personal user data.

### Selective Uninstall
If you prefer running non-interactive or targeted steps:
    
-  remove-learn2rag-data: Removes only the application binaries, runtime environments, and Open-WebUI pipelines. Your configurations, databases, chats, and models remain untouched.
-  remove-user-data: Permanently deletes your personal configurations, vector stores, and local databases (asks for confirmation unless invoked with -y).

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
UI:
  # Make administration interface available for others on any network (or specify yours)
  host: '0.0.0.0'
  port: 9000
SIMPLE_AUTH:
  # Credentials for the administrator interface
  username: admin
  password: 123
CHAT:
  # Make chat interface available for others on any network (or specify yours)
  host: '0.0.0.0'
  # Credentials for the user interface
  username: user
  password: 456
TLS:
  KEYFILE: '/absolute/path/key.pem'
  CERTFILE: '/absolute/path/fullchain.pem'
logging:
  # Display and save detailed debug logs
  debug: true
# Ports which would be preferred by default for additional services
PREFERRED_PORTS:
  - 5001
  - 5002
  - 5003
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

## Troubleshooting
### Remove application and user data storage
<#data-storage-locations>
