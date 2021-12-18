---
title: "XML"
date: 2021-12-17T15:31:18Z
---

A linguagem de frotend usada pelo Android Studio é denominada como *Extensible Markup Language* ou *XML*!
Esta linguagem é bastante semelhante a uma junção de HTML com CSS, de certa maneira, onde se tem o conceito de tag's, hierarquia e propriedades.
Para além disso, esta linguagem pode ser usada para armazenar informação, montar esquemas ou *layouts* e muito mais!

## Formato
Em termos de formato dentro do Android Studio e em termos de *layout*, um elemento simples é representado da seguinte maneira:

```xml
<tag
    package:propriedade="valor"
    ...
/>
```

A fim de facilitar a conexão entre nomenclatura do XML e de Android Studio, elementos com esta estrutura são denominados, no *layout* mais uma vez, como *View*.
Por outro lado, se se quiser ter uma hierarquia no ficheiro de XML, tem-se o seguinte:

```xml
<grouptag
    package:propriedade=“valor“
    ...>
    <tag
        package:propriedade=“valor“
    />
    <tag .../>
</grouptag>
```

Denominando o elemento `grouptag` neste caso como `ViewGroup`.


## Packages
A fim de apresentar mais o conceito que dedicar tempo à sua explicação, quando se quis dizer `propriedade` dentro de cada `tag` e `grouptag`, estava-se a referir aos seguintes módulos que devem estar garantidamente dentro do ficheiro XML caso uma das suas propriedades seja usada:

```xml
<!- Package Android: exemplo -->
<grouptag 
    xmlns:android="http://schemas.android.com/apk/res/android"
    >
    <tag android:layout_width="math_parent" />
</grouptag>

<!- Package App: exemplo -->
<grouptag 
    xmlns:app="http://schemas.android.com/apk/res-auto"
    >
    <tag app:layout_constraintBottom_toBottomOf="parent" />
</grouptag>
```

Sendo o que muda em ambos casos é o que se esteja a importar, com `xmlns:package="url"`, e o respetivo nome do package.