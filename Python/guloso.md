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

```py
# quantidade de fornecedores e demanda
n, d = map(int, input().split())
# custo total da compra
custo = 0
# lista de fornecedores, cada um com seu preço e estoque
fornecedores = [{'preco': 0, 'estoque': 0} for _ in range(n)]

# lemos os preços e estoques de cada fornecedor
for i in range(n):
    p, e = map(float, input().split())
    fornecedores[i]['preco'] = p
    fornecedores[i]['estoque'] = e

# ordenamos os fornecedores pelo preço, isso custa O(n log n)
fornecedores.sort(key=lambda x: x['preco'])

# compramos o estoque de cada fornecedor até atingir a demanda
# isso custa O(n)
for i in range(n):
    atual = fornecedores[i]
    if d >= atual['estoque']:
        d -= atual['estoque']
        custo += atual['preco'] * atual['estoque']
    else:
        custo += atual['preco'] * d
        d = 0
        break

# se não conseguimos comprar a demanda, imprimimos 'Impossivel'
if d:
    print('Impossivel')
else:
    print(f'{custo:.2f}')

# Complexidade: O(n log n)
```

## 🤔 Por que funciona?

A ideia de um algoritmo guloso é sempre escolher a opção que parecer ideal, sem se preocupar com as consequências dessa ação.

No caso do exemplo, a opção ideal é sempre comprar do fornecedor mais barato, pois assim gastamos menos dinheiro.

## Exercícios

- Exercício [2387](https://www.beecrowd.com.br/judge/pt/problems/view/2387) do Beecrowd, que caiu na OBI 2010, esse exercício é um ótimo exemplo de um problema que pode ser resolvido com um algoritmo guloso.
