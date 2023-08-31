# Busca binária

A busca binária é um algoritmo de busca que utiliza a técnica de divisão e conquista. Ela é utilizada para buscar um elemento em um vetor ordenado.

A busca binária é um algoritmo de complexidade O(log n), ou seja, ele é muito mais rápido que uma busca linear, que tem complexidade O(n).

## 🤷 Como funciona?

Digamos que você tenha um vetor de números inteiros ordenados, e queira buscar o número 7.

```cpp
int vetor[10] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
```

O algoritmo da busca binária funciona da seguinte forma:

1. Verifica o elemento do meio do vetor
2. Se o elemento do meio for o que você está procurando, retorna o índice dele
3. Se o elemento do meio for maior que o que você está procurando, repete o processo na primeira metade do vetor
4. Caso o elemento do meio for menor que o que você está procurando, repete o processo na segunda metade do vetor

Vamos ver um exemplo:

```cpp
int vetor[10] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

// O elemento do meio é o 5
// 5 é menor que 7, então vamos procurar na segunda metade do vetor
// [6, 7, 8, 9, 10]

// O elemento do meio é o 8
// 8 é maior que 7, então vamos procurar na primeira metade do vetor
// [6, 7]

// O elemento do meio é o 7
// 7 é o que estamos procurando, então retornamos o índice dele
```

## 🤓 Implementação

```cpp
int busca_binaria(int vetor[], int elemento) {
    int inicio = 0;
    int fim = sizeof(vetor) / sizeof(vetor[0]) - 1;

    while (inicio <= fim) {
        int meio = (inicio + fim) / 2;

        if (vetor[meio] == elemento) {
            return meio;
        } else if (vetor[meio] > elemento) {
            fim = meio - 1;
        } else {
            inicio = meio + 1;
        }
    }

    return -1;
}

int main() {
    int vetor[10] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
    int elemento = 2;

    cout << busca_binaria(vetor, elemento) << endl;
    // 1 (índice do elemento)
}
```

## 🤔 Observações

É importante notar que a busca binária só funciona pois o vetor está ordenado. Caso o vetor não esteja ordenado, o algoritmo não funciona.
