---
title: "Kotlin Trivia(l)"
date: 2021-12-17T15:35:03Z
---

Fora das comparações, eis alguns excertos daquilo que se pode escrever em Kotlin:

### Declaração de variáveis
```kotlin
var inteiro : Int = 3
var flutuante : Float = 3.14f
var duplo : Double = 3.14 // este é mais preciso que float
var texto : String = "HackerSchool"
var booleano : Boolean = true
```

#### Constantes
Podem ser declaradas variáveis com o termo `val` variáveis que só pode ser atribuído uma única vez um valor.
Caso haja uma segunda, haverá erro de compilação.
Contudo, variáveis como esta pode ter propriedades alteradas do mesmo modo que fosse um objeto, a partir de um `setter` ou de um `getter`:
```kotlin
val valorConstante = 2

// Vai dar erro
valorConstante = 3
valorConstante = valorConstante + 1

// Não vai dar erro
valorConstante.inc()
```

#### (Alguns) modificadores de visibilidade
Por default, quando declarada uma variável até agora, a mesma seria pública, isto é, poderia ser acedida fora do documento ao qual esta fora declarada.
Por outro lado, é possível declarar variáveis que só podem ser acedidas dentro do mesmo documento, sendo essas `private` ou privadas.

```kotlin
// O `public` pode ser omitido
public var publica : Int = 3 // Default
private var privada : Int = 3
```

#### Inicialização tardia
Por vezes pode ser conveniente declarar um objeto, mesmo antes de se poder inicializá-lo, pois não se sabe que condições este será no futuro.
Para tal, usa-se o comando `lateinit var` para indicar que queremos inicializar mais tarde este objeto ou variável.
Atenção que não é recomendado usar este comando dentro de um método e, ao mesmo tempo, não é possível para tipos primitivos, como inteiros ou flutuantes.
Para estes, é necessário dar um valor por defeito, *default*, para serem declarados e alterados mais tarde (tendo assim de necessitar do parâmetro *var*).
```kotlin
lateinit var txtView : TextView
```

## Listas e Mapas
Tal como em Python, é possível em Kotlin criar listas e mapas (dicionários do Python).
Contudo, Kotlin tem uma particularidade neste departamento em que as mesmas podem ser *mutáveis* ou *imutáveis*.
Isto é, uma lista (mapa) podem ter a propriedade de mudar de tamanho, acrescentar ou remover elementos, se forem mutáveis.
Caso contrário, se não poderem alterar o seu tamanho, então são imutáveis.
Esta nomenclatura ajuda em lidar com melhor armazenamento de memória, pois só se aloca um espaço certo na memória, e com dados guardados em bases de dados ou armazenamento do sistema.
```kotlin
val lMutavel : MutableList<Int> = mutableListOf() 
val lImutavel : List<Int> = listOf()
val mMutavel : MutableMap<String, Int> = mutableMapOf() 
val mImutavel : Map<Int, Int> = mapOf() 
```

### Funções Lambda
Kotlin também pode conter funções lambda - funções anónimas e criadas/declaradas no momento.
A estrutura das mesmas pode ser representada da seguinte maneira:
```kotlin
lMutavel.forEach {
    // Incrementa cada elemento
    it.inc()
}
```
A variável `it` é uma variável gerada automaticamente dentro do `forEach` para representar o elemento em questão da operação - neste caso os inteiros dentro da lista `lMutavel`.