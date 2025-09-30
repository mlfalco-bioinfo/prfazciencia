#### **Arquivo: `tutoriais/ETAPA_03_Limpeza_de_Dados_com_Trimmomatic.md`**

# Etapa 3: Limpeza (Trimming) de Dados com Trimmomatic

Com base no relatório do FastQC, vimos que a qualidade dos reads pode ser melhorada. A ferramenta **Trimmomatic** é usada para remover adaptadores e cortar bases de baixa qualidade das pontas das leituras.

### Parte 1: Executando a Limpeza

Primeiro, vamos criar um diretório para salvar nossos novos arquivos de reads, já limpos.
```bash
mkdir -p data/trimmed_reads
```

Agora, vamos executar o Trimmomatic. O comando é longo, mas cada parte tem uma função específica:

**PE**: Indica que nossos dados são Paired-End.

**-threads 4**: Usa 4 núcleos para acelerar o processo.

**ILLUMINACLIP**: Remove as sequências de adaptadores.

**SLIDINGWINDOW**: Corta o read se a qualidade média em uma janela de 4 bases cair abaixo de 20.

**MINLEN**: Descarta reads que ficarem com menos de 36 bases após a limpeza.



### Parte 2: Executando o Trimmomatic
```bash
trimmomatic PE -threads 4 \
  data/SRR28199596_1.fastq data/SRR28199596_2.fastq \
  data/trimmed_reads/SRR28199596_1P.fastq.gz data/trimmed_reads/SRR28199596_1U.fastq.gz \
  data/trimmed_reads/SRR28199596_2P.fastq.gz data/trimmed_reads/SRR28199596_2U.fastq.gz \
  ILLUMINACLIP:data/TruSeq3-PE-2.fa:2:30:10 \
  SLIDINGWINDOW:4:20 \
  MINLEN:36
```
Ao final, teremos os arquivos `_1P.fastq.gz` e `_2P.fastq.gz` na pasta `data/trimmed_reads`, que são os reads pareados que passaram pela limpeza.


### Parte : Reavaliando a Qualidade

Será que a limpeza funcionou? Vamos rodar o FastQC novamente, mas desta vez nos arquivos limpos, para comparar os resultados.

Primeiro, crie um novo diretório para os relatórios pós-limpeza:

```bash
mkdir -p results/fastqc_trimmed
```

Agora, execute o FastQC nos reads trimados:

```bash
fastqc data/trimmed_reads/SRR28199596_1P.fastq.gz data/trimmed_reads/SRR28199596_2P.fastq.gz -o results/fastqc_trimmed
```

Abra os novos relatórios e compare com os antigos. Você notará uma melhora significativa na qualidade das bases, especialmente no final das leituras.

**Fim do Minicurso!**

Parabéns! Você completou o fluxo de trabalho essencial de controle de qualidade e limpeza de dados NGS. Seus dados agora estão prontos para análises mais avançadas.

### [➡️  Voltar para a Página Inicial](../README.md)
