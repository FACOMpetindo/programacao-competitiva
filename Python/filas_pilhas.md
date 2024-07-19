# Filas e Pilhas

## 📚 Introdução

Nesse artigo vamos falar sobre filas e pilhas, duas estruturas de dados muito importantes em programação competitiva, uma fila segue o princípio FIFO (First In, First Out) e uma pilha segue o princípio LIFO (Last In, First Out).

Imagine uma fila, assim como uma fila de banco, a primeira pessoa a chegar é a primeira a ser atendida, e uma pilha, assim como uma pilha de pratos, o último prato a ser colocado é o primeiro a ser retirado.

Usamos filas e pilhas para processar dados em certa ordem, podemos fazer o mesmo com uma lista, porém filas e pilhas são muito mais otimizadas para esses tipos de operações.

## 📝 Implementação

### 📋 Implementação usando listas

Para implementarmos uma fila usando listas, podemos usar a função `append` para adicionar elementos ao final da fila e a função e `pop(0)` para remover elementos do início da fila.

Simular uma pilha é bem semelhante, usamos `append` para adicionar elementos ao final da pilha e `pop` para remover elementos do final da pilha.

Porém essa implementação é lenta, pois inserir ou remover um elemento do início da fila requer que todos os outros elementos sejam deslocados, o que custa `O(n)` de tempo.

```py
# Inicializando uma fila vazia
queue = []

# Adicionando elementos à fila
queue.append('a')
queue.append('b')
queue.append('c')

print("Fila inicial:")
print(queue)

# Remove o primeiro elemento da fila
print("\nElementos removidos da fila:")
print(queue.pop(0))
print(queue.pop(0))
print(queue.pop(0))

print("\nFila após a remoção:")
print(queue)

# Descomentar print(queue.pop(0))
# vai causar um IndexError
# pois a fila está vazia
```

### 📋 Implementação usando deque

Essas estruturas podem ser implementadas de forma muito mais eficiente em Python usando a classe deque da biblioteca padrão collections.

É mais interessante usar deque sobre listas, pois deque fornece uma complexidade de tempo `O(1)` para operações de anexação e remoção!

Deque é uma abreviação de Double Ended Queue (Fila de duas pontas), ou seja, uma fila que pode ser acessada tanto pelo início quanto pelo fim, assim conseguimos usar a mesma estrutura para implementar tanto filas quanto pilhas.

```py
from collections import deque

fila = deque()

# Podemos adicionar elementos ao final da fila
fila.append('a')

# E também podemos adicionar elementos ao início da fila
fila.appendleft('b')

# Podemos remover elementos do final da fila e obter seu valor
final = fila.pop()

# E também podemos remover elementos do início da fila
inicio = fila.popleft()

# Podemos limpar a fila
fila.clear()
```

Para obtermos o comportamento FIFO, temos que adicionar de um lado e remover do outro, geralmente usamos `append` para adicionar elementos e `popleft` para remover elementos.

Se adicionarmos do mesmo lado que removemos, por exemplo, `append` e `pop` teremos um comportamento LIFO (Last In, First Out), que é o comportamento de uma pilha (stack), em algumas situações isso pode ser útil.

Mais para frente, estudaremos sobre grafos, e veremos que usar filas e pilhas conseguimos percorrer um grafo de maneiras diferentes, por enquanto, sempre que precisar percorrer sobre uma lista de elementos, pense em usar uma fila ou pilha!

## 🧑‍🏫 Exercícios

- Exercício [1110](https://www.beecrowd.com.br/judge/pt/problems/view/1110) do Beecrowd, esse é um ótimo treino para filas e complexidade de tempo.
