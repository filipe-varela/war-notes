---
title: "Null Safety"
date: 2021-12-17T15:35:12Z
---

Um dos maiores problemas que JAVA criou desde da sua criação foi o erro `NullPointerException`, um erro gerado quando se tenta efetuar uma operação sobre uma variável nula - `null`.
Ora, como a variável é nula, não representa nada na memória, então efetuar qualquer operação sobre a mesma seria o mesmo como efetuar uma operação em nada.

```java
// Se se correr este código em JAVA
// 'String nula' irá aparecer na consola
// pois se está a efetuar uma operação
// sob uma variável nula
String stringNula = null;

try {
  stringNula.isEmpty();
} catch (NullPointerExcetion e) {
  System.out.println("String nula");
}
```

Este erro já custou milhões de euros ou dolares à industria, sendo por isso um dos maiores problemas enquanto se lida com JAVA e um dos problemas que a Google quis evitar aquando se desenvolveu o Kotlin.

Em Kotlin, as variáveis são por defeito não nulas, isto é, se se tentar atribuir o valor `null` a uma das variáveis vistas anteriormente, iria-se ter um erro de sintaxe e o programa não iria compilar.
Sendo assim, para se ter variáveis nulas, tem-se que explicitamente indicar no código, usando o ponto de interrogação - `?` - na declaração das variáveis
```kotlin
// Indica que pode ser nulo com “?”
var stringNula : String? = ""
var stringNaoNula : String = ""

// stringNula!!.isEmpty()
stringNula?.isEmpty()
stringNaoNula.isEmpty()
```

Posteriormente, qualquer operação na variável que seja nula tem que ter o sinal `?` para poder executar a operação caso não seja nula - consecutivamente, não executará se for nula.
Caso se queira mesmo que seja executada a função na variável nula no momento em que for executado o comando, pode-se utilizar o `!!`.
Contudo, com este último pode-se estar sujeito ao erro de `NullPointerException`, pois se tentou executar uma operação numa variável nula caso não se tenha cuidado.