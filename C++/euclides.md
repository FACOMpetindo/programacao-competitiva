# Algoritmo de Euclides

O algoritmo de Euclides é um algoritmo que é usado para calcular o máximo divisor comum, assim como o mínimo múltiplo comum entre dois números inteiros.

## Máximo divisor comum

O máximo divisor comum entre dois números inteiros é o maior número inteiro que divide ambos os números.

Por exemplo, o máximo divisor comum entre 12 e 18 é 6, pois 6 é o maior número que divide 12 e 18.

Uma solução ingênua para calcular o máximo divisor comum entre dois números seria começar no maior número e ir decrementando até encontrar um número que divide ambos os números.

```cpp
int mdc(int a, int b) {
    for (int i = max(a, b); i > 0; i--) {
        if (a % i == 0 && b % i == 0) {
            return i;
        }
    }
}
```

O código acima funciona, mas é muito lento para números grandes.

O algoritmo de Euclides é muito mais rápido, pois ele utiliza a seguinte propriedade:

> Seja `a` e `b` dois números inteiros, com `a > b`. O máximo divisor comum entre `a` e `b` é igual ao máximo divisor comum entre `b` e `a % b`.

Ou seja, se `a` e `b` são dois números inteiros, com `a > b`, mdc(a,b) = mdc(b, a % b).

Ademais, usando o fato de que mdc(a,0) = a, aplicamos a propriedade anterior várias vezes, até que o segundo número seja 0, nesse momento retornamos a.

Por exemplo, para calcular o mdc entre 12 e 18 usando esse algoritmo, o passo a passo seria:

- mdc(18, 12) = mdc(12, 18 % 12) = mdc(12, 6)
- mdc(6, 12 % 6) = mdc(6, 0) = 6

O código em Python fica:

```cpp
int euclides(int a, int b) {
    if (b == 0) {
        return a;
    }
    return euclides(b, a % b);
}
```

## Mínimo múltiplo comum

O algoritmo de Euclides também pode ser usado para calcular o mínimo múltiplo comum entre dois números inteiros.

O mínimo múltiplo comum entre dois números inteiros é o menor número inteiro que é múltiplo de ambos os números.

Por exemplo, o mínimo múltiplo comum entre 12 e 18 é 36, pois 36 é o menor número que é múltiplo de 12 e 18.

Podemos usar a seguinte propriedade para calcular o mínimo múltiplo comum entre dois números inteiros:

> mmc(a,b) = a * b / mdc(a,b)

Ou seja, o mínimo múltiplo comum entre dois números inteiros é igual ao produto entre os dois números dividido pelo máximo divisor comum entre eles.

O código em Python fica:

```cpp
int mmc(int a, int b) {
    return a * b / euclides(a, b);
}
```
