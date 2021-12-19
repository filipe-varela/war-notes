---
title: "Box Model"
date: 2021-12-17T15:36:08Z
---

Quando se dimensiona *layout*'s, tem-se que ter noção do [Box Model](https://en.wikipedia.org/wiki/CSS_box_model), um conceito proveniente de CSS e tem como objetivo ter zonas dum objeto que podem mudar de grossura, fazendo caixas com os limites grossos ou finos, juntos ou afastados do conteúdo ou fazer com que um objeto esteja próximo ou afastado de um outro objeto.

![Box_Model](../images/box_model.png)

> **Content:** Onde estará o conteúdo do objeto, podendo ser uma imagem ou texto

> **Padding:** Espaçamento entre o conteúdo e a fronteira

> **Border:** A espessura da fronteira ou do limite à volta do conteúdo

> **Margin:** Espaçamento entre a fronteira de outros elementos do UI. Este pode "colidir" com outras margens, proporcionando um afastamento ainda maior entre elementos

Um exemplo pode ser o de afastar o botão do texto no [exemplo](../exemplo_frotend) prático do frotend feito anteriormente:

```xml
<TextView
    android:id="@+id/txt_view"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="@string/app_name"
    android:layout_centerInParent="true"
    android:layout_marginBottom="12dp"
    />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Click me!"
    android:layout_centerHorizontal="true"
    android:layout_below="@id/txt_view"
    />
```