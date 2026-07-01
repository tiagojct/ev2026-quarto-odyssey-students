# Exercício 2 — Análise em Quarto

## Objectivo

Completar um documento `.qmd` parcialmente preenchido com blocos de código R que produzem uma **tabela descritiva** e um **gráfico**, e renderizar o resultado para HTML.

## Antes de começar

- Exercício 1 não precisa estar concluído para começar este. Mas precisas do Codespace aberto.
- R, Quarto e os pacotes necessários (`tidyverse`, `gt`, `ggplot2`) já estão instalados no Codespace.
- O dataset (`data/cohort-asma.csv`) e o template (`template/manuscript.qmd`) estão na pasta deste exercício.

## O dataset

`exercises/02-quarto-analysis/data/cohort-asma.csv` — cerca de 200 doentes pediátricos com asma, com 8 variáveis: `patient_id`, `age`, `sex`, `height_cm`, `weight_kg`, `fev1_l`, `fvc_l`, `asthma_severity`.

Os dados são sintéticos e limpos — sem missing, sem valores impossíveis. O objectivo aqui não é qualidade de dados, é demonstrar como o código R dentro de um `.qmd` produz tabelas e gráficos.

## Passos

### 1. Abre o template

No VS Code do Codespace, abre `exercises/02-quarto-analysis/template/manuscript.qmd`. Lê o YAML *front matter* — vais ver título, autor, data, formato, e a directiva `bibliography`.

### 2. Inicia o pré-visualizador

No terminal:

```bash
cd exercises/02-quarto-analysis/template
quarto preview manuscript.qmd
```

Abre uma página com o documento renderizado. Cada vez que gravares o `.qmd`, a página actualiza-se automaticamente.

### 3. Completa o primeiro chunk — leitura dos dados

No chunk marcado com o comentário `# TODO: chunk 1`, escreve código R que carregue o dataset e guarde-o num objecto chamado `cohort`. Algo como:

```r
library(tidyverse)

cohort <- read_csv("../data/cohort-asma.csv")
```

> Atenção ao caminho relativo: o ficheiro `.qmd` está em `template/`, e o dataset está em `../data/cohort-asma.csv`.

### 4. Completa o segundo chunk — tabela descritiva

No chunk marcado com `# TODO: chunk 2`, produz uma tabela com:

- N por sexo.
- Média e desvio-padrão da idade, em cada grupo de sexo.
- Média e desvio-padrão do FEV1, em cada grupo de sexo.

Usa `dplyr` para o cálculo e `gt` (ou `knitr::kable`) para a formatação.

Dá ao chunk o label `tbl-demographics` e uma legenda em `tbl-cap`.

### 5. Completa o terceiro chunk — gráfico

No chunk marcado com `# TODO: chunk 3`, faz um gráfico com `ggplot2`:

- Eixo X: idade.
- Eixo Y: FEV1 em litros.
- Cor por gravidade da asma (`asthma_severity`).
- Adiciona uma linha de regressão linear (`geom_smooth(method = "lm")`).

Dá ao chunk o label `fig-fev1-age` e uma legenda em `fig-cap`.

### 6. Cita as figuras no texto

Na secção de resultados, escreve uma frase a referenciar a tabela e o gráfico:

```markdown
As características demográficas da amostra estão sumariadas na @tbl-demographics.
A relação entre idade e função pulmonar, estratificada por gravidade, está
ilustrada na @fig-fev1-age.
```

### 7. Renderiza para HTML

Se o pré-visualizador já está aberto, só precisas de gravar o ficheiro. Se não:

```bash
quarto render manuscript.qmd --to html
```

## Output esperado

- `manuscript.html` na pasta `template/`, com tabela e gráfico visíveis.
- As referências cruzadas (`@tbl-demographics`, `@fig-fev1-age`) substituídas por "Tabela 1", "Figura 1" no texto.

## Para discussão

- O que aconteceria se mudasses um valor no `cohort-asma.csv` e re-renderizasses? Tenta.
- Se removesses o `label` de um chunk, conseguirias ainda referenciá-lo?
- Que opções de chunk usaste? `echo`? `warning`? Porquê?
- Como ficou o tempo de render? Mais rápido ou mais lento do que esperavas?
