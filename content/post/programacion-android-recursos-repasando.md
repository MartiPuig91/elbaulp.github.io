---
title: 'Programación Android: Recursos - Repasando la estructura del directorio de recursos'
modified: 2016-09-29T20:36
layout: post.amp
permalink: /programacion-android-recursos-repasando/
categories:
  - android
  - opensource
tags:
  - curso android pdf
mainclass: "android"
color: "#689F38"
---
En resumen, en el siguiente listado muestra la estructura global del directorio de recursos:

```bash
/res/values/string.xml
                /colors.xml
                /dimens.xml
                /attrs.xml
                /styles.xml
     /drawable/*.png
              /*.jpg
              /*.gif
              /*.9.png
     /anim/*.xml
     /layout/*.xml
     /raw/*.*
     /xml/*.xml
/assets/*.*/*.*
```

> Debido a que no se encuentra bajo el directorio <i>/res</i>, solo el directorio<i> /assets</i> puede contener una lista arbitrária de directorios. Cualquier otro directorio solo puede contener ficheros en ese nivel, y no mas subdirectorios

## Siguiente Tema: [Programación Android: Recursos - Recursos y cambios de configuración][1]

 [1]: https://elbauldelprogramador.com/programacion-android-recursos-recursos/
