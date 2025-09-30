# Etapa 4: Desafio - Limpando um Novo Dataset

Chegou a hora de aplicar tudo o que você aprendeu! Nesta etapa, você não terá uma "receita de bolo". Seu objetivo é usar as ferramentas **FastQC** e **Trimmomatic** para diagnosticar e limpar um novo conjunto de dados.

### A Missão

Seus novos arquivos de dados brutos são:
* `data/SRR7694205_1.fastq`
* `data/SRR7694205_2.fastq`

Sua tarefa é seguir o fluxo de trabalho que aprendemos:

1.  **Diagnosticar:** Execute o **FastQC** nos dois arquivos brutos para identificar os problemas de qualidade. Analise os relatórios. O que você consegue notar sobre a qualidade das bases e a presença de adaptadores?

2.  **Limpar:** Escreva e execute um comando **Trimmomatic** para corrigir os problemas que você encontrou. Você precisará escolher os parâmetros corretos (como `SLIDINGWINDOW` e `MINLEN`) e usar o arquivo de adaptadores que já está na pasta `data`.

3.  **Verificar:** Execute o **FastQC** novamente nos arquivos limpos (os que terminam em `_1P.fastq.gz` e `_2P.fastq.gz`) para confirmar que sua limpeza foi bem-sucedida.

### Critérios de Sucesso

Você terá concluído o desafio com sucesso quando os relatórios do FastQC dos seus arquivos limpos mostrarem:
* ✅ O gráfico "Per base sequence quality" com a maior parte das bases na zona verde (acima de Q28).
* ✅ O módulo "Adapter Content" passando (sem contaminação de adaptadores detectada).

---
<details>
  <summary>Clique aqui para ver uma possível solução</summary>

  ### Possível Solução

  Seu comando do Trimmomatic pode variar, mas um que funcionaria muito bem para este dataset é o seguinte:

  ```bash
  # Criando os diretórios de saída
  mkdir -p data/trimmed_desafio
  mkdir -p results/fastqc_raw_desafio
  mkdir -p results/fastqc_trimmed_desafio

  # 1. Rodando o QC inicial
  fastqc data/SRR7694205_1.fastq data/SRR7694205_2.fastq -o results/fastqc_raw_desafio

  # 2. Comando do Trimmomatic
  trimmomatic PE -threads 4 \
    data/SRR7694205_1.fastq data/SRR7694205_2.fastq \
    data/trimmed_desafio/SRR7694205_1P.fastq.gz data/trimmed_desafio/SRR7694205_1U.fastq.gz \
    data/trimmed_desafio/SRR7694205_2P.fastq.gz data/trimmed_desafio/SRR7694205_2U.fastq.gz \
    ILLUMINACLIP:data/TruSeq3-PE-2.fa:2:30:10 \
    LEADING:3 \
    TRAILING:3 \
    SLIDINGWINDOW:4:20 \
    MINLEN:36

  # 3. Verificando o resultado
  fastqc data/trimmed_desafio/SRR7694205_1P.fastq.gz data/trimmed_desafio/SRR7694205_2P.fastq.gz -o results/fastqc_trimmed_desafio
```
