---
title: "SharedPreferences"
date: 2021-12-17T15:35:55Z
---

> **SharedPreferences:** Interface for accessing and modifying preference data returned by Context.getSharedPreferences(String, int). (…) Modifications to the preferences must go through an Editor object to ensure the preference values remain in a consistent state and control when they are committed to storage.

As `SharedPreferences` servem para guardar e restaurar valores dentro do armazenamento alocado para a aplicação, sendo esses valores os primitivos discutidos na [trivia de Kotlin](../kotlin_trivia).

Para se poder usar, tem-se que inicializar uma variável que represente um dos blocos de dados que poderemos usar.
Criando um caso não exista, no processo, e caracterizado por uma String única do próprio, por isso, tem de ser constante e deveria ser diferente ao mostrado:

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main)
    // Criar o sharedpreferences, pode ser necessário importar o Context
    val sharedPrefs = getSharedPreferences("CONSTANT_KEY", Context.MODE_PRIVATE)
}
```

Sendo que poderemos obter os dados deste bloco a partir do método `.get`:

```kotlin
var textoGuardado = sharedPrefs.getString("chave", "default")
```

Sendo que precisa de uma chave única, específica e constante para o dado que se esteja a restaurar e de um valor defeito ou *default* caso não exista previamente.

### Editar
Para editar os valores, é preciso chamar o editor e posteriormente dar apply do valor.

```kotlin
val editor = sharedPrefs.edit()
editor.putString("chave", "outro valor")
editor.apply()
```

Neste caso se chama o editor para alterar qualquer que seja o valor que estivesse alocado para a chave `"chave"` por `"outro valor"`.
O `apply` indica ao programa para salvar as alterações o mais cedo possível, a fim de evitar qualquer problema na sincronização com outros processos que estejam a correr no background.

### Exemplo
Neste exemplo, tem-se que ao carregar num botão, o texto é alterado e ao mesmo tempo guardado com um valor incrementado. 
Ao mesmo tempo, quando se inicia a atividade, o texto é restaurado da sessão anterior:

```kotlin
// Chaves para serem usadas no SharedPreferences
val chaveShared = "CONSTANT_KEY"
val chaveInteiro = "inteiro"
val chaveTexto = "texto"

override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main)

    // Iniciar sharedprefs
    val sharedPrefs = getSharedPreferences(
        chaveShared, 
        Context.MODE_PRIVATE
    )

    // Iniciar a view, restaurando a sessão anterior
    val txtView : TextView = findViewById(R.id.txt_view)
    txtView.text = sharedPrefs.getString(chaveTexto, "Carregado 0 vezes")
    val btnView : Button = findViewById(R.id.btn_view)

    // Quando se carrega no botão, é incrementado o valor guardado,
    // mostrado no txtView e guardado no sharedPrefs
    btnView.setOnClickListener {
        var inteiro = sharedPrefs.getInt(chaveInteiro, 0)

        inteiro += 1

        txtView.text = "Carregado $inteiro vezes"

        val editor = sharedPrefs.edit()
        editor.putString(chaveTexto, txtView.text.toString())
        editor.putInt(chaveInteiro, inteiro)
        editor.apply()
    }
}
```