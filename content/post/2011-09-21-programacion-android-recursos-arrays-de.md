---
categories:
- android
- opensource
color: '#689F38'
date: 2011-09-21T00:00:00Z
main-class: android
modified: 2016-08-09T09:50
redirect_from: /opensource/programacion-android-recursos-arrays-de/
tags:
- curso android pdf
title: 'Programación Android: Recursos - Arrays de strings'
url: /programacion-android-recursos-arrays-de/
---

Se pueden definir arrays de strings como recursos en cualquier archivo bajo el subdirectorio ./res/values. Para definirlos, usaremos un nodo XML llamado *string-array*. Este nodo es un hijo de *resources*, al igual que el nodo *string*. A continuación, vamos a ver como crear un array de strings:

<!--ad-->

```xml
<resources>
    <string>
        <item>uno</item>
        <item>dos</item>
        <item>tres</item>
    </string>
</resources>
```

Una vez definido el recurso, podemos usarlo en el código Java de la siguiente manera:

```java
//Accedemos al objeto 'Recursos' desde la Activity
Resources res = nombre-de-la-actividad.getResources();
String strings[] = res.getStringArray(R.array.test_array);

//Mostramos el array
for (String s: strings)
   Log.d("ejemplo", s);
```

#### Siguiente Tema: [Programación Android: Recursos - Plurales][1] 

 [1]: https://elbauldelprogramador.com/programacion-android-recursos-plurales/
