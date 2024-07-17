# Conjuntos

## 📚 Introdução

Conjuntos são uma ferramenta muito útil em programação competitiva, a ideia básica de um conjunto é uma lista que não contém elementos repetidos, ou seja, se você tentar adicionar um elemento que já está no conjunto, ele não será adicionado.

Conjuntos são não ordenados, ou seja, não é possível acessar o elemento de um conjunto pelo seu índice, porém é possível iterar sobre os elementos de um conjunto e verificar se um valor está presente em um conjunto.

Também não é possível alterar o valor de um elemento de um conjunto, porém é possível adicionar e remover elementos de um conjunto.

## 🔨 Criando um conjunto

Podemos criar um conjunto de duas maneiras diferentes:

```py
conjunto = {1, 2, 3, 4, 5}
conjunto = set([1, 2, 3, 4, 5])
```

A diferença entre os dois métodos é que o primeiro é mais rápido, porém o segundo é mais flexível, pois podemos criar um conjunto a partir de qualquer iterável, como uma lista, uma string, um dicionário, etc.

Em programação competitiva, acabamos usando quase que exclusivamente a segunda maneira, pois é muito comum que precisemos criar um conjunto a partir de uma lista.

## 🗃️ Manipulando seus elementos

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

Essa é uma das grandes vantagens do conjunto em relação a lista, a verificação de pertencimento é muito mais rápida em um conjunto do que em uma lista, tendo uma complexidade de O(1) em um conjunto e O(n) em uma lista.

## ⚙️ Operações com conjuntos

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

## 🚀 Demonstração

Vamos analisar o exercício 2410 do Beecrowd que caiu na OBI 2012, o enunciado do exercício é o seguinte:

<figure><img src="../assets/2410.png" alt="Exercício 2410 do Beecrowd"><figcaption></figcaption></figure>

Primeiramente, esse exercício pode parecer muito simples de resolver! Simplesmente lemos as entradas, colocamos o número do aluno em uma lista se ele não estava lá, e no final verificamos o tamanho da lista, certo?

Não exatamente, o problema é que a lista é uma estrutura de dados muito lenta para esse problema, como o enunciado nos diz que podemos ter até 10ˆ5 alunos, temos que olhar na lista 10ˆ5 vezes (pois você pode ter certeza que um dos casos de teste terá o número máximo de alunos), e essa verificação tem complexidade O(n), ou seja, a solução terá complexidade O(nˆ2), o que é muito lento para esse problema.

Mas esquecemos um detalhe importante, o enunciado nos diz que os números dos alunos são únicos, ou seja, não temos números repetidos, e isso é um indicativo claro de que devemos usar um conjunto, já que como discutimos, ele não aceita números repetidos, podemos simplesmente adicionar (e a operação de adição custa O(1)) cada aluno a um conjunto e usar a função `len()` para ver quantos alunos foram pra aula!

```py
import sys
presente = set()

for i in range(int(sys.stdin.readline())):
    presente.add(sys.stdin.readline())

sys.stdout.write(f'{len(presente)}\n')
```

## 🧑‍🏫 Exercícios

- Exercício [1581](https://www.beecrowd.com.br/judge/pt/problems/view/1581) do Beecrowd, esse é um exercício que é resolvido facilmente com conjuntos.

- Exercício [2322](https://www.beecrowd.com.br/judge/pt/problems/view/2322) do Beecrowd, que caiu na OBI 2007, esse é um exercício simples que serve para treinar o uso de conjuntos.

- Exercício [2410](https://www.beecrowd.com.br/judge/pt/problems/view/2410) do Beecrowd, que caiu na OBI 2012, esse exercício é ótimo para mostrar a diferença de tempo entre a verificação de pertencimento em um conjunto e em uma lista.

- Exercício [2469](https://www.beecrowd.com.br/judge/pt/problems/view/2469) do Beecrowd, que caiu na OBI 2014, esse exercício pode ser resolvido de várias maneiras, mas uma das mais simples é usando um conjunto e uma lista.

- Exercício [1248](https://www.beecrowd.com.br/judge/pt/problems/view/1248) do Beecrowd, esse exercício é mais complicado mas é um ótimo treino para as operações com conjuntos.
