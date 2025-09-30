# Aula 4: Limpeza e Filtragem com Trimmomatic

Com base nos relatórios do FastQC, vamos limpar os reads de baixa qualidade e remover adaptadores usando o Trimmomatic.

### 1. Preparando os diretórios
Criando o diretório das `reads` trimadas.
```bash
mkdir -p data/trimmed_reads
```

Criando o diretório das `reads` trimadas e analisadas novamente pelo controle de qualidade (Fastqc).
```bash
mkdir -p results/fastqc_trimmed
```

### 2. Rodando o Trimmomatic

```bash
java -jar $(which trimmomatic) PE -threads 4 \
  data/SRR28199596_1.fastq data/SRR28199596_2.fastq \
  data/trimmed_reads/SRR28199596_1P.fastq.gz data/trimmed_reads/SRR28199596_1U.fastq.gz \
  data/trimmed_reads/SRR28199596_2P.fastq.gz data/trimmed_reads/SRR28199596_2U.fastq.gz \
  ILLUMINACLIP:/opt/Trimmomatic-0.39/adapters/TruSeq3-PE.fa:2:30:10 \
  LEADING:3 TRAILING:3 SLIDINGWINDOW:4:15 MINLEN:36
```


### 3. Rodando Controle de Qualidade

Novamente rodamos o controle de qualidade (FASTQC) para analisar se houve melhora na qualidade das `reads`.

```bash
fastqc data/trimmed_reads/SRR28199596_1P.fastq.gz data/trimmed_reads/SRR28199596_2P.fastq.gz -o results/fastqc_trimmed
```
