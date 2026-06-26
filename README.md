# RideSmart

## Modelagem e Análise de Rotas Urbanas com Grafos

Dado um ponto de origem `A`, um destino `B` e uma distância máxima que o usuário aceita caminhar, o RideSmart escolhe o melhor ponto de embarque `P` que minimize o custo total da viagem (caminhada `A → P` + carro `P → B`).

O notebook compara quatro algoritmos de caminho mínimo — Dijkstra simples, Dijkstra com heap, A\* geográfico e Bellman-Ford — aplicados à malha viária real obtida do OpenStreetMap, com e sem trânsito sintético.

---

## Pré-requisitos

- Python 3.12+
- `pip` (gerenciador de pacotes)

## Instalação

```bash
# Clone o repositório
git clone git@github.com:Lucasadasc/projeto-ridesmart.git
cd projeto-ridesmart

# Crie e ative o ambiente virtual
python -m venv venv
source venv/bin/activate        # Linux/macOS
# venv\Scripts\activate         # Windows

# Instale as dependências
pip install osmnx networkx pandas matplotlib scikit-learn ipykernel

# Registre o kernel no Jupyter
python -m ipykernel install --user --name ridesmart
```

## Execução

```bash
jupyter lab
# ou
jupyter notebook
```

Abra `projeto_final.ipynb`, selecione o kernel **ridesmart** e execute as células em ordem.

> O download da malha viária do OpenStreetMap requer acesso à internet na primeira execução. Depois disso os dados ficam em cache.

---

## Estrutura do projeto

```
projeto-ridesmart/
├── projeto_final.ipynb          # Notebook principal com implementação e análise
├── README.md
├── cache/                       # Cache do OSMnx (dados do OpenStreetMap)
├── docs/
│   └── relatorio.tex            # Relatório acadêmico (IEEE dupla coluna, LaTeX)
├── anim_dijkstra_simples.gif    # Animação — Dijkstra simples
├── anim_dijkstra_heap.gif       # Animação — Dijkstra com heap
├── anim_astar.gif               # Animação — A* geográfico
├── anim_bellman_ford.gif        # Animação — Bellman-Ford
├── anim_comparativo.gif         # Animação — comparativo 4 algoritmos
├── mapa_interativo.html         # Mapa interativo (Plotly)
└── venv/                        # Ambiente virtual (não versionado)
```

---

## Algoritmos implementados

| Algoritmo         | Complexidade     | Suporte a pesos negativos |
| ----------------- | ---------------- | ------------------------- |
| Dijkstra simples  | O(V²)            | Não                       |
| Dijkstra com heap | O((V + E) log V) | Não                       |
| A\* geográfico    | O((V + E) log V) | Não                       |
| Bellman-Ford      | O(V · E)         | Sim                       |

---

## Resultados

### Animações — Expansão dos Algoritmos

Cada GIF mostra a ordem de expansão dos nós (azul) até encontrar o caminho mínimo (verde) entre o ponto de embarque `P` e o destino `B`.

![Comparativo dos 4 algoritmos](anim_comparativo.gif)

### Mapa Interativo (Plotly)

O mapa interativo em HTML mostra a rota completa `A → P → B` sobre a malha viária, com zoom e pan.  
Arquivo: [`mapa_interativo.html`](mapa_interativo.html) — abra no navegador.

---

## Relatório Acadêmico (IEEE Dupla Coluna)

Arquivo LaTeX: `docs/relatorio.tex` — 7 seções em 3 páginas.

**Compilar o PDF:**

```bash
cd docs
pdflatex relatorio.tex
pdflatex relatorio.tex   # segunda passagem para referências cruzadas
```

🔗 **Acesse o Relatório Final em PDF:** [docs/relatorio.pdf](docs/relatorio.pdf)

### Validação de Referências

**Citações usadas × bibitems definidos:** `osmnx`, `networkx`, `cormen` — todas com entrada na `thebibliography`.  
**Orfãos na bibliografia:** `boeing`, `dijkstra`, `hart`, `bellman` — definidos mas sem `\cite{}` no texto (mantidos por completude das fontes originais).  
**Labels × refs:** `tab:pesos`, `tab:desempenho`, `tab:rotas`, `eq:custo` — todos emparelhados corretamente.  
**Equações expositivas** (sem `\ref`): `eq:walktime`, `eq:euclidiana` — intencional.

---

## Apresentação (Demo Section)

A apresentação contendo os slides da Demo Section pode ser visualizada e compilada no diretório `docs`.

🔗 **Acesse os Slides em PDF:** [docs/apresentacao.pdf](docs/apresentacao.pdf)


---

## Integrantes

| Nome                           | GitHub                                             |
| ------------------------------ | -------------------------------------------------- |
| Eugenio Vitor Lopes dos Santos | [@EugenioVLopes](https://github.com/EugenioVLopes) |
| Lucas Augusto da Silva Cardoso | [@Lucasadasc](https://github.com/Lucasadasc)       |
| Pedro Henrique Ribeiro de Lima | [@pedenriqu3](https://github.com/pedenriqu3)       |

---

## Referências

- [OSMnx](https://geoffboeing.com/21mn-urban-form-crunch/) — download e manipulação de grafos viários do OpenStreetMap
- [NetworkX](https://networkx.org/) — biblioteca de grafos em Python
- Projeto final da disciplina de Algoritmos e Estruturas de Dados II — UFRN 2026.1
