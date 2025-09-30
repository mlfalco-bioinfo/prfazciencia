# Aula 2: Obtendo os Dados Brutos e o Genoma de Referência

Agora que as ferramentas estão instaladas, vamos baixar nossos dados.

### 1. Preparando os Diretórios

Vamos criar os diretórios onde nossos dados 
```bash
mkdir data
```
e os nossos resultado.

```bash 
mkdir results
```

Agora, com so dois diretórios prontos, vamos fazer o download dos dados.

#### 2. Baixar Genoma de Referência

Navega para o diretório data
```bash
cd data
```

Baixa o arquivo do genoma (formato .fna.gz)
```bash
wget -O ecoli_k12_ref.fna.gz [https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/005/845/GCF_000005845.2_ASM584v2/GCF_000005845.2_ASM584v2_genomic.fna.gz](https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/005/845/GCF_000005845.2_ASM584v2/GCF_000005845.2_ASM584v2_genomic.fna.gz)
```

Descompacta o arquivo
```bash
gunzip ecoli_k12_ref.fna.gz
```

Volta para o diretório raiz
```bash
cd ..
```

#### 3. Baixar os dados do Sequenciamento

# Baixa os reads no formato FASTQ, já separados em arquivos pareados
# A opção -p mostra o progresso do download
```bash
fasterq-dump --split-files --outdir data -p SRR28199596	
```
