# Setting up the development environment
## Overview
The setup assumes using a Debian Linux system; for other distributions, make changes accordingly.
## Requirements
### Debian packages
`apt install autoconf automake ca-certificates clang cmake dpkg-dev g++ gcc git golang-go libc6-dev libgl1 libmagic1 libssl-dev make python3 python3-dev python3-pip python3-venv rsync unzip wget`
### Node.js
Version 20 is required.
### Pyenv
https://github.com/pyenv/pyenv
After installing:
```sh
pyenv install 3.11.13
pyenv install 3.13.5
pyenv global 3.13.5
```
### Poetry
`pipx install --force poetry`
### Rust
#### Debian 13
`apt install rustup`
#### Debian 12
```sh
wget -O ~/.local/bin/rustup-init https://static.rust-lang.org/rustup/dist/x86_64-unknown-linux-gnu/rustup-init
chmod +x ~/.local/bin/rustup-init
rustup-init
```
## Source
```
git clone --recursive https://github.com/Learn2RAG/configurator
cd configurator
```
## Download and install dependencies and components
`./install`
