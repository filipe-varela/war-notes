---
title: "Python & Kotlin"
date: 2021-12-17T15:34:52Z
---

Tanto como o Python como Kotlin têm bastante parecenças entre si, podendo ser necessário acrescentar um indicador ou chavetas para delimitar os blocos de código.
De seguida, mostra-se alguns exemplos de código que, quando executados, irão produzir o mesmo resultado em ambos os casos:

Python:
```python
# Declaração de variáveis
a = 1
b = 2
# Declaração de funções/métodos
def soma (val1, val2):
    return val1 + val2
# Mostrar o resultado
print(soma(a,b)) # a+b=3
```
Kotlin:
```kotlin
// Declaração de variáveis
var a : Int = 1

// É opcional indicar o seu tipo
var b = 2

// Declaração de funções/métodos
fun soma (val1:Int, val2:Int) : Int {
    return val1 + val2
}

println(soma(a,b)) // a+b=3
```

---

### Para `for`'s e `if`'s
Python:
```python
# for’s
for i in range(100):
    print(i)

# if’s
if (condition):
    # verdadeiro
else:
    # falso
```
Kotlin:
```kotlin
// for’s
for (i in 0..100) {
    println(i)
}

// if’s
if (condition) {
    // verdadeiro
} else {
    // falso
}
```

---

### Mapeamento de várias condições
Python prévio à versão [3.10](https://docs.python.org/3/whatsnew/3.10.html)
```python
valor = 0

if (valor==0):
    print("Zero")
elif (valor==1):
    valor += 1
elif (valor==2):
    do_something()
# ...
else:
    print("Outra qualquer")
```

Pyhton 3.10 (os highlights pelos vistos ainda não funcionam pois esta versão é bastante recente)
```python
valor = 0

match valor:
    case 0:
        print("Zero")
    case 1:
        valor += 1
    case 2:
        do_something()
    # ...
    case _:
        print("Outra qualquer")
```

Kotlin
```kotlin
// when’s
var valor = 0
when(valor) {
    0 -> println("Zero")
    1 -> valor.inc()
    2 -> {
        // Se o statement for mais que uma linha de código, 
        // usar esta nomenclatura
        doSomething() 
    }
// ... 
    else -> {
        println("Outra qualquer")
    }
}
```