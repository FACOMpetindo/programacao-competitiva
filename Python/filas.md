# Filas

## 📚 Introdução

Uma fila é uma estrutura de dados que segue o princípio FIFO (First In, First Out), ou seja, o primeiro elemento a entrar é o primeiro a sair.

Filas são muito utilizadas em programação competitiva, pois são uma forma simples de organizar uma lista de elementos que precisam ser processados e mais rápidas que uma lista com o mesmo propósito.

## 📝 Implementação

### 📋 Implementação usando listas

Para implementarmos uma fila usando listas, podemos usar a função `append` para adicionar elementos ao final da fila e a função `pop` para remover elementos do início da fila. Porém essa implementação é lenta, pois inserir ou remover um elemento do início da fila requer que todos os outros elementos sejam deslocados, o que custa O(n) de tempo.

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

Filas em Python podem ser implementadas usando a classe deque da biblioteca padrão collections. 

É mais interessante usar deque sobre listas, pois deque fornece uma complexidade de tempo O(1) para operações de anexação e pop em comparação com a lista que fornece O(n) complexidade de tempo.

Deque é uma abreviação de Double Ended Queue (Fila de duas pontas), ou seja, uma fila que pode ser acessada tanto pelo início quanto pelo fim.

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

## 📝 Exercícios

- Exercício [1110](https://www.beecrowd.com.br/judge/pt/problems/view/1110) do Beecrowd, esse é um ótimo treino para filas e complexidade de tempo.
