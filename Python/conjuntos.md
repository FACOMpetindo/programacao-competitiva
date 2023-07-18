# Conjuntos

Conjuntos são uma ferramenta muito útil em programação competitiva, a ideia básica de um conjunto é uma lista que não contém elementos repetidos, ou seja, se você tentar adicionar um elemento que já está no conjunto, ele não será adicionado.

Conjuntos são não ordenados, ou seja, não é possível acessar o elemento de um conjunto pelo seu índice, porém é possível iterar sobre os elementos de um conjunto e verificar se um valor está presente em um conjunto.

Também não é possível alterar o valor de um elemento de um conjunto, porém é possível adicionar e remover elementos de um conjunto.

## Criando um conjunto

Podemos criar um conjunto de duas maneiras diferentes:

```py
conjunto = {1, 2, 3, 4, 5}
conjunto = set([1, 2, 3, 4, 5])
```

A diferença entre os dois métodos é que o primeiro é mais rápido, porém o segundo é mais flexível, pois podemos criar um conjunto a partir de qualquer iterável, como uma lista, uma string, um dicionário, etc.

Em programação competitiva, acabamos usando quase que exclusivamente a segunda maneira, pois é muito comum que precisemos criar um conjunto a partir de uma lista.

## Manipulando seus elementos

Se você quer adicionar um único elemento ao conjunto, você pode usar o método `add`:

```py
conjunto = {1, 2, 3, 4, 5}
conjunto.add(6)
print(conjunto) # {1, 2, 3, 4, 5, 6}
```

Caso você queira adicionar todos os valores de um iterável, ou mais de um valor ao conjunto, você pode usar o método `update`:

```py
conjunto = {1, 2, 3, 4, 5}
conjunto.update([6, 7, 8])
print(conjunto) # {1, 2, 3, 4, 5, 6, 7, 8}
```

Para remover um elemento do conjunto, você pode usar o método `remove`:

```py
conjunto = {1, 2, 3, 4, 5}
conjunto.remove(3)
print(conjunto) # {1, 2, 4, 5}
```

Caso você não tenha certeza se o elemento está presente no conjunto, você pode usar o método `discard`, que não gera um erro caso o elemento não esteja presente no conjunto:

```py
conjunto = {1, 2, 3, 4, 5}
conjunto.discard(3)
print(conjunto) # {1, 2, 4, 5}
```

Lembrando que os conjuntos não são ordenados, então não é possível remover o primeiro elemento do conjunto por exemplo, assim como não é possível acessar o elemento de um conjunto pelo seu índice.

Para acessar os elementos de um conjunto, você pode iterar sobre ele:

```py
conjunto = {1, 2, 3, 4, 5}
for elemento in conjunto:
    print(elemento)
```

ou você pode verificar se um elemento está presente no conjunto:

```py
conjunto = {1, 2, 3, 4, 5}
if 3 in conjunto:
    print('3 está presente no conjunto')
```

Essa é uma das grandes vantagens do conjunto em relação a lista, a verificação de pertencimento é muito mais rápida em um conjunto do que em uma lista, pois em um conjunto essa verificação é feita em tempo constante, enquanto em uma lista essa verificação é feita em tempo linear.

## Operações com conjuntos

Assim como podemos fazer operações com números, como soma, subtração, multiplicação, etc, podemos fazer operações com conjuntos, como união, interseção, diferença, etc.

Para fazer essas operações, podemos usar os métodos `union`, `intersection`, `difference`, entre outros.

O método `union` retorna a união de dois conjuntos, ou seja, um conjunto que contém todos os elementos dos dois conjuntos:

```py
conjunto1 = {1, 2, 3, 4, 5}
conjunto2 = {4, 5, 6, 7, 8}
print(conjunto1.union(conjunto2)) # {1, 2, 3, 4, 5, 6, 7, 8}
```

O método `intersection` retorna a interseção de dois conjuntos, ou seja, um conjunto que contém apenas os elementos que estão presentes nos dois conjuntos:

```py
conjunto1 = {1, 2, 3, 4, 5}
conjunto2 = {4, 5, 6, 7, 8}
print(conjunto1.intersection(conjunto2)) # {4, 5}
```

O método `difference` retorna a diferença entre dois conjuntos, ou seja, um conjunto que contém apenas os elementos que estão presentes no primeiro conjunto, mas não estão presentes no segundo conjunto:

```py
conjunto1 = {1, 2, 3, 4, 5}
conjunto2 = {4, 5, 6, 7, 8}
print(conjunto1.difference(conjunto2)) # {1, 2, 3}
```

Existem muitos outros métodos úteis para conjuntos, como `issubset`, `issuperset`, `symmetric_difference`, etc, um bom local para conferir todos os métodos é a [W3Schools](https://www.w3schools.com/python/python_sets_methods.asp).

## Exercícios

- Exercício [1581](https://www.beecrowd.com.br/judge/pt/problems/view/1581) do Beecrowd, esse é um exercício que é resolvido facilmente com conjuntos.

- Exercício [2322](https://www.beecrowd.com.br/judge/pt/problems/view/2322) do Beecrowd, que caiu na OBI 2007, esse é um exercício simples que serve para treinar o uso de conjuntos.

- Exercício [2410](https://www.beecrowd.com.br/judge/pt/problems/view/2410) do Beecrowd, que caiu na OBI 2012, esse exercício é ótimo para mostrar a diferença de tempo entre a verificação de pertencimento em um conjunto e em uma lista.

- Exercício [2469](https://www.beecrowd.com.br/judge/pt/problems/view/2469) do Beecrowd, que caiu na OBI 2014, esse exercício pode ser resolvido de várias maneiras, mas uma das mais simples é usando um conjunto e uma lista.

- Exercício [1248](https://www.beecrowd.com.br/judge/pt/problems/view/1248) do Beecrowd, esse exercício é mais complicado mas é um ótimo treino para as operações com conjuntos.
