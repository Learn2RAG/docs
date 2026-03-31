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

### Python and other tools
```sh
sudo apt install pipx
pipx ensurepath
source ~/.bashrc

pipx install uv
uv python install 3.11.13
uv python install 3.13.5

pipx install poetry
```

### Dependencies
```sh
sudo apt install make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev curl git libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev libzstd-dev
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
git clone --recursive --branch master https://github.com/Learn2RAG/configurator
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
rustup default stable
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
# might need to add ~/.cargo/bin to $PATH
```

### Docker
```sh
sudo apt install docker.io
sudo usermod -aG docker $USER
```
