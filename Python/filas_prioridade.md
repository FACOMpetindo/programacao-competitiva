# Filas de prioridade

## 📚 Introdução

Uma fila de prioridade em Python é implementada usando a biblioteca padrão heapq.

A propriedade dessa estrutura em Python é que cada elemento da fila tem uma prioridade associada a ele e o elemento com a maior prioridade é sempre removido primeiro.

Elementos com maior prioridade, são os menores elementos, então quando você insere um elemento na fila, ele é colocado em uma posição que mantém a fila ordenada.

## 📝 Implementação

### 📋 Inicializando uma fila de prioridade

Para inicializar uma fila de prioridade, basta importar a biblioteca heapq e usar a função `heapify` para inicializar uma lista como uma fila de prioridade.

```py
import heapq

fila = [5, 3, 1, 4, 2]

# Inicializa a fila de prioridade
heapq.heapify(fila)

print(fila)
```

### 📋 Adicionando elementos à fila de prioridade

Podemos usar a função `heappush` para adicionar elementos à fila de prioridade e a função `heappop` para remover elementos da fila de prioridade.

```py
import heapq

fila = [5, 3, 1, 4, 2]

# Inicializa a fila 
heapq.heapify(fila)

# Adiciona um elemento
heapq.heappush(fila, 6)

# Remove o elemento com maior prioridade
menor = heapq.heappop(fila)

print(fila)
```

### 📋 Exemplo de uso

Imagine que você é um treinador de pokemons e após capturar vários pokemons você está finalmente pronto para enfrentar o ginásio da cidade, quando você vai batalhar no ginásio você que sempre usar seus pokemons mais fortes.

Sabendo disso, será dado uma sequencia de operações alternadas entre capturar um pokemon ou batalhar em um ginásio, quando uma batalha em um ginásio ocorre você usará sempre seu pokemon mais forte e após a batalha, seu pokemon ficará com metade do poder que tinha antes da batalha.

Em cada comando de batalha, imprima na tela o pokemon selecionado para a batalha.

```py
import heapq

fila = heapq.heapify([])

while (op := input()):
    if op == 'C':
        nome, poder = input().split()
        heapq.heappush(fila, (-int(poder), nome))
    elif op == 'B':
        pokemon = heapq.heappop(fila)
        print(pokemon[1])
        heapq.heappush(fila, (pokemon[0] / 2, pokemon[1]))
```

O código acima adiciona uma tupla com o poder do pokemon e seu nome na fila de prioridade, porém como queremos sempre usar o pokemon mais forte, adicionamos o poder do pokemon como negativo, assim o pokemon com maior poder será o menor elemento da fila.

Quando uma batalha ocorre, removemos o pokemon mais forte da fila e imprimimos seu nome, após isso adicionamos o pokemon de volta na fila com seu novo poder.

## 📚 Leia mais

- [GeeksforGeeks - Heap Queue in Python](https://www.geeksforgeeks.org/heap-queue-or-heapq-in-python/)

## 🧑‍🏫 Exercícios

- Exercício [2958](https://www.beecrowd.com.br/judge/pt/problems/view/2958) do Beecrowd, esse problema se trata em priorizar tarefas, ótimo pra se resolver com filas de prioridade!
