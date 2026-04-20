# Revisão da Monografia — Entrega

> Documento-guia das alterações feitas nesta revisão.
> Leia este arquivo antes de abrir o projeto no Overleaf/VSCode.

## 📋 Resumo das alterações

### Estrutura dos capítulos

**Antes (5 capítulos):**
```
01 Introdução                  [vazio, só TO DO]
02 Trabalhos Relacionados      (arquivo chamava 'fundamentacao_teorica.tex'
                                mas \chapter era 'Trabalhos Relacionados' —
                                nome desalinhado com conteúdo)
03 Desenvolvimento/Metodologia [misturava teoria com metodologia]
04 Resultados                  [vazio]
05 Considerações               [vazio]
```

**Depois (6 capítulos):**
```
01 Introdução                  [mantido vazio — não foi foco desta revisão]
02 Fundamentação Teórica       [NOVO — teoria migrada do antigo cap 3]
03 Trabalhos Relacionados      [reaproveitado — nome do arquivo corrigido]
04 Metodologia                 [REESCRITO — focado só no "como"]
05 Resultados                  [mantido vazio]
06 Considerações               [mantido vazio]
```

### Arquivos mexidos

| Arquivo | Ação |
|---|---|
| `principal.tex` | Atualizado para incluir novo cap. 2, apagar apêndice poluído, novo .bib |
| `01_capitulo/introducao.tex` | **Não mexido** — foco não foi aqui |
| `02_capitulo/fundamentacao_teorica.tex` | **Novo** — toda a teoria que estava no desenvolvimento.tex |
| `03_capitulo/trabalhos_relacionados.tex` | Renomeado de `fundamentacao_teorica.tex`; conteúdo de Yang et al. mantido, TODO para 5 novos trabalhos |
| `04_capitulo/metodologia.tex` | Renomeado de `desenvolvimento.tex`; **conteúdo reescrito** |
| `05_capitulo/resultados.tex` | Não mexido (vazio) |
| `06_capitulo/consideracoes.tex` | Não mexido (vazio) |
| `referencias.bib` | **Novo** — bibliografia inteira com 20+ refs da área |
| `abntex2-modelo-references.bib` | **Apagado** — era da pessoa anterior (só Pesquisa Operacional) |

### Imagens

| Imagem | Onde ficava | Onde está agora |
|---|---|---|
| `imageArquiteturaRedeNeural.png` | `03_capitulo/` | `02_capitulo/` (Fund. Teórica) |
| `imageMatrizes_sigmoid.png` | `03_capitulo/` | `02_capitulo/` |
| `pixel-nos.png` | `03_capitulo/` | `02_capitulo/` |
| `imagepoda.png` | `03_capitulo/` | `02_capitulo/` |
| `imagepodamagnitude.png` | `03_capitulo/` | `02_capitulo/` |
| `imagepruning.png` | `03_capitulo/` | `02_capitulo/` |
| `P_np_np-completo_np-hard.png` | `02_capitulo/` | **Apagada** (pessoa anterior) |
| `Subdivisão Timetabling.png` | `02_capitulo/` | **Apagada** |
| `Preferências Observadas.png` | `04_capitulo/` | **Apagada** |
| `Quadro_de_horarios_1.png` | `04_capitulo/` | **Apagada** |
| `escolaridade.png` | `04_capitulo/` | **Apagada** |
| `vinculo_ufvjm.png` | `04_capitulo/` | **Apagada** |
| `Questionario_TCC.pdf` | raiz | **Apagada** |

## 🎨 Sistema de marcação de revisão (cores)

No Overleaf/VSCode, o PDF compilado vai mostrar:

- **Preto** — texto do Enzo preservado integralmente (`\mantido{...}` ou sem marca).
- **Laranja** — texto do Enzo com ajustes pontuais (`\modificado{...}`).
- **Verde** — texto novo acrescentado por esta revisão (`\adicionadomarcelo{...}`).
- **Vermelho tachado** — texto removido (`\removido{...}`).
- **Caixas amarelas** — `\todo[inline]{...}` com itens pendentes.

Para remover as cores e gerar o PDF "limpo" no final, basta editar o `principal.tex` e redefinir os comandos para não colorir:

```latex
\renewcommand{\modificado}[1]{#1}
\renewcommand{\adicionadomarcelo}[1]{#1}
```

(Mas recomendo deixar as cores até o orientador revisar.)

## ⚙️ Para compilar

A estrutura do template ABNTeX2 **não foi tocada**. O projeto deve compilar normalmente com:

```bash
pdflatex principal.tex
bibtex principal
pdflatex principal.tex
pdflatex principal.tex
```

Ou pelo botão de compilação do Overleaf/VSCode.

## 📌 Itens pendentes (TODOs) que ficaram no texto

Todos os itens pendentes estão marcados como `\todo[inline]{...}` e aparecerão destacados no PDF. Os principais são:

1. **Cap. 3 (Trabalhos Relacionados):** adicionar 5 resenhas sugeridas (Han et al., Li et al., Frankle & Carbin, Blalock et al., Liu et al.).
2. **Cap. 4 (Metodologia):** produzir figura do *pipeline* geral do trabalho.
3. **Cap. 4 (Metodologia):** produzir tabela-resumo das métricas.
4. **Cap. 4 (Metodologia):** preencher, ao final dos experimentos, especificações de *hardware* e versões das bibliotecas.

## 🗣️ Pontos para levar ao orientador

1. **Reorganização para 6 capítulos** — foi decidido em conversa contigo, mas vale confirmar com o orientador. Se ele preferir 5, é só juntar Fund. Teórica + Metodologia num capítulo só.
2. **Decisão por CIFAR-100 em vez de ImageNet-1K** — justificada na seção 4.2 (Dataset) da metodologia; vale mencionar explicitamente.
3. **Dois métodos de poda escolhidos** — seção 4.5 explica a lógica (um não-estruturado, um estruturado, complementares).
4. **Estratégia otimizada: sensibilidade por camada** — seção 4.6. Se o orientador quiser algo mais ousado, podemos adicionar *distillation*, mas atenção ao prazo.
