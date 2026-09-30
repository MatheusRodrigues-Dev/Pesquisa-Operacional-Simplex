<div align="center">

# Pesquisa Operacional em Python

**Implementações didáticas de otimização para estudo e experimentação com Programação Linear e Programação Inteira.**

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-F37626?logo=jupyter&logoColor=white)
![PuLP](https://img.shields.io/badge/Otimização-PuLP-2C3E50)
![Status](https://img.shields.io/badge/status-projeto%20didático-informational)

</div>

---

## Sobre o projeto

Este repositório reúne implementações e exemplos de **Pesquisa Operacional** em Python, com foco em modelagem matemática, resolução de problemas de otimização e interpretação dos resultados.

O projeto combina uma implementação didática própria dos métodos **Simplex Primal e Dual** com modelos de **Programação Inteira** resolvidos por meio do **PuLP/CBC**.

### Conteúdos disponíveis

| Tema | Abordagem | Arquivo |
| --- | --- | --- |
| Simplex Primal e Dual | Implementação própria com NumPy | [`dual-simplex.ipynb`](dual-simplex.ipynb) |
| Problema da Mochila 0-1 | Programação inteira binária com PuLP | [`mochila.ipynb`](mochila.ipynb) |
| Problema do Caixeiro-Viajante (TSP) | Formulação MTZ com PuLP | [`caixeiro-viajante.ipynb`](caixeiro-viajante.ipynb) |
| Orçamento de Capital | Seleção binária de projetos com restrições anuais | [`fabrica.ipynb`](fabrica.ipynb) |

---

## Estrutura do repositório

```text
.
├── classes/
│   ├── ClassCaixeiro.py      # Funções auxiliares e solver MTZ para o TSP
│   ├── ClassMochileiro.py    # Classe reutilizável para o problema da mochila
│   └── SimplexSolver.py      # Implementação didática do Simplex Primal/Dual
├── src/
│   └── dados_entrada.txt     # Exemplo de dados gerados para testes do Simplex
├── caixeiro-viajante.ipynb  # Exemplo do Problema do Caixeiro-Viajante
├── dual-simplex.ipynb        # Exemplos de Simplex Primal e Dual
├── fabrica.ipynb             # Exemplo de orçamento de capital
├── mochila.ipynb             # Exemplo do Problema da Mochila
├── requirements.txt          # Dependências do projeto
├── .gitignore
└── README.md
```

---

## Como executar

### 1. Clone o repositório

```bash
git clone https://github.com/MatheusRodrigues-Dev/Pesquisa-Operacional-Simplex.git
cd Pesquisa-Operacional-Simplex
```

### 2. Crie um ambiente virtual

```bash
python -m venv .venv
```

**Windows:**

```bash
.venv\Scripts\activate
```

**Linux/macOS:**

```bash
source .venv/bin/activate
```

### 3. Instale as dependências

```bash
pip install -r requirements.txt
```

### 4. Abra os notebooks

```bash
jupyter lab
```

---

## Exemplo rápido — Simplex

A classe `SimplexSolver` recebe os coeficientes da função objetivo, a matriz de restrições, o lado direito e o tipo de cada restrição.

```python
from classes.SimplexSolver import SimplexSolver

c = [320, 530]
A = [
    [2, 1],
    [1, 3],
]
b = [4, 6]
constraints = ["<=", "<="]

solver = SimplexSolver(
    c=c,
    A=A,
    b=b,
    constraints=constraints,
    problem_type="max",
)

solution, optimal_value = solver.solve()

print("Solução:", solution)
print("Valor ótimo:", optimal_value)
```

Durante a resolução, o solver imprime os **tableaux de cada iteração**, permitindo acompanhar o processo de pivoteamento.

---

## Modelos implementados

### Simplex Primal e Dual

A implementação em [`classes/SimplexSolver.py`](classes/SimplexSolver.py) utiliza NumPy para construir e atualizar os tableaux. O código escolhe entre o procedimento primal e o dual de acordo com a forma inicial do problema após o pré-processamento das restrições.

### Mochila 0-1

O notebook [`mochila.ipynb`](mochila.ipynb) utiliza a classe `KnapsackSolver`, baseada em PuLP, para escolher um subconjunto de itens que maximize o valor total sem ultrapassar a capacidade disponível.

### Caixeiro-Viajante

O notebook [`caixeiro-viajante.ipynb`](caixeiro-viajante.ipynb) modela o TSP com variáveis binárias e restrições **MTZ (Miller–Tucker–Zemlin)** para eliminação de sub-rotas. O projeto também possui funções para cálculo da matriz de distâncias e visualização da rota.

### Orçamento de Capital

O notebook [`fabrica.ipynb`](fabrica.ipynb) apresenta um problema de seleção de projetos: o objetivo é maximizar o VPL total respeitando limites de investimento em diferentes períodos.

---

## Dependências principais

- **NumPy** — operações matriciais e implementação do Simplex;
- **PuLP** — modelagem de Programação Linear/Inteira;
- **SciPy** — cálculo de distâncias no exemplo do TSP;
- **Pandas** — apresentação tabular das matrizes;
- **Matplotlib** — visualização gráfica;
- **Jupyter** — execução interativa dos exemplos.

A lista completa está em [`requirements.txt`](requirements.txt).

---

## Limitações atuais

Este é um projeto **didático**, pensado para estudo e demonstração dos conceitos de Pesquisa Operacional.

- A implementação própria do Simplex não pretende substituir solvers numéricos de produção;
- o tratamento atual das restrições não implementa um procedimento completo de **Fase I/Fase II** com variáveis artificiais;
- os modelos inteiros dependem do solver utilizado pelo PuLP, normalmente o CBC;
- casos degenerados, problemas numericamente difíceis ou formulações mais gerais podem exigir tratamento adicional.

Essas limitações são mantidas explícitas para diferenciar a implementação educacional de bibliotecas de otimização destinadas a uso industrial.

---

## Referências

- TAHA, Hamdy A. *Operations Research: An Introduction*.
- HILLIER, Frederick S.; LIEBERMAN, Gerald J. *Introduction to Operations Research*.
- DANTZIG, George B. *Linear Programming and Extensions*.
- [PuLP — documentação oficial](https://coin-or.github.io/pulp/)

---

## Autor

**Matheus Rodrigues**

[GitHub](https://github.com/MatheusRodrigues-Dev)

> Projeto acadêmico e didático voltado ao estudo de Pesquisa Operacional, Programação Linear e Programação Inteira.
