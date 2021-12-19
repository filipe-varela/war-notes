---
title: "Utils"
date: 2021-12-17T15:36:12Z
---

Por vezes é útil criar um ficheiro com ferramentas usadas ao longo do projeto e/ou que não tenha relacionamento com as outras funcionalidades que se esteja a desenvolver.
Para tal, é útil utilizar o ficheiro `Utils.kt`, que se gera e normalmente fica ou numa pasta própria ou na pasta global e pode ter como exemplo o seguinte:

```kotlin
class Utils {
    companion object {
        /**
        * As variáveis daqui podem ser chamadas
        * onde quiserem, usando apenas o comando
        * Utils.<nome da variavel>.
        *
        * Isto funciona com métodos mesmo assim,
        * do mesmo modo que as variáveis:
        * Utils.<nome do método>()
        */
        val a = 1
        fun soma(val1:Int, val2:Int) : Int {
            return val1 + val2
        }    
    }
}
```

Este ficheiro usa o conceito de `companion object`, parecido a `static` em JAVA e o que permite este modificador é aquilo que se encontra comentado no bloco de código anterior.
Desta maneira, não é preciso criar uma instância de `Utils` nem é preciso estar a reescrever o mesmo código várias vezes.
Não confundir com o [Resources](../resources), sendo que estes, apesar de serem estáticos, devem ser usados para chaves de [shared preferences](../sharedprefs) ou para organizar o layout, entre outras funcionalidades.