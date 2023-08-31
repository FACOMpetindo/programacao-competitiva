# Manipulação de bits

## 📚 Introdução

Todos os dados que são armazenados em um computador são representados por bits, que são 0s e 1s. Por exemplo, o número 5 é representado por 101 em binário, e o número 7 é representado por 111.

## 📌 Operadores binários

### Operador `|`

O operador `|` é o operador de ou, ou OR. Ele retorna 1 se pelo menos um dos bits for 1, e 0 caso contrário.

| Operação | Resultado |
|:--------:|:---------:|
| 0 \| 0    | 0         |
| 0 \| 1    | 1         |
| 1 \| 0    | 1         |
| 1 \| 1    | 1         |

### Operador `^`

O operador `^` é o operador de ou exclusivo, ou XOR. Ele retorna 1 se os bits forem diferentes, e 0 se forem iguais.

| Operação | Resultado |
|:--------:|:---------:|
| 0 ^ 0    | 0         |
| 0 ^ 1    | 1         |
| 1 ^ 0    | 1         |
| 1 ^ 1    | 0         |

### Operador `&`

O operador `&` é o operador de e, ou AND. Ele retorna 1 se os dois bits forem 1, e 0 caso contrário.

| Operação | Resultado |
|:--------:|:---------:|
| 0 & 0    | 0         |
| 0 & 1    | 0         |
| 1 & 0    | 0         |
| 1 & 1    | 1         |

### Operador `~`

O operador `~` é o operador de negação, ou NOT. Ele inverte todos os bits.

| Operação | Resultado |
|:--------:|:---------:|
| ~0       | 1         |
| ~1       | 0         |

### Operador `<<`

O operador `<<` é o operador de deslocamento à esquerda. Ele desloca todos os bits para a esquerda, e preenche os bits vazios com 0.

| Operação | Resultado |
|:--------:|:---------:|
| 1 << 1   | 2         |
| 1 << 2   | 4         |
| 5 << 2   | 20        |

### Operador `>>`

O operador `>>` é o operador de deslocamento à direita. Ele desloca todos os bits para a direita, e preenche os bits vazios com 0.

| Operação | Resultado |
|:--------:|:---------:|
| 1 >> 1   | 0         |
| 4 >> 1   | 2         |
| 5 >> 2   | 1         |

## Checar se um dado bit está ligado

Para checar se um bit é 1, podemos usar o operador `&` com uma máscara que tenha apenas o bit que queremos checar como 1.

Por exemplo, para checar se o terceiro bit de 5 é 1, podemos fazer:

```cpp
bool is_set(int x, int i){
  bool ret = ((x&(1 << i)) != 0);
  return ret;
}
```

## Retornar o bit menos significativo

O negativo de um número é só trocar os bits do número e somar 1 a isso, dessa forma os `lsb` dos dois números são iguais, porém todos os bits maiores que o `lsb` deles serão diferentes,assim, basta retornamos o `and` dos bits entre o número e o negativo desse número.

```cpp
int lsb(int x){
  return x&-x;
}
```

## Contar o número de bits 1

Podemos usar a ideia do `lsb` para fazer esse cálculo mais rapidamente, usamos um loop, e enquanto o número for diferente de 0, subtraimos o `lsb` do número e adicionamos um a um contador, quando o loop termina retornamos o contador

```cpp
int count_bits(int x){
  int ret = 0;
  while(x != 0){
    ++ret;
    x -= x&-x;
  }
  return ret;
}
```

## Checar se um número é potência de 2

Se o númerno não for 0, vemos se ele tem algum bit em comum com seu antecessor, pois se ele for uma potência de 2, digamos 2**i, o único bit ligado será o i, enquanto seu antecessor tem todos os bits menores que i iguais a 1, assim o and deles será 0.

```cpp
bool is_power_of_two(int x){
  if(x == 0)  return 0;
  return ((x&(x - 1)) == 0);
}
```

## Bits necessários para representar um número

Podemos checar quantos bits são necessários para representar um número usando o operador `>>` e um loop, enquanto o número for diferente de 0, deslocamos ele para a direita e adicionamos 1 a um contador, quando o loop termina retornamos o contador.

```cpp
int number_of_bits(int number) {
  int count = 0;
  while (number > 0) {
    number >>= 1;
    count++;
  }
  return count;
}
```

## Ligar um bit

Para ligar um bit, basta usar o operador `|` com uma máscara que tenha apenas o bit que queremos ligar como 1.

Por exemplo, para ligar o terceiro bit de 5 como 1, podemos fazer:

```cpp
int x = 5;
x |= (1 << 2);
```

## Desligar um bit

Primeiro garantimos que o bit está ligado, depois ele recebe ele mesmo `xor` a potência de 2 do bit que queremos desligar.

Por exemplo, para desligar o terceiro bit de 5, podemos fazer:

```cpp
int x = 5;
x |= (1 << 2)
x ^= (1 << 2)
```

## Exercícios

- Exercício [2544](https://www.beecrowd.com.br/judge/pt/problems/view/2544) do Beecrowd, esse exercício pode ser resolvido de várias maneiras, mas saber manipular bits te faz ter menos dor de cabeça.

- Exercício [1026](https://www.beecrowd.com.br/judge/pt/problems/view/1026) do Beecrowd, também é um ótimo exercício para praticar manipulação de bits.
