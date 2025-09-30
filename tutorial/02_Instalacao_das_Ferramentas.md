# Aula 2: Instalação das Ferramentas no Sistema

Nesta aula, vamos instalar nosso kit de ferramentas. 
Usaremos três métodos diferentes, que são comuns no dia a dia de um bioinformata.

### Método 1: Gerenciador de Pacotes `apt`

O `apt` é o gerenciador de pacotes do Ubuntu. Ele é ótimo para instalar softwares bem estabelecidos que estão nos repositórios oficiais.

Primeiro, vamos sempre atualizar a lista de pacotes do `apt`:
```bash
sudo apt-get update
```


A **primeira** ferramenta é responsável por baixar os dados brutos de sequenciamento. **SRATOOLKIT**
```bash
sudo apt-get install sra-tools
```


O próximo comando testa se a instalação está ok!
```bash
fasterqdump --version
```

A **segunda** ferramenta será o **FASTQC**, ferramenta de análise de qualidade do sequenciamento.
```bash
sudo apt-get install fastqc 
```

Novamente o comando para testar a intalação da ferramenta!
```bash
fastqc --version
```


