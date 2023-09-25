# Crivo de Eratóstenes

## 📚 Introdução

O crivo de Eratóstenes é um algoritmo que permite encontrar todos os números primos até um determinado número `n`.

Pense no seguinte problema, dados N e Q, teremos Q números inteiros menores que N, e devemos responder para cada um deles se ele é primo. Como resolveríamos esse problema?

Uma solução ingênua seria testar todos os números de 2 até N-1 para cada um dos Q números, da seguinte forma:

```py
def eh_primo(n):
    for i in range(2, n):
        if n % i == 0:
            return False
    return True
```

Esse algoritmo funciona, mas ele é muito lento, pois para cada um dos Q números, ele testa todos os números de 2 até N-1, o que resulta em uma complexidade de `O(Q*N)`.

Podemos melhorar esse algoritmo, se percebermos que não precisamos testar todos os números de 2 até N-1, pois se um número `n` não for divisível por nenhum número de 2 até `n-1`, então ele não é divisível por nenhum número de 2 até `n/2`, pois se ele fosse divisível por um número maior que `n/2`, ele também seria divisível por um número menor que `n/2`.

Então podemos melhorar o algoritmo da seguinte forma:

```py
def eh_primo(n):
    for i in range(2, n//2):
        if n % i == 0:
            return False
    return True
```

Agora o algoritmo está um pouco mais rápido, mas ainda é lento, pois para cada um dos Q números, ele testa todos os números de 2 até `n/2`, o que resulta em uma complexidade de `O(Q*N/2)`.

Podemos melhorar ainda mais esse algoritmo, se percebermos que não precisamos testar todos os números de 2 até `n/2`, podemos testar apenas os números de 2 até a raiz quadrada de n + 1, essa é uma propriedade bem legal da matemática que nos permite reduzir a complexidade ainda mais.

O código ficaria da seguinte forma:

```py
def eh_primo(n):
    for i in range(2, int(n**0.5)+1): #também podemos usar math.sqrt(n)
        if n % i == 0:
            return False
    return True
```

Agora o algoritmo está bem mais rápido, com uma complexidade de `O(Q*sqrt(N))`, porém para um número Q muito grande, esse código pode demorar muito para responder para todos os N números.

Estamos esquecendo de algo muito importante, se um dado número é primo, então duas vezes esse número não é primo, 3 vezes esse número não é primo e assim por diante, podemos visualizar isso na animação abaixo:

<p align='center'>
<img src='../assets/crivo.gif' width=400>
</p>

Podemos aplicar isso da seguinte forma, poderíamos usar um vetor e percorrer todos os números de 2 a N, se ele estiver marcado, o número é um primo, então desmarcamos todos os múltiplos desse primo menores que N  

No final, só consultamos o vetor para ver se dado número é primo.

O código ficaria da seguinte forma:

```py
def crivo(n):
    primos = [True for _ in range(n+1)]
    primos[0] = False  # 0 não é primo
    primos[1] = False  # 1 não é primo
    for i in range(2, n+1):
        if primos[i]:  # se i é primo
            for j in range(i*i, n+1, i):  # marca todos os múltiplos de i como não primos
                primos[j] = False
    return primos
```

Essa solução tem uma complexidade de `O(N * log(log(N)))`, sendo assim bastante rápida.

Entretanto, lembre-se que criamos uma lista com o tamanho de N, então em casos com valores pequenos ou que a memória é crítica, a primeira solução pode ser preferível.
