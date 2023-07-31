# Inputs e outputs rápidos

Geralmente usaremos os métodos padrões de input e output do Python, porém, as vezes os exercícios requerem que façamos centenas ou mais de leituras e escritas, nesses casos, os métodos padrões custam muito tempo, então temos que usar métodos mais rápidos.

## 📥 Inputs

O método padrão de input do Python é o `input()`.

Quando queremos ler mais de um valor na mesma linha, podemos usar o `split()`.

```python
a, b = input().split()
```

Se quisermos ler uma lista de valores, podemos usar o `map()`.

```python
a, b = map(int, input().split())
```

O código acima lê dois valores inteiros na mesma linha.

Se precisarmos que os valores sejam armazenados em uma lista, podemos usar a coompreensão de listas.

```python
a = [int(x) for x in input().split()]
```

Esse métodos é mais lento que o `map()`, então só o use se for necessário.

Porém, o jeito mais rápido de ler valores em python é usando o `sys.stdin.readline()`.

```python
import sys

a, b = map(int, sys.stdin.readline().split())
vet = [int(x) for x in sys.stdin.readline().split()]
```

Temos que manter algumas coisas em mente ao usar o `sys.stdin.readline()`:

- Ele lê uma linha inteira, então se quisermos ler mais de um valor na mesma linha, temos que usar o `split()`.
- Ele lê uma string, então se quisermos ler um inteiro, temos que usar o `int()`.
- Ele lê o `\n` no final da linha, então se quisermos ler uma única linha, temos que usar o `.rstrip()`.

## 📤 Outputs

O método padrão de output do Python é o `print()`.

Porém, o jeito mais rápido de escrever valores em python é usando o `sys.stdout.write()`.

```python
import sys

sys.stdout.write(str(a) + '\n')
```

Assim como no `sys.stdin.readline()`, temos que manter algumas coisas em mente ao usar o `sys.stdout.write()`:

- Ele só aceita strings, então se quisermos escrever um inteiro, temos que usar o `str()` ou f-strings.
- Ele não coloca o `\n` automaticamente no final da linha, isso é importante pois os juízes de código não aceitaram a resposta se não tiver o `\n` no final da linha.

## Exercícios

Nenhum exercício listado aqui precisam de fast io, porém, eles são bons para treinar o uso do `sys.stdin.readline()` e do `sys.stdout.write()`, assim quando você encontrar um onde o tempo é um problema, usar esses métodos é um bom truque a se aplicar.

- Exercício [1248](https://www.beecrowd.com.br/judge/pt/problems/view/1248) do Beecrowd, que caiu na OBI 2012.

- Exercício [2408](https://www.beecrowd.com.br/judge/pt/problems/view/2408) do Beecrowd, que caiu na OBI 2012.

- Exercício [2420](https://www.beecrowd.com.br/judge/pt/problems/view/2420) do Beecrowd, que caiu na OBI 2012.

- Exercício [1410](https://www.beecrowd.com.br/judge/pt/problems/view/1410) do Beecrowd, que caiu na ACM/ICPC South America Contest 2007.

- Exercício [2770](https://www.beecrowd.com.br/judge/pt/problems/view/2770) do Beecrowd, que caiu na V Maratona Norte Mineira de Programação, não se assuste com o nível 7 desse exercício, mantenha a calma e leia o que se pede.
