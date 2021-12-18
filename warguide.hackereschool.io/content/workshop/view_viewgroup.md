---
title: "View e ViewGroup"
date: 2021-12-17T15:31:29Z
---

Exemplos de [*View*](https://developer.android.com/reference/android/view/View):

- *Textview*
```xml
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Hello World!"
    />
```
![TextView](../images/txtview.png)

- *Button*
```xml
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Click me!"
    />
```
![Button](../images/btnview.png)

---

Como os [*ViewGroup*](https://developer.android.com/reference/android/view/ViewGroup)'s são mais fáceis de testar na prática com vários elementos, fica aqui um possível arranjo dos mesmos:

```xml
<!-- ConstraintLayout (abreviado no nome e normalmente default)     -->
<!-- Este layout é usado de uma forma mais visual e ajuda a colocar -->
<!-- constraints ou relações/guias entre elementos e parente        -->
<ConstraintLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    ></ConstraintLayout>

<!-- RelativeLayout                                                 -->
<!-- Este layout serve para posicionar elementos relativos a um     -->
<!-- outro ou com o parente                                         -->
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    ></RelativeLayout>

<!-- LinearLayout                                                   -->
<!-- Este layout organiza os vários elementos internos em colunas,  -->
<!-- com orientation colocada para horizontal, ou em linhas, com a  -->
<!-- orientation colocada para vertical                             -->
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    ></LinearLayout>

<!-- GridLayout -->
<!-- Como o nome indica, este ViewGroup posiciona os seus elementos -->
<!-- sob uma grelha, onde rowCount e columnCount têm que ser forne- -->
<!-- cidos para poder funcionar                                     -->
<GridLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:rowCount="4"
    android:columnCount="2"
    ></GridLayout>
```