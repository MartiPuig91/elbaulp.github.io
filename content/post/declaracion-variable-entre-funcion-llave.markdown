---
layout: post.amp
title: Declaración De Variables Entre El Nombre De La Función Y La Primera Llave en C
modified:
categories:
description: "Declaración De Variables Entre El Nombre De La Función Y La Primera Llave en C"
tags: [pre ansi C stilo, declarar variables antes de funcion C, sintaxis extraña C]
date: 2016-04-06T21:24:34+02:00
modified: 2016-08-09T10:00
main-class: "dev"
color: "#E64A19"
---

> El siguiente artículo es una traducción de una pregunta en **StackOverflow** del usuario <a href="http://stackoverflow.com/users/1612432/algui91" target="_blank" title="algui91 perfil">algui91</a> , que preguntaba <a href="http://stackoverflow.com/questions/13789450/variable-declaration-between-function-name-and-first-curly-brace" target="_blank" title="Variable declaration between function name and first curly brace">_Variable declaration between function name and first curly brace_</a>. La respuesta es del usuario <a href="http://stackoverflow.com/users/270060/omkant" target="_blank" title="Omkant Perfil">omkant</a>.

Hace bastante tiempo me encontré un un código como este:

```c
int main(c,v) char *v; int c;{...}
```

<!--ad-->

Nunca lo había visto, declarar variables entre el nombre de una función y la primera llave, resulta que esta sintaxis corresponde con la definición de funcionas a la vieja usanza de C (pre-ANSI C):

```c
void foo(a,b)
int a;
float b;
{
  // body
}
```

Lo cual es equivalente a escribir lo siguiente:

```c
void foo(int a, float b)
{
// body
}
```

Me resultó curioso, pero no lo uséis :-).

#### Fuente

- Variable declaration between function name and first curly brace \| <a href="http://stackoverflow.com/questions/13789450/variable-declaration-between-function-name-and-first-curly-brace" title="Variable declaration between function name and first curly brace" target="_blank">stackoverlow.com</a>
