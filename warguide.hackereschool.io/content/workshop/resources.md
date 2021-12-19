---
title: "Resources"
date: 2021-12-17T15:36:01Z
---

Dentro da aplicação pode haver [elementos](https://developer.android.com/guide/topics/resources/providing-resources) que sejam constantes durante a sua utilização, tanto para dimensões, esquemas ou até textos que podem ser usados para serem internacionalizados posteriormente.
Para isto, o Android permite armazenamento de *Resources* dentro do mesmo, localizando-se como a superpasta dos layouts, `res`.

![Resources Exemplo](../images/resources_exemplo.png)

Aqui só se encontram ficheiros de formato `.xml`, visto na secção de [frotend](../xml), mas com uma particularidade:

```xml
<resources>
    <tipo name="nome_do_recurso">valor</tipo>
</resources>
```

### res/value/strings
Aqui se pode colocar os textos estáticos da aplicação, onde até se mais tarde se podem internacionalizar a partir deste ficheiro.
```xml
<resources>
    <string name="app_name">Titulo da App</string>
</resources>
```

E podem ser usados nas propriedades de `text` das tags no layout, como por exemplo

```xml
<TextView
    android:id="@+id/txt_view"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="@string/app_name"
    android:layout_centerInParent="true"
    />
```

> Recomendado usar este formato/procedimento aquando se tem texto no layout que não altere enquanto o utilizador mexe na aplicação

### res/value/colors
Este formato pode se aplicado para o `res/values/colors`, sendo que o que altera é o valor inserido e o tipo de *resource* que se esteja a lidar:

```xml
<resources>
    <color name="purple_200">#FFBB86FC</color>
    <color name="purple_500">#FF6200EE</color>
    <color name="purple_700">#FF3700B3</color>
    <color name="teal_200">#FF03DAC5</color>
    <color name="teal_700">#FF018786</color>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
</resources>
```

A sua aplicação pode ser aplicada em vários locais ao longo da UI ou até como recurso no background.
Um dos exemplos no UI pode ser o seguinte acréscimo de `background` no `TextView` anterior:

```xml
<TextView
    android:id="@+id/txt_view"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="@string/app_name"
    android:layout_centerInParent="true"
    android:background="@color/teal_200"
    />
```



### res/value/dimen
Este ficheiro em principio não existe na criação do projeto, mas é essencial para manter a concordância entre tamanhos e espaçamentos do UI, tal como haver concordância das cores ou texto.
A sua formatação é a seguinte:
```xml
<resources>
    <dimen name="textFont">12sp</dimen>
</resources>
```

Sendo posteriormente aplicado da mesma maneira que nos outros tópicos, sendo neste caso usado como `textSize` no `TextView`:
```xml
<TextView
    android:id="@+id/txt_view"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="@string/app_name"
    android:layout_centerInParent="true"
    android:background="@color/teal_200"
    android:textSize="@dimen/textFont"
    />
```

#### Unidades
Ainda neste tópico é importante ter noção nas [dimensões](https://developer.android.com/guide/topics/resources/more-resources#Dimension) que se use, sendo neste caso importante notar que:

> **dp:** Uma unidade usada para definir o espaçamento ou tamanho entre elementos no ecrã independentemente da densidade de pixeis que se tenha. 

> **sp:** Uma unidade usada para definir a fonte do texto, sendo que é de certo modo semelhante ao `dp`, mas adapta-se ao tamanho de fonte do dispositivo

É importante saber que unidade usar para cada caso e evitar maus usos.

## Uso no backend
Para se poder usar os resources no backend é através da variável `resources` que normalmente vem com a atividade, ou seja, pode-se fazer:

```kotlin
var nomeApp = resources.getString(R.string.app_name)
```

Sendo que é possível obter outros valores estáticos de recursos a partir desta variável.
Para o caso de, ao longo do desenvolvimento, não se conseguir aceder à variável resources, deve-se usar o `context` atual do código - ver mais informação [aqui](https://developer.android.com/reference/kotlin/android/content/res/Resources).