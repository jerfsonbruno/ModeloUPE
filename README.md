# modeloUPE

Modelo de relatório/artigo para a Universidade de Pernambuco (Campus Caruaru), no estilo
"Royal Society Open Science", pensado para relatórios de disciplinas de estatística
(regressão linear múltipla, análise de dados, etc.). Disponível tanto para **R**
(pacote + template do R Markdown) quanto para **Python** (extensão do Quarto), usando
exatamente a mesma capa e formatação em LaTeX nos dois casos.

Um exemplo completo de análise (regressão múltipla no conjunto de dados `iris`) vem
pronto em ambas as linguagens:

- R: [inst/rmarkdown/templates/modeloUPE/skeleton/skeleton.Rmd](inst/rmarkdown/templates/modeloUPE/skeleton/skeleton.Rmd)
- Python: [python/relatorio.qmd](python/relatorio.qmd)

## Instalação e uso em R

1. Instale o pacote a partir do GitHub:

   ```r
   install.packages("remotes")
   remotes::install_github("jerfsonbruno/ModeloUPE")
   ```

2. Depois de instalado, abra o RStudio e crie um novo documento a partir do template:

   **File > New File > R Markdown... > From Template > "Modelo de Artigo - Probabilidade e Estatística"**

   O RStudio vai criar uma pasta nova já com o `.Rmd` de exemplo e todos os arquivos de
   apoio (`.cls`, `.bst`, logo, `.bib`, orientações do trabalho).

   Se preferir fazer isso pelo console em vez da interface do RStudio:

   ```r
   rmarkdown::draft(
     "relatorio.Rmd",
     template = "modeloUPE",
     package = "modeloUPE",
     edit = FALSE
   )
   ```

3. Edite o `.Rmd` gerado com sua própria análise e gere o PDF:

   ```r
   rmarkdown::render("relatorio.Rmd")
   ```

## Instalação e uso em Python (via Quarto)

O lado Python usa o [Quarto](https://quarto.org/docs/get-started/) para executar
código Python (Jupyter) e o mesmo template LaTeX do pacote R.

Pré-requisitos: Quarto instalado e Python 3 com Jupyter.

1. Crie a pasta do seu relatório e instale a extensão dentro dela:

   ```bash
   mkdir meu-relatorio && cd meu-relatorio
   quarto add jerfsonbruno/ModeloUPE
   ```

   Isso copia a extensão para `meu-relatorio/_extensions/modeloupe/`. Esse passo
   precisa ser repetido em cada pasta/projeto novo que for usar o template.

2. Copie o exemplo pronto da pasta [python/](python/) deste repositório para dentro
   da sua pasta (`relatorio.qmd`, `modeloUPE.bib`, `orientacoes.tex`,
   `requirements.txt`), ou comece um `.qmd` do zero usando `format: modeloupe-pdf`
   no cabeçalho YAML.

3. Instale as dependências Python (num ambiente virtual, por exemplo):

   ```bash
   python3 -m venv venv && source venv/bin/activate
   pip install -r requirements.txt
   ```

4. Renderize o relatório:

   ```bash
   quarto render relatorio.qmd --to modeloupe-pdf
   ```

## Estrutura do repositório

```
inst/rmarkdown/templates/modeloUPE/   Template R Markdown (pacote R)
_extensions/modeloupe/                Extensão Quarto (formato modeloupe-pdf)
python/                                Exemplo completo em Python + extensão local
```

## Licença

MIT — veja [LICENSE](LICENSE).
