# Etapa 4: Controle de Qualidade (QC) com FastQC

É crucial verificar a qualidade dos dados brutos antes de qualquer análise.

### 1. Criando um diretório para os resultados do QC
```bash
mkdir -p results/fastqc_raw
```

### 2. Rodando o FASTQC
Vamos rodar o programa que analisa a qualidade dos `reads` e bases sequenciadas.

```bash
fastqc data/SRR28199596_1.fastq data/SRR28199596_2.fastq -o results/fastqc_raw
```
