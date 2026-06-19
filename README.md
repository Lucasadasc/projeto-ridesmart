# RideSmart

## Modelagem e Análise de Rotas Urbanas com Grafos

Dado um ponto de origem `A`, um destino `B` e uma distância máxima que o usuário aceita caminhar, o RideSmart escolhe o melhor ponto de embarque `P` que minimize o custo total da viagem (caminhada `A → P` + carro `P → B`).

O notebook compara quatro algoritmos de caminho mínimo — Dijkstra simples, Dijkstra com heap, A* geográfico e Bellman-Ford — aplicados à malha viária real obtida do OpenStreetMap, com e sem trânsito sintético.

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
├── projeto_final.ipynb         # Notebook principal com implementação e análise
├── PROJETO_FINAL_RideSmart.md  # Especificação do projeto
├── README.md
├── cache/                      # Cache do OSMnx (dados do OpenStreetMap)
├── docs/
│   └── relatorio.tex           # Relatório acadêmico (IEEE dupla coluna, LaTeX)
└── venv/                       # Ambiente virtual (não versionado)
```

---

## Algoritmos implementados

| Algoritmo | Complexidade | Suporte a pesos negativos |
|---|---|---|
| Dijkstra simples | O(V²) | Não |
| Dijkstra com heap | O((V + E) log V) | Não |
| A* geográfico | O((V + E) log V) | Não |
| Bellman-Ford | O(V · E) | Sim |

---

## Resultados

> Seção será atualizada com gráficos e tabelas de comparação após a implementação de todas as issues.

---

## Relatório Acadêmico (IEEE Dupla Coluna)

Arquivo LaTeX: `docs/relatorio.tex` —模板 IEEEtran conference, 7 seções com placeholders `[DADOS]`.

**Compilar o PDF:**
```bash
cd docs
pdflatex relatorio.tex
pdflatex relatorio.tex   # segunda passagem para referências cruzadas
```

---

## Integrantes

| Nome | GitHub |
|---|---|
| Eugenio Vitor Lopes dos Santos | [@EugenioVLopes](https://github.com/EugenioVLopes) |
| Lucas Augusto da Silva Cardoso | [@Lucasadasc](https://github.com/Lucasadasc) |
| Pedro Henrique Ribeiro de Lima | [@pedenriqu3](https://github.com/pedenriqu3) |

---

## Referências

- [OSMnx](https://geoffboeing.com/21mn-urban-form-crunch/) — download e manipulação de grafos viários do OpenStreetMap
- [NetworkX](https://networkx.org/) — biblioteca de grafos em Python
- Projeto final da disciplina de Algoritmos e Estruturas de Dados II — UFRN 2026.1
