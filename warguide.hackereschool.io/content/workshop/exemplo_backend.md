---
title: "Exemplo do Backend"
date: 2021-12-17T15:35:30Z
---

Vai-se ao `/src/main/res/` da [estrutura](../estrutura) do projeto e abre-se o `MainActivity.kt`.
Para ajuda, pode-se carregar em `Shift` duas vezes rapidamente para aparecer uma palete de comandos. Daí, pode-se escrever `MainActivity` e deve aparecer o ficheiro que se pretende como um dos sugeridos.

Daí, deve-se ter o seguinte:
```kotlin
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        
    }
}
```

Daqui, tem-se que o código aqui feito é dentro do `onCreate`.

## Declarar os elementos do UI
Para chamar os elementos no UI, tem-se de colocar em primeiro lugar um [ID](../id) no botão.
```xml
<Button
    android:id="@+id/btn_menu"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Click me!"
    android:layout_centerHorizontal="true"
    android:layout_below="@+id/txt_menu"
/>
```

Para depois se poder chamar tanto o texto como o botão do UI no Backend:

```kotlin
val txtView : TextView = findViewById(R.id.txt_menu)
val btnView : Button = findViewById(R.id.btn_menu)
```

> Se aparecer algum erro, põe o cursos perto do mesmo e faz `Alt+Enter`. Deve aparecer algumas sugestões para resolver o mesmo. Em principio, deve ser preciso importar, ou seja, o `import`, mas se não for, fala comigo para poder ver do problema ou tenta resolver procurando na internet.

> `R` é como se fosse uma pasta onde se tem todos os recursos estáticos - que são constantes no decorrer da aplicação -, tais como, `layout`'s, id's ou valores de cores/dimensões/textos. De lá, se quer obter o valor dos id's que se criou previamente

## Alternar o texto
Agora pretende-se alterar o texto `'Hello World!'` por outros dois.
Para tal, vamos usar uma das propriedades do botão e adicionar uma ação quando este é clicado.

Logo depois da sua declaração:
```kotlin
btnView.setOnClickListener {
    txtView.text = "HackerSchool rocks!"
}
```

Agora, se se correr a aplicação, tem-se que o texto muda para `'HackerSchool rocks!'` quando o botão é clicado.

A fim de gerar este efeito de alternar o texto quando se carrega no botão, tem-se que criar uma variável booleana em cima do `onCreate` (podendo ser noutro lugar, mas põe-se antes para conveniência e boa prática):
```kotlin
var mudarTexto = true
```

E mudar a ação do botão para:
```kotlin
btnView.setOnClickListener {
    if (mudarTexto) {
        txtView.text = "HackerSchool rocks!"
        // Negar o valor do mudarTexto para 
        // gerar o efeito de alternação
        mudarTexto = mudarTexto.not()
    } else {
        txtView.text = "You rock!"
        mudarTexto = mudarTexto.not()
    }
}
```

Quando se correr a aplicação agora, tem-se que o texto se vai alternando.

## Exemplo completo
```kotlin
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle

class MainActivity : AppCompatActivity() {
    // Variável para alternar o texto
    var mudarTexto = true

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declarar os objetos na UI
        val txtView : TextView = findViewById(R.id.txt_menu)
        val btnView : Button = findViewById(R.id.btn_menu)

        // Quando carregado, alterar o texto para um novo
        // e negar o valor mudarTexto
        btnView.setOnClickListener {
            if (mudarTexto) {
                txtView.text = "HackerSchool rocks!"
                // Negar o valor do mudarTexto para gerar 
                // o efeito de alternação
                mudarTexto = mudarTexto.not()
            } else {
                txtView.text = "You rock!"
                mudarTexto = mudarTexto.not()
            }
        }
    }
}
```