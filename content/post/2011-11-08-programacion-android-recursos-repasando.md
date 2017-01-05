---
categories:
- android
- opensource
color: '#689F38'
date: 2011-11-08T00:00:00Z
main-class: android
modified: 2016-09-29T20:36
tags:
- curso android pdf
title: 'Programación Android: Recursos - Repasando la estructura del directorio de
  recursos'
url: /programacion-android-recursos-repasando/
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
