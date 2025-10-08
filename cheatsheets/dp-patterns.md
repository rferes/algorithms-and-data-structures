# 🎯 Dynamic Programming Patterns Cheatsheet

> Guia rápido de padrões identificados durante o estudo

---

## 📋 Índice de Padrões

1. [1D Linear DP](#1d-linear-dp)
2. [House Robber Pattern](#house-robber-pattern)
3. [Coin Change Pattern](#coin-change-pattern)
4. [LIS Pattern](#lis-pattern)
5. [2D Grid DP](#2d-grid-dp)
6. [LCS Pattern](#lcs-pattern)
7. [0/1 Knapsack](#01-knapsack)
8. [Unbounded Knapsack](#unbounded-knapsack)
9. [Interval DP](#interval-dp)
10. [State Machine DP](#state-machine-dp)

---

## 1D Linear DP

### 🔍 Como Identificar
- Problema envolve sequência/array
- Decisão atual depende de estado(s) anterior(es)
- Exemplo: Fibonacci, Climbing Stairs

### 📝 Template

```python
def linear_dp(nums):
    n = len(nums)
    dp = [0] * n
    
    # Base case
    dp[0] = nums[0]
    
    # Recorrência
    for i in range(1, n):
        dp[i] = function_of(dp[i-1], nums[i])
    
    return dp[n-1]
```

### 🎯 Problemas
- Climbing Stairs (LC 70)
- Fibonacci Numbers
- Min Cost Climbing Stairs (LC 746)

---

## House Robber Pattern

### 🔍 Como Identificar
- Não pode usar elementos adjacentes
- Maximizar/minimizar com restrições de vizinhança
- Escolha binária com skip

### 📝 Template

```python
def house_robber(nums):
    if not nums: return 0
    if len(nums) == 1: return nums[0]
    
    dp = [0] * len(nums)
    dp[0] = nums[0]
    dp[1] = max(nums[0], nums[1])
    
    for i in range(2, len(nums)):
        # Pegar atual + i-2 OU não pegar (i-1)
        dp[i] = max(dp[i-1], nums[i] + dp[i-2])
    
    return dp[-1]
```

### 🎯 Problemas
- House Robber (LC 198)
- House Robber II (LC 213) - circular
- Delete and Earn (LC 740)

---

## Coin Change Pattern

### 🔍 Como Identificar
- Minimizar número de moedas/itens
- Unlimited supply de cada item
- Atingir valor target

### 📝 Template

```python
def coin_change(coins, amount):
    dp = [float('inf')] * (amount + 1)
    dp[0] = 0
    
    for i in range(1, amount + 1):
        for coin in coins:
            if i >= coin:
                dp[i] = min(dp[i], dp[i - coin] + 1)
    
    return dp[amount] if dp[amount] != float('inf') else -1
```

### 🎯 Problemas
- Coin Change (LC 322)
- Perfect Squares (LC 279)
- Minimum Cost For Tickets (LC 983)

---

## LIS Pattern

### 🔍 Como Identificar
- Encontrar subsequência (não precisa ser contígua)
- Crescente/decrescente
- "Longest" algo

### 📝 Template

```python
def length_of_lis(nums):
    if not nums: return 0
    
    dp = [1] * len(nums)
    
    for i in range(1, len(nums)):
        for j in range(i):
            if nums[i] > nums[j]:
                dp[i] = max(dp[i], dp[j] + 1)
    
    return max(dp)
```

### 🎯 Problemas
- Longest Increasing Subsequence (LC 300)
- Number of LIS (LC 673)
- Russian Doll Envelopes (LC 354)

---

## 2D Grid DP

### 🔍 Como Identificar
- Grid/matriz de inputs
- Movimento limitado (direita, baixo)
- Contar caminhos ou min/max path

### 📝 Template

```python
def unique_paths(m, n):
    dp = [[0] * n for _ in range(m)]
    
    # Base cases: primeira linha e coluna
    for i in range(m):
        dp[i][0] = 1
    for j in range(n):
        dp[0][j] = 1
    
    # Recorrência
    for i in range(1, m):
        for j in range(1, n):
            dp[i][j] = dp[i-1][j] + dp[i][j-1]
    
    return dp[m-1][n-1]
```

### 🎯 Problemas
- Unique Paths (LC 62)
- Unique Paths II (LC 63)
- Minimum Path Sum (LC 64)
- Dungeon Game (LC 174)

---

## LCS Pattern

### 🔍 Como Identificar
- Duas strings/arrays
- Encontrar comum entre elas
- Edit distance variants

### 📝 Template

```python
def lcs(text1, text2):
    m, n = len(text1), len(text2)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if text1[i-1] == text2[j-1]:
                dp[i][j] = dp[i-1][j-1] + 1
            else:
                dp[i][j] = max(dp[i-1][j], dp[i][j-1])
    
    return dp[m][n]
```

### 🎯 Problemas
- Longest Common Subsequence (LC 1143)
- Edit Distance (LC 72)
- Distinct Subsequences (LC 115)
- Shortest Common Supersequence (LC 1092)

---

## 0/1 Knapsack

### 🔍 Como Identificar
- Cada item pode ser usado 0 ou 1 vez
- Capacidade limitada
- Maximizar valor ou contar subsets

### 📝 Template

```python
def knapsack(weights, values, capacity):
    n = len(weights)
    dp = [[0] * (capacity + 1) for _ in range(n + 1)]
    
    for i in range(1, n + 1):
        for w in range(capacity + 1):
            # Não pegar item i
            dp[i][w] = dp[i-1][w]
            
            # Pegar item i (se couber)
            if w >= weights[i-1]:
                dp[i][w] = max(
                    dp[i][w],
                    dp[i-1][w - weights[i-1]] + values[i-1]
                )
    
    return dp[n][capacity]
```

### 🎯 Problemas
- Partition Equal Subset Sum (LC 416)
- Target Sum (LC 494)
- Last Stone Weight II (LC 1049)

---

## Unbounded Knapsack

### 🔍 Como Identificar
- Itens podem ser usados múltiplas vezes
- Unlimited supply
- Similar a Coin Change

### 📝 Template

```python
def unbounded_knapsack(weights, values, capacity):
    dp = [0] * (capacity + 1)
    
    for w in range(capacity + 1):
        for i in range(len(weights)):
            if w >= weights[i]:
                dp[w] = max(dp[w], dp[w - weights[i]] + values[i])
    
    return dp[capacity]
```

### 🎯 Problemas
- Coin Change 2 (LC 518)
- Combination Sum IV (LC 377)
- Perfect Squares (LC 279)

---

## Interval DP

### 🔍 Como Identificar
- Problema envolve intervalos/ranges
- Quebrar em subproblemas menores
- Tipicamente 3 loops nested

### 📝 Template

```python
def interval_dp(nums):
    n = len(nums)
    dp = [[0] * n for _ in range(n)]
    
    # Length do intervalo
    for length in range(2, n + 1):
        for i in range(n - length + 1):
            j = i + length - 1
            
            # Tentar todos k entre i e j
            for k in range(i, j + 1):
                dp[i][j] = max(
                    dp[i][j],
                    function_of(dp, i, k, j)
                )
    
    return dp[0][n-1]
```

### 🎯 Problemas
- Burst Balloons (LC 312)
- Minimum Cost Tree From Leaf Values (LC 1130)
- Stone Game (LC 877)

---

## State Machine DP

### 🔍 Como Identificar
- Estados bem definidos
- Transições entre estados
- Exemplo: Buy/Sell stock

### 📝 Template

```python
def state_machine(prices):
    # Estados possíveis
    hold = float('-inf')  # Tem ação
    sold = 0              # Vendeu
    rest = 0              # Descansando
    
    for price in prices:
        prev_hold = hold
        prev_sold = sold
        
        hold = max(hold, rest - price)     # Comprar
        sold = prev_hold + price           # Vender
        rest = max(rest, prev_sold)        # Descansar
    
    return max(sold, rest)
```

### 🎯 Problemas
- Best Time to Buy and Sell Stock series (LC 121, 122, 123, 188, 309, 714)

---

## 🎓 Como Identificar o Padrão Certo

### Perguntas para fazer:

1. **É 1D ou 2D?**
   - 1 array/string → 1D DP
   - 2 arrays/strings ou grid → 2D DP

2. **Elementos adjacentes têm restrições?**
   - Sim → House Robber pattern

3. **Tem unlimited supply de algo?**
   - Sim → Unbounded Knapsack / Coin Change

4. **É sobre subsequência/substring?**
   - Subsequência → LIS/LCS
   - Substring → Diferente (sliding window talvez)

5. **Tem estados bem definidos?**
   - Sim → State Machine DP

6. **É sobre intervalos?**
   - Sim → Interval DP

---

## 📊 Complexidade Típica

| Padrão | Tempo | Espaço | Otimizável? |
|--------|-------|--------|-------------|
| 1D Linear | O(n) | O(n) | ✅ para O(1) |
| House Robber | O(n) | O(n) | ✅ para O(1) |
| Coin Change | O(n×m) | O(n) | ❌ |
| LIS | O(n²) | O(n) | ✅ para O(n log n) |
| 2D Grid | O(m×n) | O(m×n) | ✅ para O(n) |
| LCS | O(m×n) | O(m×n) | ✅ para O(min(m,n)) |
| Knapsack | O(n×W) | O(n×W) | ✅ para O(W) |
| Interval | O(n³) | O(n²) | ❌ |

---

## 💡 Dicas Gerais

### Para Resolver Qualquer DP:

1. **Identifique o padrão** usando as perguntas acima
2. **Defina o estado:** `dp[i]` significa o que?
3. **Escreva a recorrência:** `dp[i] = function_of(dp[i-1], ...)`
4. **Identifique base cases:** `dp[0] = ?`
5. **Determine a ordem:** bottom-up ou top-down?
6. **Otimize espaço:** se possível

### Armadilhas Comuns:

- ❌ Não definir bem o que `dp[i]` representa
- ❌ Esquecer base cases
- ❌ Ordem errada de iteração (2D DP)
- ❌ Off-by-one errors
- ❌ Não considerar edge cases (array vazio, etc)

---

**Última atualização:** Em construção durante Semana 4
