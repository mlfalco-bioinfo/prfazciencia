# Etapa 1: Uma Introdução Prática ao Terminal Linux

<br>Conheça o terminal!</br> Pense nele como uma forma de conversar diretamente com o computador. Em vez de clicar em ícones, você digita comandos para dizer a ele exatamente o que fazer. Esta é a ferramenta mais poderosa de um bioinformata.

### Entendendo o Prompt
Você verá algo como `vscode@hostname:~$`. Isso significa:
* `vscode`: Seu nome de usuário.
* `hostname`: O nome do "computador" na nuvem.
* `~`: Seu diretório "home" (sua pasta pessoal).
* `$`: Indica que o terminal está pronto para receber um comando.

---

### 1. Navegação: Onde Estou e Para Onde Vou?
* **`pwd`** (Print Working Directory): Mostra o caminho completo do diretório onde você está.
    ```bash
    pwd
    ```
* **`ls -lh`**: Lista o conteúdo do diretório atual em formato legível.
    ```bash
    ls -lh
    ```
* **`cd`** (Change Directory): Muda de diretório.
    ```bash
    cd data # Entra no diretório 'data'
    ls -lh # Vê o que tem dentro
    cd ..   # Volta para o diretório anterior
    ```

---

### 2. Manipulação: Criando e Gerenciando
* **`mkdir`** (Make Directory): Cria um novo diretório.
    ```bash
    mkdir results
    ```
* **`cp`** (Copy): Copia arquivos.
    ```bash
    cp README.md readme_backup.md
    ```
* **`mv`** (Move): Move ou renomeia arquivos.
    ```bash
    mv readme_backup.md README.bkp
    ```
* **`rm`** (Remove): Remove arquivos. **CUIDADO: ESTE COMANDO É PERMANENTE!**
    ```bash
    rm README.bkp
    ```

---

### 3. Inspeção: Vendo o Conteúdo dos Arquivos
* **`head`** e **`tail`**: Mostram as 10 primeiras (`head`) ou as 10 últimas (`tail`) linhas de um arquivo.
    ```bash
    head data/SRR28199596_1.fastq
    ```

Com estes comandos, você já tem o conhecimento fundamental para prosseguir com o curso.

---
### [➡️ Próxima Etapa: Controle de Qualidade com FastQC](./ETAPA_02_Controle_de_Qualidade_com_FastQC.md)
