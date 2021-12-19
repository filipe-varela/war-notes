---
title: "Conexão de Backend com Frotend"
date: 2021-12-17T15:35:24Z
---

Para concluir a parte de Backend, a fim de se poder conectar o UI já criado com o Backend da aplicação, deve-se usar o método `findViewById`, que vem já importado, se assim se pode dizer, dentro da atividade:
```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main)

    // Pode-se chamar o método aqui
    val txtView : TextView = findViewById(R.id.txt_menu)
}
```