---
layout: default
title: Einrichten der Entwicklungsumgebung
nav_order: 1
permalink: /de/basic/developer/setup/
parent: Entwicklerdokumentation
---
# Entwicklungsumgebung einrichten
## Übersicht
Die Einrichtung setzt die Verwendung eines Debian-Linux-Systems mit der `bash`-Shell voraus.
Bei anderen Linux-Distributionen müssen diese Anweisungen ggf. angepasst werden.
## Voraussetzungen
### Vor der Installation
```sh
sudo apt update
```

### Python und weitere Werkzeuge
```sh
sudo apt install pipx
pipx ensurepath
source ~/.bashrc

pipx install uv
uv python install 3.13.5
```

### Abhängigkeiten
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

### Weitere Pakete
```sh
sudo apt install cmake
```

## Quellcode
```sh
git clone --recursive --branch master https://github.com/Learn2RAG/configurator
```

## Projektabhängigkeiten und weitere Komponenten
```sh
cd configurator
./install
```

## Laufzeitabhängigkeiten
```sh
sudo apt install libgl1 libmagic1
```

## Abhängigkeiten für das Erstellen der Pakete
In der Entwicklungsumgebung nicht erforderlich.
### Rust
#### Debian 13
```sh
sudo apt install rustup
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