# Etapa 2: Controle de Qualidade (QC) com FastQC

O primeiro passo em qualquer análise de NGS é verificar a qualidade dos dados brutos que saem do sequenciador. Para isso, usamos a ferramenta **FastQC**, que gera um relatório detalhado sobre nossas leituras.

### 1. Organizando os Resultados

É uma boa prática criar um diretório específico para cada resultado. Vamos criar uma pasta para os relatórios do FastQC.

```bash
mkdir -p results/fastqc_raw
```

### 2. Executando o FastQC

```bash
fastqc data/SRR5199203_1.fastq data/SRR5199203_2.fastq -o results/fastqc_raw
```

### 3. Analisando o Relatório

Após a execução, navegue pela árvore de diretórios à esquerda e entre em `results/fastqc_raw`. Você verá dois arquivos .html.

Para visualizar um relatório:

Clique com o botão direito sobre o arquivo `SRR5199203_1_fastqc.html`.

Selecione **"Open with Live Server"** (se disponível) ou **"Open in Browser"**.

<br>O que observar?</br> 
Preste atenção principalmente no gráfico "Per base sequence quality". 
É comum que a qualidade caia no final das leituras. Identificar isso é o motivo pelo qual a próxima etapa de limpeza é tão importante.

### [➡️ Próxima Etapa: Limpeza de Dados com Trimmomatic](./ETAPA_03_Limpeza_de_Dados_com_Trimmomatic.md)
