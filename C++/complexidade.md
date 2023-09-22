# Complexidade de Algoritmos

## 📚 Introdução

Antes de começarmos a estudar algoritmos, precisamos entender complexidade de tempo e de espaço.

## ⏲️ Complexidade de tempo

A complexidade de tempo de um algoritmo é a quantidade de tempo que ele leva para executar, em função do tamanho da entrada.

Por exemplo, considere o seguinte algoritmo:

```cpp
int soma(int n) {
    int soma = 0;
    for (int i = 0; i < n; i++) {
        soma += i;
    }
    return soma;
}
```

Esse algoritmo recebe um número `n` e retorna a soma de todos os números de `0` até `n - 1`.

Por exemplo, se `n = 5`, o algoritmo retorna `0 + 1 + 2 + 3 + 4 = 10`.

A complexidade de tempo desse algoritmo é `O(n)`, pois ele executa `n` operações, uma para cada número de `0` até `n - 1`.

Chamamos essa notação de **Big O**, ela representa o pior caso de um algoritmo, ou seja, a quantidade máxima de operações que um algoritmo pode executar.

Vejamos outro exemplo:

```cpp
int soma(int n) {
    int soma = 0;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            soma += i + j;
        }
    }
    return soma;
}
```

Esse algoritmo também recebe um número `n` porém adicionamos um laço de repetição a mais.

Por exemplo, se `n = 3` o algoritmo retorna `(0 + 0) + (0 + 1) + (0 + 2) + (1 + 0) + (1 + 1) + (1 + 2) + (2 + 0) + (2 + 1) + (2 + 2) = 18`.

Podemos perceber então que a complexidade desse algoritmo é bem maior do que a do algoritmo anterior, isso se dá pois cada número de `0` até `n - 1` é somado com cada número de `0` até `n - 1`, isso nos dá `n * n` operações.

A complexidade de tempo desse algoritmo é `O(n^2)`.

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

Ao longo da nossa jornada, vamos estudar algoritmos que possuem complexidades de tempo diferentes.

## 📈 Complexidade de espaço

A complexidade de espaço de um algoritmo é a quantidade de espaço que ele ocupa na memória, em função do tamanho da entrada.

Por exemplo, considere o seguinte algoritmo:

```cpp
int soma(int n) {
    vetor<int> numeros(n);
    int soma = 0;
    for (int i = 0; i < n; i++) {
        soma += i;
    }
    return soma;
}
```

Esse algoritmo recebe um número `n` e retorna a soma de todos os números de `0` até `n - 1`, usando um vetor para armazenar os números.

A complexidade de espaço desse algoritmo é `O(n)`, pois ele ocupa `n` posições na memória, uma para cada número de `0` até `n - 1`.

Vejamos outro exemplo:

```cpp
int soma(int n) {
    vetor<vetor<int>> numeros(n, vetor<int>(n));
    int soma = 0;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            soma += i + j;
        }
    }
    return soma;
}
```

Esse algoritmo também recebe um número `n` e retorna a soma de todos os números de `0` até `n - 1`, porém usamos uma matriz para armazenar os números.

Isso nos dá uma complexidade de espaço de `O(n^2)`, pois ele ocupa `n * n` posições na memória, cada número de `0` até `n - 1` é armazenado `n - 1` vezes.

No geral, a complexidade de espaço de um algoritmo é bem menos importante do que a complexidade de tempo, nas competições e na maioria dos casos, não precisamos nos preocupar com ela, pois temos memória muito maior do que o necessário.
