# 🧮 Algorithms and Data Structures

> Preparação focada em Dynamic Programming, padrões de algoritmos e estruturas de dados para entrevistas senior

[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![LeetCode](https://img.shields.io/badge/LeetCode-Practice-orange.svg)](https://leetcode.com/)

---

## 📚 Estrutura do Repositório

```
.
├── dynamic-programming/     # Foco principal - DP problems
│   ├── 1d-patterns/        # Padrões lineares
│   ├── 2d-patterns/        # Padrões bidimensionais
│   ├── knapsack/           # Variações de knapsack
│   └── hard-problems/      # Problemas avançados
├── data-structures/        # Implementações de estruturas
├── sorting-searching/      # Algoritmos clássicos
├── graphs/                 # Grafos e BFS/DFS
├── trees/                  # Árvores e traversals
├── cheatsheets/           # Guias rápidos de padrões
└── docs/                  # Logs de estudo
```

---

## 🎯 Dynamic Programming - Foco Principal

### Padrões 1D (Semana 4 - Dias 1-2)

| # | Problema | LeetCode | Dificuldade | Status | Padrão |
|---|----------|----------|-------------|--------|--------|
| 1 | Coin Change | [322](https://leetcode.com/problems/coin-change/) | Medium | 🔴 | Min coins |
| 2 | House Robber | [198](https://leetcode.com/problems/house-robber/) | Medium | 🔴 | Skip pattern |
| 3 | Longest Increasing Subsequence | [300](https://leetcode.com/problems/longest-increasing-subsequence/) | Medium | 🔴 | LIS |
| 4 | Climbing Stairs | [70](https://leetcode.com/problems/climbing-stairs/) | Easy | 🔴 | Fibonacci-like |
| 5 | Decode Ways | [91](https://leetcode.com/problems/decode-ways/) | Medium | 🔴 | Count ways |

### Padrões 2D (Semana 4 - Dia 3)

| # | Problema | LeetCode | Dificuldade | Status | Padrão |
|---|----------|----------|-------------|--------|--------|
| 6 | Longest Common Subsequence | [1143](https://leetcode.com/problems/longest-common-subsequence/) | Medium | 🔴 | LCS |
| 7 | Edit Distance | [72](https://leetcode.com/problems/edit-distance/) | Hard | 🔴 | String matching |
| 8 | Unique Paths II | [63](https://leetcode.com/problems/unique-paths-ii/) | Medium | 🔴 | Grid paths |
| 9 | Minimum Path Sum | [64](https://leetcode.com/problems/minimum-path-sum/) | Medium | 🔴 | Grid optimization |

### Knapsack Variations (Semana 4 - Dia 4)

| # | Problema | LeetCode | Dificuldade | Status | Padrão |
|---|----------|----------|-------------|--------|--------|
| 10 | Partition Equal Subset Sum | [416](https://leetcode.com/problems/partition-equal-subset-sum/) | Medium | 🔴 | 0/1 Knapsack |
| 11 | Target Sum | [494](https://leetcode.com/problems/target-sum/) | Medium | 🔴 | Count subsets |
| 12 | Coin Change 2 | [518](https://leetcode.com/problems/coin-change-2/) | Medium | 🔴 | Unbounded knapsack |

### Hard Problems (Semana 4 - Dia 5)

| # | Problema | LeetCode | Dificuldade | Status | Padrão |
|---|----------|----------|-------------|--------|--------|
| 13 | Regular Expression Matching | [10](https://leetcode.com/problems/regular-expression-matching/) | Hard | 🔴 | String DP |
| 14 | Burst Balloons | [312](https://leetcode.com/problems/burst-balloons/) | Hard | 🔴 | Interval DP |
| 15 | Interleaving String | [97](https://leetcode.com/problems/interleaving-string/) | Medium | 🔴 | 2D DP |

**Legenda:** 🔴 Pendente | 🟡 Em progresso | 🟢 Resolvido

---

## 📖 Cheatsheets Disponíveis

- **[DP Patterns Cheatsheet](./cheatsheets/dp-patterns.md)** - Todos os padrões identificados
- **[Time Complexity Guide](./cheatsheets/time-complexity.md)** - Big O reference
- **[Study Log](./docs/study-log.md)** - Progresso diário

---

## 📁 Estrutura de Cada Solução

```
problema-nome/
├── README.md              # Explicação do problema
├── solution.py            # Solução otimizada
├── solution_brute.py      # Solução força bruta (para comparar)
├── test_solution.py       # Testes
└── notes.md              # Notas pessoais e padrão identificado
```

---

## 🎯 Metodologia de Estudo

### Para Cada Problema:

1. **Entender** (5min)
   - Ler problema
   - Identificar inputs/outputs
   - Pensar em exemplos

2. **Identificar Padrão** (5min)
   - Qual padrão de DP?
   - Já vi problema similar?
   - Qual a recorrência?

3. **Resolver** (30-40min)
   - Começar com força bruta
   - Identificar overlapping subproblems
   - Criar tabela DP
   - Otimizar espaço se possível

4. **Testar** (5min)
   - Edge cases
   - Verificar complexidade

5. **Documentar** (5min)
   - Adicionar ao cheatsheet
   - Escrever padrão identificado

---

## 🚀 Como Usar Este Repositório

### Setup Inicial

```bash
# Clonar
git clone https://github.com/seu-username/algorithms-and-data-structures.git
cd algorithms-and-data-structures

# Criar ambiente virtual
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Instalar dependências
pip install -r requirements.txt
```

### Rodar Testes

```bash
# Todos os testes
pytest

# Teste específico
pytest dynamic-programming/1d-patterns/coin-change/test_solution.py -v

# Com coverage
pytest --cov=. --cov-report=html
```

### Adicionar Nova Solução

```bash
# Usar template
cp -r docs/problem-template dynamic-programming/1d-patterns/novo-problema
cd dynamic-programming/1d-patterns/novo-problema
# Editar arquivos...
```

---

## 📊 Progresso Geral

```
Problemas Resolvidos: 0/15+ (0%)
Padrões Identificados: 0/10 (0%)
Cheatsheet Completo: 0%
```

**Última atualização:** 29/10/2025

---

## 🎓 Padrões de DP Identificados

Será preenchido conforme o estudo:

- [ ] **1D Linear DP** - Fibonacci-like problems
- [ ] **House Robber Pattern** - Skip elements
- [ ] **Coin Change Pattern** - Unbounded choices
- [ ] **LIS Pattern** - Longest increasing subsequence
- [ ] **2D Grid DP** - Unique paths variants
- [ ] **LCS Pattern** - String matching
- [ ] **0/1 Knapsack** - Binary choice per item
- [ ] **Unbounded Knapsack** - Unlimited items
- [ ] **Interval DP** - Burst balloons style
- [ ] **State Machine DP** - Buy/sell stock

---

## 📖 Recursos Recomendados

### Online
- [NeetCode Roadmap](https://neetcode.io/roadmap)
- [LeetCode Patterns](https://seanprashad.com/leetcode-patterns/)
- [DP for Beginners](https://leetcode.com/discuss/general-discussion/662866/dp-for-beginners-problems-patterns-sample-solutions)

### Vídeos
- [NeetCode - DP Playlist](https://www.youtube.com/watch?v=73r3KWiEvyk&list=PLot-Xpze53lcvx_tjrr_m2lgD2NsRHlNO)
- [Back To Back SWE - DP](https://www.youtube.com/c/BackToBackSWE)

### Livros
- [Grokking Dynamic Programming Patterns](https://www.educative.io/courses/grokking-dynamic-programming-patterns-for-coding-interviews)

---

## 💡 Dicas de Estudo

1. **Não decore soluções** - Entenda o padrão
2. **Resolva no papel primeiro** - Depois code
3. **Sempre comece com força bruta** - Depois otimize
4. **Identifique overlapping subproblems** - É o sinal de DP
5. **Desenhe a tabela DP** - Visualize o problema
6. **Pratique articular a solução** - Como se estivesse em entrevista

---

## 📝 Formato de Commit

```bash
# Ao adicionar solução
git commit -m "feat(dp): add coin change solution with notes"

# Ao atualizar cheatsheet
git commit -m "docs(cheatsheet): add knapsack pattern"

# Ao adicionar testes
git commit -m "test(dp): add edge cases for house robber"
```

---

## 📫 Notas

Este repositório é parte do plano de estudos de 45 dias focado em preparação para entrevistas senior backend. O foco principal está em Dynamic Programming durante a Semana 4 (28/10 - 01/11/2025).

---

**Status:** 🚧 Início previsto para 29/10/2025
