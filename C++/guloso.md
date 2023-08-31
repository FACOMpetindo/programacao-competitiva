# Algoritmo guloso

É uma estratégia para resolver desafios de programação muito útil, a ideia de um algoritmo guloso é sempre escolher a opção que parecer ideal, sem se preocupar com as consequências dessa ação.

Algoritmos gulosos são muito úteis para resolver problemas de otimização, onde queremos maximizar ou minimizar alguma coisa.

## 🤷 Como funciona?

Imagine que você é o dono de um posts de gasolina e no final do mês tem que repor seu estoque.

Nesse dia, você recebe uma lista, com o número de fornecedores, a sua demanda, e o preço por litro de cada fornecedor e quantos litros eles tem para venda.

Você, como um bom dono de posto, quer satisfazer sua demanda, mas também quer gastar o mínimo possível.

Como você faria para resolver esse problema?

Uma solução possível seria:

1. Ordenar a lista de fornecedores pelo preço do litro
2. Comprar do fornecedor mais barato até que sua demanda seja satisfeita

Felizmente essa solução funciona e é eficiente, mas por que?

A resposta é simples, se você comprar do fornecedor mais barato, você vai gastar menos dinheiro, e se você comprar até que sua demanda seja satisfeita, você não vai gastar dinheiro a mais.

Este programa resume muito bem a ideia de um algoritmo guloso

Nesse caso, tenho que escolher de quais fornecedores comprar, então ordeno as opções pelo preço, pois o melhor fornecedor
é o mais barato, e vou comprando sempre do melhor até atingir a demanda necessária.

O código abaixo mostra uma implementação desse algoritmo em python:

```cpp
#include <iostream>
#include <algorithm>

#define MAXN 100100

using namespace std;

struct gas {
  double preco, estoq; 
}; // declaro a struct gas

bool compara(gas x, gas y) { //Cria a função para comparar tipo gas
  return x.preco < y.preco; 
} 

gas forn[MAXN]; // crio um array de gas de nome "forn" para representar a lista

// declaro as variáveis que vou usar
int n;
double d, custo;

int main() {
  cin >> n >> d;  // leio os valores de n e d

  // leio o preço e o estoque de cada fornecedor
  for (int i=1; i<=n; i++) {
    cin >> forn[i].preco >> forn[i].estoq;
  }

  // ordeno o veotor de gas
  sort(forn+1, forn+n+1, compara);

  // percorro o vetor
  for (int i=1; i<=n; i++) {
    // o fornecedor davez será o que estou olhando no vetor, no momento
    gas davez=forn[i];

    // se todo o seu estoque não consegue preencher o que ainda preciso
    if (davez.estoq < d){
      custo+=davez.estoq*davez.preco; // somo a custo o valor de comprar todo o estoque
      d-=davez.estoq; // e subtraio de d o litros que comprei
    }
    // caso contrário, ou seja, dá pra encher tudo só com esse fornecedor
    else {
      custo+=d*davez.preco; // somo  acusto o valor de comprar o que preciso
      d=0; // zero a quantidade que a inda falta comprar
      break; // e paro de percorrer o vetor, pois já comprei o que precisava
    }
  }

  // se o loop acabar e ainda houver alguma quantidade em d
  if (d) {
    cout << "Impossivel\n"; // então não foi possível comprar tudo o que precisava
  }
  // caso contrário, foi possível
  else{
    cout.precision(2);
    cout << fixed << custo << "\n"; // e imprimo o valor gasto na compra
  }
  return 0;
}
```

## 🤔 Por que funciona?

A ideia de um algoritmo guloso é sempre escolher a opção que parecer ideal, sem se preocupar com as consequências dessa ação.

No caso do exemplo, a opção ideal é sempre comprar do fornecedor mais barato, pois assim gastamos menos dinheiro.

## Exercícios

- Exercício [2387](https://www.beecrowd.com.br/judge/pt/problems/view/2387) do Beecrowd, que caiu na OBI 2010, esse exercício é um ótimo exemplo de um problema que pode ser resolvido com um algoritmo guloso.
