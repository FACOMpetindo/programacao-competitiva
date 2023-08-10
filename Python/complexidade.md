# Complexidade de Algoritmos

Antes de começarmos a estudar algoritmos, precisamos entender complexidade de tempo e de espaço.

## ⏲️ Complexidade de tempo

A complexidade de tempo de um algoritmo é a quantidade de tempo que ele leva para executar, em função do tamanho da entrada.

Por exemplo, considere o seguinte algoritmo:

```py
def soma(n):
    soma = 0
    for i in range(n):
        soma += i
    return soma
```

Esse algoritmo recebe um número `n` e retorna a soma de todos os números de `0` até `n - 1`.

A complexidade de tempo desse algoritmo é `O(n)`, pois ele executa `n` operações, uma para cada número de `0` até `n - 1`.

Chamamos essa notação de **Big O**, ela representa o pior caso de um algoritmo, ou seja, a quantidade máxima de operações que um algoritmo pode executar.

Vejamos outro exemplo:

```py
def soma(n):
    soma = 0
    for i in range(n):
        for j in range(n):
            soma += i + j
    return soma
```

Esse algoritmo também recebe um número `n` e retorna a soma de todos os números de `0` até `n - 1`.

A complexidade de tempo desse algoritmo é `O(n^2)`, pois ele executa `n * n` operações, uma para cada par de números de `0` até `n - 1`.

## 📈 Complexidade de tempo de alguns algoritmos

Vejamos as complexidades mais comuns de algoritmos:

- **O(1)**: Constante
- **O(log n)**: Logarítmica
- **O(n)**: Linear
- **O(n log n)**: Linearítmica
- **O(n^2)**: Quadrática
- **O(n^3)**: Cúbica
- **O(2^n)**: Exponencial

É importante se atentar a complexidade de tempo de um algoritmo, pois ela pode ser a diferença entre um algoritmo que roda em 1 segundo e um que roda em 1 minuto, como podemos ver no gráfico abaixo:

<img alt="Complexity time graph" src="https://www.raebear.net/media/2017/12/jIGhf.png" />

Ao longo desse repositório, vamos estudar algoritmos que possuem complexidades de tempo diferentes.

## 📈 Complexidade de espaço

A complexidade de espaço de um algoritmo é a quantidade de espaço que ele ocupa na memória, em função do tamanho da entrada.

Por exemplo, considere o seguinte algoritmo:

```py
def soma(n):
    numeros = [i for i in range(n)]
    soma = 0
    for i in numeros:
        soma += i
    return soma
```

Esse algoritmo recebe um número `n` e retorna a soma de todos os números de `0` até `n - 1`.

A complexidade de espaço desse algoritmo é `O(n)`, pois ele ocupa `n` posições na memória, uma para cada número de `0` até `n - 1`.

Vejamos outro exemplo:

```py
def soma(n):
    numeros = [[i for i in range(n)] for j in range(n)]
    soma = 0
    for i in numeros:
        for j in i:
            soma += j
    return soma
```

Esse algoritmo também recebe um número `n` e retorna a soma de todos os números de `0` até `n - 1`.

No entanto a complexidade de espaço desse algoritmo é `O(n^2)`, pois ele ocupa `n * n` posições na memória, uma para cada par de números de `0` até `n - 1`.

No geral a complexidade de espaço é negligenciada, pois a memória disponível é muito maior do que a quantidade de memória que um algoritmo ocupa, porém, conhecimento nunca é demais.
