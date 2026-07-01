<p align="center">
  <img src="course/images/quartoodissey.png" alt="2001: A Quarto Odyssey — Escola de Verão MEDCIDS 2026" width="320">
</p>

# 2001: A Quarto Odyssey — Workshop

Curso sobre Quarto, Zotero e R para investigação reproduzível em saúde. FMUP / MEDCIDS Escola de Verão 2026.

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/tiagojct/ev2026-quarto-odyssey-students)

## Como começar

1. Cria uma conta GitHub gratuita, se ainda não tiveres.
2. Carrega em **"Use this template" → "Create a new repository"** no canto superior desta página. Faz uma cópia para a tua conta (podes deixá-la privada).
3. No teu novo repositório, carrega em **"Code" → "Codespaces" → "Create codespace on main"**.
4. Espera dois a três minutos no primeiro arranque. O Codespace usa a imagem `rocker-org/devcontainer/tidyverse` com a feature `quarto-cli` (TinyTeX incluído), que traz R, tidyverse, Quarto e LaTeX já instalados.
5. Quando o VS Code abrir, o terminal já está aberto em baixo. Para abrir o curso no navegador:

   ```bash
   quarto preview course/course.qmd
   ```

   Abre um separador novo com o documento do curso. Navega pelo índice à esquerda.

   Quando renderizares um PDF (exercício 3), carrega duas vezes no ficheiro `.pdf` no painel de ficheiros à esquerda — abre num visualizador de PDF dentro do próprio Codespace, sem precisares de descarregar nada.

   Os slides de abertura ficam em `presentation/slides.qmd` — renderiza-os com `quarto preview presentation/slides.qmd` se quiseres a versão local, ou consulta directamente a versão [online](https://tiagojct.eu/quarto-odissey/slides/). Não são necessários para os exercícios, só para acompanhar a introdução.

## Estrutura

```
.
├── course/
│   ├── course.qmd                  # Documento do curso (Quarto HTML)
│   ├── theme.scss                  # Tema visual (paleta do poster)
│   └── images/                     # Poster e outras imagens
├── presentation/
│   └── slides.qmd                  # Slides de abertura (Quarto reveal.js)
└── exercises/
    ├── 01-zotero/                  # Biblioteca Zotero + Better BibTeX (local)
    ├── 02-quarto-analysis/         # Quarto + R chunks (no Codespace)
    │   ├── data/cohort-asma.csv
    │   └── template/
    │       ├── manuscript.qmd
    │       ├── references.bib
    │       └── vancouver.csl, nature.csl
    └── 03-writing-export/          # Citações + exportação para .docx/PDF/HTML
```

## Requisitos

- Conta GitHub (qualquer plano gratuito).
- Navegador moderno.
- **Para o exercício 1 apenas:** Zotero 7+ na tua máquina local. O Zotero é uma aplicação desktop e não corre dentro do Codespace.

Tudo o resto (R, tidyverse, Quarto, LaTeX) está pré-instalado no Codespace. Não precisas de instalar nada no teu computador.

## Aviso

Os dados disponíveis no exercício 2 são **sintéticos**. Para os teus projectos reais com dados de doentes, vê a secção "Dados sintéticos e dados reais" em [`course/course.qmd`](course/course.qmd) e confirma a política da tua instituição.
