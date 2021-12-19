---
title: "Exemplo do Frotend"
date: 2021-12-17T15:32:02Z
---

O exemplo começa em alterar o ficheiro `activity_main.xml` em `/src/main/res/layout` e poderá ser provavelmente um dos separadores dentro do Android Studio já aberto.
Tem-se como objetivo para este exemplo ter um botão que altere o texto de forma alternada.

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    >
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        />
    </androidx.constraintlayout.widget.ConstraintLayout>
```

O primeiro paço aqui seria adaptar o `ConstraintLayout` para um *layout* que nos permita posicionar melhor os elementos com poucas linhas de código.
Para tal, iremos utilizar o `RelativeLayout`, adaptando posteriormente o `TextView` para manter o mesmo aspeto anterior a esta alteração (que foi trocar o nome do ViewGroup e retirar as linhas que continham o package da `app`):

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        android:layout_centerInParent="true"
        />
</RelativeLayout>
```
![Exemplo 1](../images/exemplo_frotend_1.png)

Um aspeto interessante é de que as propriedades usadas são diretas na interpretação, sendo que a linha adicionada no texto ser `layout_centerInParent` indica que o elemento vai ser centrado no centro do elemento parente.

> Define-se como elemento parente ou *parent* o elemento que está um nível acima na hierarquia. Por vezes, pode-se ter como o parente o ecrã do telemóvel se o *ViewGroup* for o elemento mais exterior que consigamos alterar

Por fim, pretende-se adicionar um botão, bastando adicionar as respetivas linhas já vistas anteriormente no ficheiro:

```xml
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Click me!"
    />
```

Contudo, este aparecerá no canto superior esquerdo do ecrã.
este é a posição *default* do android aquando não estiver definida um posicionamento para o mesmo.
Para evitar isto, vamos utilizar o conceito de ID já falado e utilizar uma das propriedades provenientes do `RelativeLayout`, `android:layout_below="id`: Coloca o *View* em questão debaixo de outro a partir do ID deste último - [doc](https://developer.android.com/reference/android/widget/RelativeLayout.LayoutParams#attr_android:layout_below).
Neste caso, iremos colocar esta linha no botão e necessitar de referenciar o texto que está centrado no ecrã:

```xml
<!-- Relative Layout -->

<TextView
    android:id="@+id/txt_menu"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Hello World!"
    android:layout_centerInParent="true"
    />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Click me!"
    android:layout_centerHorizontal="true"
    android:layout_below="@+id/txt_menu"
/>

<!-- Relative Layout -->
```
![Exemplo 2](../images/exemplo_frotend_2.png)

Sendo que se acrescentou a linha `layout_centerHorizontal` para o botão ficasse centrado horizontalmente com o seu parente.

Está-se por concluído, por enquanto o frotend desta secção.

## Exemplo completo
```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/txt_menu"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        android:layout_centerInParent="true"
        />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Click me!"
        android:layout_centerHorizontal="true"
        android:layout_below="@+id/txt_menu"
        />
        
</RelativeLayout>
```