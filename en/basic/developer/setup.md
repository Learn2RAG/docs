---
layout: default
title: Setting up the development environment
nav_order: 1
permalink: /en/basic/developer/setup/
parent: Developer Documentation
---
# Setting up the development environment
## Overview
The setup assumes using a Debian Linux system with the `bash` shell.
Other Linux distributions might require adapting these instructions.
## Requirements
### Before you start
```sh
sudo apt update
```

### pyenv
See also: https://github.com/pyenv/pyenv

```sh
git clone --branch v2.6.11 --depth 1 https://github.com/pyenv/pyenv.git ~/.pyenv
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init - bash)"' >> ~/.bashrc
source ~/.bashrc
```

### Python
```sh
sudo apt install make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev curl git libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev libzstd-dev
pyenv install 3.11.13
pyenv install 3.13.5
pyenv global 3.11.13
```

### Poetry
```sh
python3 -m pip install --user pipx
python3 -m pipx ensurepath
source ~/.bashrc
pipx install poetry
```

### node.js
```sh
wget https://nodejs.org/dist/v20.19.5/node-v20.19.5-linux-x64.tar.xz
tar -xf node-v20.19.5-linux-x64.tar.xz
echo "PATH=$PWD/node-v20.19.5-linux-x64/bin:\$PATH" >> ~/.bashrc
source ~/.bashrc
```

### Other packages
```sh
sudo apt install cmake
```

## Source code
```sh
git clone --recursive https://github.com/Learn2RAG/configurator
```

## Project dependencies and other components
```sh
cd configurator
./install
```

## Runtime dependencies
```sh
sudo apt install libgl1 libmagic1
```

## Dependencies for building the packages
### Rust
#### Debian 13
```sh
apt install rustup
```
#### Debian 12
```sh
wget -O ~/.local/bin/rustup-init https://static.rust-lang.org/rustup/dist/x86_64-unknown-linux-gnu/rustup-init
chmod +x ~/.local/bin/rustup-init
rustup-init
echo '. "$HOME/.cargo/env"' >> ~/.bashrc
source ~/.bashrc
```

### Cross
```sh
cargo install cross --git https://github.com/cross-rs/cross
```

### Docker
```sh
sudo apt install docker.io
sudo usermod -aG docker $USER
```
