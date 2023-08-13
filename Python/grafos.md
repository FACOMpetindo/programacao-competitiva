# Grafos

Um grafo é uma estrutura que consiste em um conjunto de pontos, chamados de vértices, e um conjunto de linhas que conectam esses vértices, chamadas de arestas. Em outras palavras, um grafo é uma representação visual de objetos (vértices) e suas conexões (arestas).

Essa estrutura é usada para modelar relações entre diferentes elementos, como redes de computadores, mapas de estradas, redes sociais e muito mais. Em um grafo, os vértices representam os pontos e as arestas representam as ligações entre esses pontos.

![Grafo](https://www.revista-programar.info/wp-content/uploads/2007/09/grafo-exemplo-1.gif)

Existem diversos tipos de grafos, sendo os mais comuns:

- **Grafo direcionado**: um grafo onde as arestas possuem uma direção, ou seja, uma aresta do vértice `a` para o vértice `b` não implica que existe uma aresta do vértice `b` para o vértice `a`.
- **Grafo não direcionado**: um grafo onde as arestas não possuem uma direção, ou seja, uma aresta do vértice `a` para o vértice `b` implica que existe uma aresta do vértice `b` para o vértice `a`.

## 🔗 Representação de grafos

Uma ótima forma de representar grafos em python é usando listas de adjacência. Uma lista de adjacência é uma lista onde cada elemento representa um vértice e contém uma lista com os vértices adjacentes a ele.

O código fica mais ou menos assim:

```py
n = 5 # número de vértices
graph: {i: set() for i in range(1, n)} # grafo com uma lista de adjacência para cada vértice

# estabelecemos um caminho de mão dupla entre os vértices 1 e 2
graph[1].add(2)
graph[2].add(1)

# estabelecemos um caminho de mão única do vértice 3 para o vértice 4
graph[3].add(4)
```

### 🧮 Busca em largura

A busca em largura (BFS - Breadth First Search) é um algoritmo de busca em grafos que explora os vértices de um grafo em camadas.

O algoritmo funciona da seguinte forma:

- Começamos a busca em um vértice inicial `s`, colocando-o em uma fila.
- Enquanto a fila não estiver vazia, retiramos um vértice da fila e exploramos todos os vértices adjacentes a ele.
- Se um vértice adjacente não foi visitado ainda, colocamos ele na fila e marcamos como visitado.

O algoritmo termina quando não há mais vértices na fila.

```py
import collections

def bfs(s):
    fila = collections.deque([s])
    visitado = [False] * n
    visitado[s] = True

    while fila:
        vertice = fila.popleft()
        for vizinho in graph[vertice]:
            if vizinho not in visitado:
                visitado[vertice] = True
                fila.append(vizinho)
```

### 🧮 Busca em profundidade

A busca em profundidade (DFS - Depth First Search) é um algoritmo de busca em grafos que explora o máximo possível de um grafo antes de voltar.

O algoritmo funciona da seguinte forma:

- Começamos a busca em um vértice inicial `s`, marcando-o como visitado.
- Para cada vértice adjacente a `s`, se ele não foi visitado ainda, visitamos ele e repetimos o processo recursivamente.

O algoritmo termina quando não há mais vértices adjacentes a `s` que não foram visitados ainda.

```py
def dfs(s):
    visitado[s] = True

    for v in adj[s]:
        if not visitado[v]:
            dfs(v)
```

## Exercícios

- Exercício [1445](https://www.beecrowd.com.br/judge/pt/problems/view/1445) do Beecrowd, esse é um exercício que pode ser resolvido com o algoritmo de busca em largura.

- Exercício [2412](https://www.beecrowd.com.br/judge/pt/problems/view/2412) do Beecrowd, esse é um pouco mais complicado pois você precisa descobrir quais vértices se conectam com quais.
