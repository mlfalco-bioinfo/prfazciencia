# Imagem base do Ubuntu 22.04
FROM ubuntu:22.04

# Evita prompts interativos durante a instalação
ENV DEBIAN_FRONTEND=noninteractive

# Instala dependências essenciais para o sistema, compilação de software e Java
RUN apt-get update && apt-get install -y \
    sudo \
    git \
    curl \
    wget \
    unzip \
    gunzip \
    build-essential \
    default-jre \
    zlib1g-dev \
    libncurses5-dev \
    libbz2-dev \
    liblzma-dev \
    --no-install-recommends && \
    rm -rf /var/lib/apt/lists/*

# Cria o usuário 'vscode', define a senha (necessário para sudo) e o adiciona ao grupo sudo
RUN useradd -m -s /bin/bash vscode && \
    echo "vscode:vscode" | chpasswd && \
    usermod -aG sudo vscode

# Define para que o usuário 'vscode' não precise de senha para usar o sudo
RUN echo "vscode ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Define o usuário 'vscode' como padrão
USER vscode
WORKDIR /home/vscode
