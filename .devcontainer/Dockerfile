# Imagem base do Ubuntu 22.04
FROM ubuntu:22.04

# Evita prompts interativos durante a instalação de pacotes
ENV DEBIAN_FRONTEND=noninteractive

# 1. Instala as dependências essenciais do sistema
# Inclui Java (para Trimmomatic), FastQC, e outras ferramentas úteis
RUN apt-get update && apt-get install -y \
    sudo \
    git \
    wget \
    unzip \
    default-jre \
    fastqc \
    --no-install-recommends && \
    rm -rf /var/lib/apt/lists/*

# 2. Instala o Trimmomatic manualmente
RUN wget http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-0.39.zip -O /tmp/Trimmomatic.zip && \
    unzip /tmp/Trimmomatic.zip -d /opt/ && \
    rm /tmp/Trimmomatic.zip && \
    # Cria um link simbólico para que o Trimmomatic possa ser chamado de qualquer lugar
    ln -s /opt/Trimmomatic-0.39/trimmomatic-0.39.jar /usr/local/bin/trimmomatic

# 3. Copia os dados do curso para dentro da imagem
# A pasta 'course_data' do seu repositório será copiada para '/home/vscode/data'
COPY data/ /home/vscode/data/

# 4. Configura o usuário padrão do Codespace ('vscode')
RUN useradd -m -s /bin/bash vscode && \
    echo "vscode:vscode" | chpasswd && \
    usermod -aG sudo vscode

# Garante que o usuário 'vscode' seja o dono da pasta de dados
RUN chown -R vscode:vscode /home/vscode/data

# Permite que o usuário 'vscode' use 'sudo' sem senha
RUN echo "vscode ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Define 'vscode' como o usuário ativo e define o diretório de trabalho padrão
USER vscode
WORKDIR /home/vscode
