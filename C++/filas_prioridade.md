# Filas de prioridade

## 📚 Introdução

No artigo anterior vimos como implementar filas e pilhas em C++, agora veremos sobre filas de prioridade.

A característica que difere uma fila de prioridade de uma fila comum é que os elementos são retirados da fila de acordo com sua prioridade, e não necessariamente na ordem em que foram adicionados.

## 📝 Implementação

### 📋 Inicializando uma fila de prioridade

Para inicializar uma fila de prioridade, basta importar a biblioteca heapq e usar a função `heapify` para inicializar uma lista como uma fila de prioridade.

```cpp
#include <iostream>
#include <queue>

using namespace std;

int main() {
    priority_queue<int> fila;

    fila.push(5);
    fila.push(3);
    fila.push(1);
    fila.push(4);
    fila.push(2);

    cout << fila.top() << "\n"; // 5

    return 0;
}
```

Perceba a saída do print, os elementos não estão na ordem em que foram adicionados, nem em ordem crescente, e nem decrescente! O que está acontecendo aqui?

A função `heapify` faz com que nossa lista vire uma fila de prioridade, essa estrutura garante que o próximo elemento a ser retirado da fila será o menor elemento da lista, ou seja, o elemento com maior prioridade (nesse caso, pelo menos).

Ela não garante que a lista esteja ordenada, mas sim que o próximo elemento a ser retirado será o menor elemento da lista.

### 📋 Adicionando elementos à fila de prioridade

Podemos usar a função `heappush` para adicionar elementos à fila de prioridade e a função `heappop` para remover elementos da fila de prioridade.

```cpp
#include <iostream>
#include <queue>

using namespace std;

int main() {
    priority_queue<int> fila;

    fila.push(5);
    fila.push(3);
    fila.push(1);
    fila.push(4);
    fila.push(2);

    // Adiciona um elemento
    fila.push(6);

    // Remove o elemento com maior prioridade
    cout << fila.top() << "\n"; // 6
    fila.pop();

    cout << fila.top() << "\n"; // 5

    return 0;
}
```

Sempre que usamos a função `heappush` e `heappop` na nossa fila de prioridade, a função `heapify` é chamada internamente para garantir sua característica.

### 📋 Exemplo de uso

Imagine que você é um treinador de pokemons e após capturar vários pokemons você está finalmente pronto para enfrentar o ginásio da cidade, quando você vai batalhar no ginásio você que sempre usar seus pokemons mais fortes.

Sabendo disso, será dado uma sequencia de operações alternadas entre capturar um pokemon ou batalhar em um ginásio, quando uma batalha em um ginásio ocorre você usará sempre seu pokemon mais forte e após a batalha, seu pokemon ficará com metade do poder que tinha antes da batalha.

Em cada comando de batalha, imprima na tela o pokemon selecionado para a batalha.

```cpp
#include <iostream>
#include <queue>
#include <string>

using namespace std;

int main() {
    priority_queue<pair<int, string>> fila;

    char op;

    while (cin >> op) {
        if (op == 'C') {
            string nome;
            int poder;

            cin >> nome >> poder;

            fila.push({poder, nome});
        }
        else if (op == 'B') {
            auto pokemon = fila.top();
            fila.pop();

            cout << pokemon.second << "\n";

            fila.push({pokemon.first / 2, pokemon.second});
        }
    }

    return 0;
}
```

O código acima adiciona uma tupla com o poder do pokemon e seu nome na fila de prioridade, porém como queremos sempre usar o pokemon mais forte, adicionamos o poder do pokemon como negativo, assim o pokemon com maior poder será o menor elemento da fila.

Quando uma batalha ocorre, removemos o pokemon mais forte da fila e imprimimos seu nome, após isso adicionamos o pokemon de volta na fila com seu novo poder.

Esse exemplo mostra o poder de uma fila de prioridade, em exercícios que precisamos priorizar tarefas, ou escolher elementos com base em certas características, uma fila de prioridade é uma escolha excelente!

## 🧑‍🏫 Exercícios

- Exercício [2958](https://www.beecrowd.com.br/judge/pt/problems/view/2958) do Beecrowd, esse problema se trata em priorizar tarefas, ótimo pra se resolver com filas de prioridade!
