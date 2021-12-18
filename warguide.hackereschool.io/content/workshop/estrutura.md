---
title: "Estrutura do Android Studio"
date: 2021-12-17T15:30:53Z
---

Para se poder mexer no programa e desenvolver assim a aplicação, tem-se de criar um novo projeto em `File -> New -> New project` e escolher `Empty Activity`.


![New Project](../images/new_project.png)

Depois é preciso escolher um nome para o projeto, isso será arbitrário, escolher a linguagem Kotlin e `Minimum SDK` para 27, mas poderá ser um nível inferior se for necessário (mas ter atenção na escolha!).
Para este workshop, o nível de API 27 será mais que suficiente.

## Estrutura do projeto internamente
O projeto é estruturado da seguinte maneira:

![Estrutura do projeto](../images/estrutura.png)

Onde:
- Os ficheiros de backend se encontram em `MyApp/app/src/main/java/`
- Os ficheiros de frotend se encontram em `MyApp/app/src/main/res/`
- Os ficheiros usados para *build* da aplicação são os ficheiros com terminação de `*.gradle`, onde iremos utilizar para implementar componentes externos ao Android Studio.